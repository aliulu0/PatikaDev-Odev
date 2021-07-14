# PatikaDev-SQL
<a href='#Ödev 1'>Ödev - 1</a><br>
<a href='#Ödev 2'>Ödev - 2</a><br>
<a href='#Ödev 3'>Ödev - 3</a><br>
<a href='#Ödev 4'>Ödev - 4</a><br>
<a href='#Ödev 5'>Ödev - 5</a><br>
<a href='#Ödev 6'>Ödev - 6</a><br>
<a href='#Ödev 7'>Ödev - 7</a><br>
<a href='#Ödev 8'>Ödev - 8</a><br>
<a href='#Ödev 9'>Ödev - 9</a><br>
<a href='#Ödev 10'>Ödev - 10</a><br>
<a href='#Ödev 11'>Ödev - 11</a><br>
<a href='#Ödev 12'>Ödev - 12</a><br>

## <p id = 'Ödev 1' > Ödev - 1 </p> 
#### 1) film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film; 
~~~
#### 2) film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız. 
~~~sql
SELECT * FROM film WHERE length > 60 AND length < 75;
~~~
#### 3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız. 
~~~sql
SELECT * FROM film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99; 
~~~
#### 4) customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir? 
~~~sql
SELECT * FROM customer WHERE first_name = 'Mary'; 
Cevap: "Smith" 
~~~
#### 5) film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız. 
~~~sql
SELECT * FROM film WHERE NOT length > 50 AND NOT (rental_rate =2.99 OR rental_rate = 4.99); 
~~~

## <p id = 'Ödev 2' > Ödev - 2 </p>
#### 1) film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99; 
~~~
#### 2) actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name,last_name FROM actor WHERE first_name IN('Penelope','Nick','Ed'); 
~~~
#### 3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. (IN operatörünü kullanınız.)
~~~sql
SELECT * FROM film WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
~~~

## <p id = 'Ödev 3' > Ödev - 3 </p> 
#### 1) country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT * FROM country WHERE country LIKE 'A%a';
~~~
#### 2) country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM Country WHERE LENGTH(country) > 6 AND country LIKE '%n';
~~~
#### 3) film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
~~~sql
SELECT title FROM film WHERE title ILIKE '%t%t%t%t%';
~~~
#### 4) film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız. 
~~~sql
SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
~~~

## <p id = 'Ödev 4' > Ödev - 4 </p>
#### 1) film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~
#### 2) film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film;
~~~
#### 3) film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT(*) FROM film WHERE title LIKE 'T%' AND rating = 'G';
~~~
#### 4) country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT(*) FROM country WHERE LENGTH(country) = 5 ;
~~~
#### 5) city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT(*) FROM city WHERE city ILIKE  '%r';
~~~
## <p id = 'Ödev 5' > Ödev - 5 </p>
#### 1) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT title FROM film WHERE title LIKE '%n' ORDER BY LENGTH(title) DESC LIMIT 5;
~~~
#### 2) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT title FROM film WHERE title LIKE '%n' ORDER BY LENGTH(title) DESC OFFSET 5 LIMIT 5;
~~~
#### 3) customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;
~~~

## <p id = 'Ödev 6' > Ödev - 6 </p> 
#### 1) film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT ROUND(AVG(rental_rate),2) FROM film; 
~~~
#### 2) film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(*) FROM film WHERE title LIKE 'C%';
~~~
#### 3) film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX(length) FROM film WHERE rental_rate = 0.99;
~~~
#### 4) film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT( DISTINCT replacement_cost ) FROM film WHERE length > 150;
~~~

## <p id = 'Ödev 7' > Ödev - 7 </p> 
#### 1) film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating FROM film GROUP BY rating; 
~~~
#### 2) film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;
~~~
#### 3) customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
~~~sql
SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;
~~~
#### 4) city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;
~~~

## <p id = 'Ödev 8' > Ödev - 8 </p> 
#### 1) test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql
CREATE TABLE employee 
(id SERIAL PRIMARY KEY, 
name VARCHAR(50), 
email VARCHAR(100)
birtday DATE
); 
~~~
#### 2) Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~sql
insert into author (name, email, birtday) values ('Adrien Liepina', 'aliepina0@admin.ch', null);
insert into author (name, email, birtday) values ('Maisie Bonar', 'mbonar1@lycos.com', '1944-01-28');
insert into author (name, email, birtday) values ('Alethea Haddleston', 'ahaddleston2@angelfire.com', null);
insert into author (name, email, birtday) values ('Normie Leonard', 'nleonard3@lulu.com', '1988-11-17');
insert into author (name, email, birtday) values ('Sherman Rickman', 'srickman4@oaic.gov.au', '1977-08-30');
insert into author (name, email, birtday) values ('Kin Okell', 'kokell5@mediafire.com', '1978-08-07');
insert into author (name, email, birtday) values ('Jody Lofty', 'jlofty6@upenn.edu', '1978-06-26');
insert into author (name, email, birtday) values ('June Durkin', 'jdurkin7@hhs.gov', null);
insert into author (name, email, birtday) values ('Dorelia Pleuman', 'dpleuman8@ucoz.ru', '1922-02-04');
insert into author (name, email, birtday) values ('Brendin Deeley', 'bdeeley9@hc360.com', '1978-10-08');
insert into author (name, email, birtday) values ('Dona Birdall', 'dbirdalla@wunderground.com', '1925-03-07');
insert into author (name, email, birtday) values ('Savina Baddam', 'sbaddamb@ezinearticles.com', null);
insert into author (name, email, birtday) values ('Jackelyn McCarly', 'jmccarlyc@pen.io', '1992-10-12');
insert into author (name, email, birtday) values ('Brooks Casarino', null, '1952-11-14');
insert into author (name, email, birtday) values ('Danica Dodds', 'ddoddse@domainmarket.com', '1912-03-22');
insert into author (name, email, birtday) values ('Nanon Lean', 'nleanf@soundcloud.com', '1924-02-23');
insert into author (name, email, birtday) values ('Melonie Riddell', 'mriddellg@globo.com', '1975-12-11');
insert into author (name, email, birtday) values ('Nicoline Copin', 'ncopinh@ocn.ne.jp', '1948-10-18');
insert into author (name, email, birtday) values ('Dana Purton', 'dpurtoni@photobucket.com', '1925-04-25');
insert into author (name, email, birtday) values ('Kayle Grinov', 'kgrinovj@tinyurl.com', '1901-05-01');
insert into author (name, email, birtday) values ('Lisabeth Gristwood', 'lgristwoodk@dot.gov', '1987-09-26');
insert into author (name, email, birtday) values ('Vida Truscott', 'vtruscottl@spotify.com', '1932-07-10');
insert into author (name, email, birtday) values ('Wilma Kleinzweig', 'wkleinzweigm@nps.gov', '1928-01-30');
insert into author (name, email, birtday) values ('Reidar Domesday', 'rdomesdayn@wikia.com', '1919-06-16');
insert into author (name, email, birtday) values ('Elayne Pleven', 'epleveno@google.it', '1948-09-22');
insert into author (name, email, birtday) values ('Clementina Gorling', 'cgorlingp@sciencedirect.com', '1992-04-02');
insert into author (name, email, birtday) values ('Izaak Furst', 'ifurstq@illinois.edu', '1969-11-09');
insert into author (name, email, birtday) values ('Norrie Hathaway', 'nhathawayr@phpbb.com', '1970-03-11');
insert into author (name, email, birtday) values ('Birdie Georgi', 'bgeorgis@themeforest.net', null);
insert into author (name, email, birtday) values ('Lyndell Handrahan', 'lhandrahant@fema.gov', null);
insert into author (name, email, birtday) values ('Harley McDermid', 'hmcdermidu@ucoz.com', '1977-09-03');
insert into author (name, email, birtday) values ('Bryn Sperry', 'bsperryv@clickbank.net', '1956-07-26');
insert into author (name, email, birtday) values ('Celestine Kolushev', 'ckolushevw@statcounter.com', '1970-11-08');
insert into author (name, email, birtday) values ('Viva Morillas', null, '1907-07-28');
insert into author (name, email, birtday) values ('Ruprecht Malser', 'rmalsery@1und1.de', '1965-07-09');
insert into author (name, email, birtday) values ('Cori Redborn', 'credbornz@netscape.com', '1945-10-29');
insert into author (name, email, birtday) values ('Evered Loreit', 'eloreit10@gnu.org', '1920-06-24');
insert into author (name, email, birtday) values ('Roma Pellamont', 'rpellamont11@jimdo.com', '1945-10-03');
insert into author (name, email, birtday) values ('Jordanna Dall', 'jdall12@wikispaces.com', '1978-02-23');
insert into author (name, email, birtday) values ('Carling Meekins', 'cmeekins13@tripadvisor.com', null);
insert into author (name, email, birtday) values ('Dorice Kibbye', 'dkibbye14@biblegateway.com', '1950-09-02');
insert into author (name, email, birtday) values ('Carey Feldhammer', 'cfeldhammer15@dell.com', '1984-05-15');
insert into author (name, email, birtday) values ('Alikee Eagar', 'aeagar16@infoseek.co.jp', '1927-07-20');
insert into author (name, email, birtday) values ('Lothaire Eveleigh', 'leveleigh17@cargocollective.com', '1974-04-21');
insert into author (name, email, birtday) values ('Chrisse Bernette', 'cbernette18@deviantart.com', null);
insert into author (name, email, birtday) values ('Dario Sedgwick', null, '1951-11-08');
insert into author (name, email, birtday) values ('Jaine Caras', 'jcaras1a@chron.com', null);
insert into author (name, email, birtday) values ('Franky Jacobovitz', 'fjacobovitz1b@china.com.cn', '1957-08-26');
insert into author (name, email, birtday) values ('Dal Sidery', 'dsidery1c@comsenz.com', '1907-01-18');
insert into author (name, email, birtday) values ('Caterina Fideler', 'cfideler1d@over-blog.com', '1954-08-24');
~~~
#### 3) Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~sql
UPDATE employee SET name = 'David Beckham' WHERE id = 7;
UPDATE employee SET email = 'david@beckham.com' WHERE name = 'David Beckham';
UPDATE employee SET birtday = '1975-05-02' WHERE id = 7;
UPDATE employee SET name = 'Tom Hardy' WHERE name LIKE 'J%';
UPDATE employee SET email = 'whats@up.com' WHERE id = 15;
~~~
#### 4) Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~sql
DELETE FROM employee WHERE id = 7;
DELETE FROM employee WHERE name = 'Lothaire Eveleigh';
DELETE FROM employee WHERE id > 25;
DELETE FROM employee WHERE email = 'dsidery1c@comsenz.com';
DELETE FROM employee WHERE birtday = '1970-03-11';
~~~

## <p id = 'Ödev 9' > Ödev - 9 </p> 
#### 1) city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT city, country FROM city INNER JOIN country ON country.country_id = city.country_id; 
~~~
#### 2) customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT payment_id,first_name,last_name FROM payment INNER JOIN customer ON customer.customer_id = payment.customer_id;
~~~
#### 3) customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT rental_id,first_name,last_name FROM rental INNER JOIN customer ON customer.customer_id = rental.customer_id;
~~~

## <p id = 'Ödev 10' > Ödev - 10 </p> 
#### 1) city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~sql
SELECT city,country FROM country LEFT JOIN city ON city.country_id = country.country_id; 
~~~
#### 2) customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
~~~sql
SELECT payment_id,first_name,last_name FROM customer RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
~~~
#### 3) customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
~~~sql
SELECT rental_id,first_name,last_name FROM customer FULL JOIN rental ON customer.customer_id = rental.customer_id;
~~~
## <p id = 'Ödev 11' > Ödev - 11 </p> 
#### 1) actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
UNION
(
SELECT first_name FROM customer
ORDER BY first_name
); 
~~~
#### 2) actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
INTERSECT
(
SELECT first_name FROM customer
ORDER BY first_name
);
~~~
#### 3) actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
EXCEPT
(
SELECT first_name FROM customer
ORDER BY first_name
);
~~~
#### 4) İlk 3 sorguyu tekrar eden veriler için de yapalım.
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
UNION ALL
(
SELECT first_name FROM customer
ORDER BY first_name
);
~~~
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
INTERSECT ALL
(
SELECT first_name FROM customer
ORDER BY first_name
);
~~~
~~~sql
(
SELECT first_name FROM actor
ORDER BY first_name
)
EXCEPT ALL
(
SELECT first_name FROM customer
ORDER BY first_name
);
~~~

## <p id = 'Ödev 12' > Ödev - 12 </p> 
#### 1) film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
~~~sql
SELECT COUNT(length) FROM film
WHERE length >
(
SELECT AVG(length) FROM film
);
~~~
#### 2) film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
~~~sql
SELECT COUNT(*) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
~~~
#### 3) film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
~~~sql
SELECT * FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film); 
~~~
#### 4) payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız. 
~~~sql
SELECT payment.customer_id,customer.first_name,customer.last_name, SUM(amount) FROM payment
JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id,customer.first_name,customer.last_name
ORDER BY SUM(amount) DESC;
~~~
