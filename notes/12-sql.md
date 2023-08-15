# SQL

### DB SETUP

  - primary keys ALWAYS have to be unique and not null
  - comments can be left on columns for better intel
  - SQL statements end with a semicolon (;)

- id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, -> gives each new thing store in the database a unique id

- SQL handles checks on the data that is being sent up

- default charset utf8 -> must have this for every table -> sets default font for db

<!-- REVIEW THROWS ERRORS

  - trailing comas
  - not setting default font

 -->


##### Create Data

- INSERT INTO capybaras(name, ownedByGrandma, birthday, applesEaten)
  VALUES
  ('Cappy', true, '1990-12-12', 1000),
  ('Lil Cappy', false, '2020-12-12', 7);

- adds 2 capybaras (Cappy and Lil Cappy) to the table in the db

##### ORM Dapper

 - supply dapper with SQL statements

SELECT name FROM capybaras; -> on execute returns the name column with all rows within it

SELECT name, applesEaten FROM capybars -> return name and applesEaten

SELECT * FROM capybaras -> retruns everything in capybaras

SELECT * FROM capybaras WHERE id = 2;

WHERE name LIKE %cappy% -> returns cappy and lil cappy -> all names that are like cappy

DELETE FROM capybaras WHERE id = 2;
