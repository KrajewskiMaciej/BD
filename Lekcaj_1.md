# Zadanie 1.
1.
   ``` MySQL
   CREATE TABLE postacie(id INTEGER PRIMARY KEY NOT NULL AUTO_INCREMENT,nazwa VARCHAR(40),rodzaj ENUM('wiking','ptak','kobieta'),data_ur DATE,wiek INTEGER UNSIGNED);
   ```
2. INSERT INTO postacie VALUES ('1', 'Bjorn', 'wiking', '1995.02.12', '27');
   INSERT INTO postacie VALUES ('2', 'Drozd', 'ptak', '2019.07.23', '3');
   INSERT INTO postacie VALUES ('3', 'Tesciowa', 'kobieta', '1952.05.27', '70');
3. UPDATE postacie SET data_ur='1934.05.27', wiek='88' WHERE nazwa='Tesciowa';

Zadanie 2.
1. CREATE TABLE walizka(id_walizki INTEGER NOT NULL AUTO_INCREMENT UNIQUE,pojemnosc INT(10) UNSIGNED,kolor ENUM('rozowy','czerwony','teczowy','zolty'),id_wlasciciela INT);
    ALTER TABLE walizka ADD FOREIGN KEY (id_wlasciciela) REFERENCES postacie(id);
2. ALTER TABLE walizka ALTER COLUMN kolor SET DEFAULT 'rozowy';
3. INSERT INTO walizka VALUES ( 1, '20', 'rozowy', '1');
   INSERT INTO walizka VALUES ( 2, '20', 'zolty', '3');

Zadanie 3.
1. CREATE TABLE izba(adres_budynku VARCHAR(40) PRIMARY KEY, nazwa_izby VARCHAR(35), metraz INT UNSIGNED, wlascicel INT);
   ALTER TABLE izba ADD CONSTRAINT id PRIMARY KEY(adres_budynku, nazwa_izby);
   ALTER TABLE izba ADD FOREIGN KEY (wlascicel) REFERENCES postacie(id);
2. ALTER TABLE izba ADD kolor_izby VARCHAR(20) DEFAULT 'czarny';
   ALTER TABLE izba MODIFY kolor_izby VARCHAR(20) DEFAULT 'czarny' AFTER metraz;
   INSERT INTO izba (adres_budynku, nazwa_izby, metraz, wlascicel) VALUES ('ul.Sloneczna 23, Olsztyn', 'spizarnia', 25, 1);

Zadanie 4.
1. CREATE TABLE przetwory(id_przetworu INT PRIMARY KEY, rok_produkcji INT(4) DEFAULT 'papryczka chilli', id_konsumenta INT);
   ALTER TABLE przetwory ADD FOREIGN KEY (id_wykonawcy) REFERENCES postacie(id);
   ALTER TABLE przetwory ADD FOREIGN KEY (id_konsumenta) REFERENCES postacie(id);
2. INSERT INTO przetwory VALUES('1', '2000', '1', 'kapusta, mieso, marchewka', 'czosnek', '3');

Zadanie 5.
1. INSERT INTO postacie (nazwa, rodzaj, data_ur, wiek) VALUES ('Ragnar','wiking','1994.12.24','27');
   INSERT INTO postacie (nazwa, rodzaj, data_ur, wiek) VALUES ('Floki','wiking','1994.01.12','28');
   INSERT INTO postacie (nazwa, rodzaj, data_ur, wiek) VALUES ('Ubbe','wiking','2002.10.14','20');
   INSERT INTO postacie (nazwa, rodzaj, data_ur, wiek) VALUES ('Ivar','wiking','1972.03.15','50');
   INSERT INTO postacie (nazwa, rodzaj, data_ur, wiek) VALUES ('Drogo','wiking','2004.11.02','18');
2. CREATE TABLE statek(nazwa_statku VARCHAR(50) PRIMARY KEY, rodzaj_statku ENUM('aaa','bbb','ccc'), data_wodowania DATE, max_ladownosc INT UNSIGNED);
3. INSERT INTO statek VALUES('Big Berta', 'aaa', '2022.11.02', '1500');
   INSERT INTO statek VALUES('Wielka Tesciowa', 'ccc', '2022.11.02', '20000');
4. ALTER TABLE postacie ADD funkcja VARCHAR(20);
5. UPDATE postacie SET funkcja='kapitan' WHERE nazwa='Bjorn';
6. ALTER TABLE postacie ADD statek VARCHAR(50);
   ALTER TABLE postacie ADD FOREIGN KEY (statek) REFERENCES statek(nazwa_statku);
7. UPDATE postacie SET statek='Wielka Tesciowa' WHERE nazwa='Bjorn';
   UPDATE postacie SET statek='Wielka Tesciowa' WHERE nazwa='Ragnar';
   UPDATE postacie SET statek='Wielka Tesciowa' WHERE nazwa='Drozd';
   UPDATE postacie SET statek='Wielka Tesciowa' WHERE nazwa='Floki';
   UPDATE postacie SET statek='Big Berta' WHERE nazwa='Ubbe';
   UPDATE postacie SET statek='Big Berta' WHERE nazwa='Ivar';
   UPDATE postacie SET statek='Big Berta' WHERE nazwa='Drogo';
8. DELETE FROM izba WHERE nazwa_izby='spizarnia';
9. DROP TABLE izba;
