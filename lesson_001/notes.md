# Different DB systems
MySQL
Oracle
PostgreSQL
SQLite

SQL = Structured Query Language


# SQL commands

SELECT column_name FROM table_name;
SELECT * FROM table;


#### Aggregate functions
COUNT, AVG, MIN, MAX, SUM, ROUND
SELECT COUNT(column) FROM table;
SELECT ROUND(AVG("rating"), 2) FROM "longlist" AS "average rating";


#### Condition
SELECT column FROM table WHERE condition0 AND condition1;
SELECT column FROM table WHERE condition0 OR condition1;
SELECT column FROM table WHERE column LIKE value;
SELECT column FROM table WHERE column = value;

#### String matching
LIKE %: matches any char around the given string 
LIKE _: match any single char
SELECT "title" FROM "longlist WHERE "title" LIKE '%love%';
SELECT "title" FROM "longlist WHERE "title" LIKE '%love%';
SELECT "title" FROM "longlist WHERE "title" LIKE 'P_r_';

#### Other
ORDER BY / LIMIT number
SELECT "title, "rating", "votes FROM "longlist" ORDER BY "rating" DESC, "votes DESC LIMIT 10;

#### Ordering
SELECT MAX("title"), MIN("title") FROM "longlist";

.quit


#### All keywords
SELECT, FROM
WHERE
COUNT, AVG, MIN, MAX, SUM
AND, OR
NOT (negate condition), LIKE, = (equals), != (not equal), <> (not equal), <, <,<=, >=
ORDER BY, ASC, DESC
LIMIT
NULL (it is a possible value ...)
ROUND(number, number_of_decimals)
AS (rename a column)
DISTINCT (duplicate values only appear once)