# codecademy-sql-training
Free training course on SQL at https://www.codecademy.com/
Retrospective on what I learned first about SQL before training at https://sqlbolt.com/
OFC codeacademy is more like an intro, since it gives you real pieces of executable code.
But I ernestly read the materials and tried to create each query on my own, not just reproduce the code given in the examples.
97% - sucess. Then I moved onto sqlbolt, where the author(s) give(s) only abstractions and actually asks you to come up with your own queries to solve real problems.


# Manipulation

## Introduction

Reading materials.


## Relational Databases

SELECT * FROM celebs;


## Statements

CREATE TABLE celebs ( id INTEGER, name TEXT, age INTEGER);


## Create

INSERT INTO celebs (id, name, age) VALUES (1, "Justin Bieber", 21);

SELECT * FROM celebs;


## Insert

INSERT INTO celebs (id, name, age) VALUES (2, 'Beyonce Knowles', 33);
INSERT INTO celebs (id, name, age) VALUES (3, 'Jeremy Lin', 26);
INSERT INTO celebs (id, name, age) VALUES (4, 'Taylor Swift', 26);

SELECT id FROM celebs;


## Select

UPDATE celebs
SET age = 22 WHERE id = 1;

SELECT * FROM celebs;


## Update 

ALTER TABLE celebs ADD COLUMN twitter_handle TEXT;

SELECT * FROM celebs;


## Alter

UPDATE celebs SET twitter_handle = '@taylorswift13' WHERE id = 4;

SELECT * FROM celebs;


## Delete

UPDATE celebs SET twitter_handle = '@taylorswift13' WHERE id = 4;

DELETE FROM celebs WHERE twitter_handle IS NULL;

SELECT * FROM celebs;



## Constraints

CREATE TABLE awards (id INTEGER PRIMARY KEY, recipient TEXT NOT NULL, award_name TEXT DEFAULT "Grammy");



# Queries

## Select-II

SELECT name, imdb_rating FROM movies;


## Select Distinct
SELECT DISTINCT genre FROM movies;


## Where

SELECT * FROM movies WHERE imdb_rating > 8;


## Like-I

SELECT * FROM movies WHERE name LIKE 'Se_en';


## Like-II

SELECT * FROM movies WHERE name LIKE 'a%';

SELECT * FROM movies WHERE name LIKE '%man%';


## Between

SELECT * FROM movies WHERE year BETWEEN 1990 AND 2000;


## And

SELECT * FROM movies WHERE year BETWEEN 1990 AND 2000 AND genre = 'comedy';


## Or

SELECT * FROM movies WHERE genre = 'comedy' OR year < 1980;


## Order By

SELECT * FROM movies ORDER BY imdb_rating DESC;


## Limit

SELECT * FROM movies ORDER BY imdb_rating ASC LIMIT 3;


# Aggregate Functions

## Count

SELECT * FROM fake_apps;

SELECT COUNT(*) FROM fake_apps;


## Group By

SELECT price, COUNT(*) FROM fake_apps GROUP BY price;


## Sum

SELECT SUM(downloads) FROM fake_apps;


## Max

SELECT name, MAX(downloads) from fake_apps;


## Min

SELECT MIN(downloads) FROM fake_apps;

## Average

SELECT AVG(downloads) FROM fake_apps;


## Round

SELECT price, ROUND(AVG(Downloads), 2) FROM fake_apps GROUP BY price;


# Round


## Multiple Tables

Reading Materials.


## Primary Key

CREATE TABLE artists(id INTEGER PRIMARY KEY, name TEXT);


## Foreign Key

SELECT * FROM albums;
SELECT * FROM artists;
//just two query commands to train to read

SELECT * FROM albums WHERE artist_id = 3;
SELECT * FROM artists WHERE id = 3;


## Cross Join

SELECT albums.name, albums.year, artists.name FROM albums, artists


## Inner Join

SELECT * FROM albums JOIN artists ON albums.artist_id = artists.id; 


## Left Outer Join

SELECT * FROM albums LEFT JOIN artists ON albums.artist_id = artists.id;


##  Aliases

SELECT albums.name AS 'Album', albums.year, artists.name AS 'Artist' FROM albums JOIN artists ON albums.artist_id = artists.id WHERE albums.year > 1980;


## Multiple Table Creation

DROP TABLE IF EXISTS albums;

CREATE TABLE IF NOT EXISTS albums(id INTEGER PRIMARY KEY, name TEXT, year INTEGER, artist_id INTEGER, FOREIGN KEY(artist_id) REFERENCES artist(id));


## Foreign Key Constraints

DROP TABLE IF EXISTS albums;

CREATE TABLE IF NOT EXISTS albums(id INTEGER PRIMARY KEY, name TEXT, year INTEGER, artist_id INTEGER, FOREIGN KEY(artist_id) REFERENCES artist(id));
