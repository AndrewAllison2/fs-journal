# CSharp and SQL Fundamentals
01. What is the purpose of a `namespace`?

  > Namespace acts similarly to export, allowing other parts of the app to use the code inside of it.

02. What is the difference between a `class` and an `interface`?

  > An interface is a contract that contains only method declarations. A class extends or implements an interface and contains the declaration and definitions of those methods.

03. What is the method that returns an instance of a class, yet it has no return type?

  > A constructor

05. In the Car example what is the access modifier of the `Start()` method?

  ```c#
  abstract class Car
  {
    public string Start()
    {

      return "Vroooom";

    }
  }
  ```

  > public

06. In the Car example what is `string` an indication of?

  > The data type that will be returned.

07. In the Car example what is `abstract` preventing?

  > The method from being implemented on its own.

08. In a SQL table, what is the difference between information in a row and information in a column?

  > Columns are the properties we are storing in our database, rows are the actual data being stored.

09. Demonstrate the necessary SQL for creating a table called `characters` with the values `name, age, description` as strings, and an `int` id.

  > CREATE TABLE charachters(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    age VARCHAR(255) NOT NULL,
    description VARCHAR(700) NOT NULL
  ) default charset utf8;

10. In SQL how can you query more than a single table? Provide an example.

  > By using the JOIN operator

  <!-- took this example from my AllSpice checkpoint code -->

  string sql = @"
    SELECT
    rep.*,
    acc.*
    FROM recipes rep
    JOIN accounts acc ON acc.id = rep.creatorId
    WHERE rep.id = @recipeId LIMIT 1
    ;";

