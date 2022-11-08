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

2) Piti saada maitten nimet esille joiden väkiluku on vähintään 200 miljoonaa. Nimi saatiin esille 

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


4) Piti saad



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


#### A3 Sensitive data exposure



#### A7 Cross Site Scripting (XSS)



#### A8:2013 Request Forgeries

