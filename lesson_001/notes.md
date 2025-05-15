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
