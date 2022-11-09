# H3



## x) Lue/katso/kuuntele ja tiivistä

#### [OWASP TOP 10](https://terokarvinen.com/2022/tunkeutumistestaus-ict4tn027-3010-syksylla-2022/owasp-top-10-2017.pdf)



#### [Percival & Samancioglu 2020: The Complete Ethical Hacking Course videot](https://learning.oreilly.com/videos/the-complete-ethical/9781839210495/9781839210495-video21_1/)


## y) Cross site story



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




## c) Execute! 



## d) Webgoat

#### A1 Injection


#### A2 Broken authentication


![image](https://user-images.githubusercontent.com/93308960/200806221-86af7948-cab6-4edc-8dc5-a78352c4c562.png)


![image](https://user-images.githubusercontent.com/93308960/200806781-10bbd94f-c61f-4d5e-b7cf-94a765f0cc82.png)


![image](https://user-images.githubusercontent.com/93308960/200807254-c1920ff7-48d7-40a2-9bec-83714f5d7a72.png)


![image](https://user-images.githubusercontent.com/93308960/200808155-ce83a53c-8acd-4b01-ac3f-01077e491b3d.png)




![image](https://user-images.githubusercontent.com/93308960/200807383-36a30de8-8823-4805-94b7-f72a72d7e7a0.png)


#### A3 Sensitive data exposure


![image](https://user-images.githubusercontent.com/93308960/200793457-f6febc9e-c132-405d-92f1-e8c1fd33fad9.png)


#### A7 Cross Site Scripting (XSS)

![image](https://user-images.githubusercontent.com/93308960/200810596-1ea06f65-68d4-4293-885f-8c83208a6590.png)

Testeistä oli jäänyt ; merkki jonka takia sivusto ei hyväksynyt sitä aikaisemmin

![image](https://user-images.githubusercontent.com/93308960/200814134-f2a9b8da-dd91-4367-8196-6e861c4acfb0.png)


![image](https://user-images.githubusercontent.com/93308960/200814191-305807f6-651a-46e5-86a2-89c9925563ff.png)

![image](https://user-images.githubusercontent.com/93308960/200814228-b05769eb-2973-4689-abd2-e1fa41acda3a.png)


#### A8:2013 Request Forgeries

![image](https://user-images.githubusercontent.com/93308960/200825878-e1f70fd3-31d7-4af8-b026-a7eceea1915e.png)


![image](https://user-images.githubusercontent.com/93308960/200825740-2b32d85a-65af-4b52-a594-f2e0f6e51d9f.png)


![image](https://user-images.githubusercontent.com/93308960/200825794-f6aee168-d284-4b57-ac11-5c0f49ea91e2.png)




![image](https://user-images.githubusercontent.com/93308960/200832087-8c5098af-19fa-4605-bc2c-91fc2ce3e427.png)


![image](https://user-images.githubusercontent.com/93308960/200832658-a8bfe0c8-a88e-4fa5-b035-79d372af1b3e.png)


![image](https://user-images.githubusercontent.com/93308960/200835070-fd2a2b4f-8dad-4600-8613-c4dfa934ab20.png)

![image](https://user-images.githubusercontent.com/93308960/200835797-5dd8ae4d-9335-47b6-86dc-bed81cfb1e6d.png)


![image](https://user-images.githubusercontent.com/93308960/200836243-9e5bf5da-bf04-4195-a1be-b421d7d82c59.png)

![image](https://user-images.githubusercontent.com/93308960/200836024-d7d95333-c5b7-4f8e-ab20-a6ebed30e02f.png)
