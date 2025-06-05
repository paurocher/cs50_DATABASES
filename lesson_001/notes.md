# lesson001

# Relating (Relational databases)

.tables -> sqlite3 command (not a SQL )

One to One Relationship  /  One to Many Relationships  /  Many to Many Relationships

#### ER -> Entity Relationship Diagram
Represent the relationships between tables in a diagram

lines:
 - zero: arrow with an 0
 - one: an arrow with one single perpendicular line
 - many: an arrow with 2 lines


#### KEYS
Used to relate tables.

- **Primary Key**: it is unique to each element in the table  
- **Foreign Key**: when you take the primary key of another table and include it in a new table


### Subqueries or nested queries
Put one query inside of another.

One to many relationship:
```
SELECT "title" FROM "books"
WHERE "publisher_id" = (
    SELECT "id" FROM "publishers"
    WHERE "publisher" = 'Fitzcarraldo Editions'
);
```

Many to many relationship:
```
SELECT "name" FROM "authors" 
WHERE "id" = (
    SELECT "author_id" FROM "authored" 
    WHERE "book_id" = (
        SELECT "id" FROM "books" 
        WHERE "title" = 'The Birthday Party'
    )
);
```

#### IN
IN allows us to pass a set of values instead of just one.

```
SELECT "title FROM "books" WHERE "id" IN (
    SELECT "book_id" FROM "authored" WHERE "author_id" = (
        SELECT "id" FROM "authors" WHERE "name" = 'Fernanda Melchor'
    )
);
```

### JOIN
Combines tables.

```sqlite3 sea_lions.db
.tables
```

```
SELECT * FROM "sea_lions";
SELECT * FROM "migrations";
```

```
SELECT * FROM "sea_lions"
JOIN "migrations" ON "migrations"."id" = "sea_lions"."id";
```

#### INNER JOIN
This is the usual JOIN.
Rows from both tables that do not have a match are dropped: if we are joining by id, if some ids from table a do not exist on table b (and vice versa) all those rows are not shown.

#### LEFT JOIN, RIGHT JOIN, FULL JOIN
Prioritises the table A, the B or both.

Left join gives prio to the first table provided. If there are rows that do not corresponf on the B table, they still are shown:
```
SELECT * FROM "sea_lions"
LEFT JOIN "migrations" ON "migrations"."id" = "sea_lions"."id";
```

Right join does the opposite:
```
SELECT * FROM "sea_lions"
RIGHT JOIN "migrations" ON "migrations"."id" = "sea_lions;
```

FULL JOIN will show everything, even the rows without match on both tables:
```
SELECT * FROM "sea_lions"
FULL JOIN "migrations" ON "migrations"."id" = "sea_lions";
```

#### NATURAL JOIN
Will figure out how to join tables based on the data it finds exist on both tables. Drops the unmatched rows.
```
SELECT * FROM "sea_lions"
NATURAL JOIN "migrations";
```

video: 1:18:57