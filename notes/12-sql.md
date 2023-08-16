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

<!-- NOTE POST -->

- INSERT INTO capybaras(name, ownedByGrandma, birthday, applesEaten)
  VALUES
  ('Cappy', true, '1990-12-12', 1000),
  ('Lil Cappy', false, '2020-12-12', 7);

- adds 2 capybaras (Cappy and Lil Cappy) to the table in the db

##### ORM Dapper

 - supply dapper with SQL statements

<!-- NOTE GETS -->

SELECT name FROM capybaras; -> on execute returns the name column with all rows within it

SELECT name, applesEaten FROM capybars -> return name and applesEaten

SELECT * FROM capybaras -> retruns everything in capybaras

SELECT * FROM capybaras WHERE id = 2; -> returns entire row with the id of 2

WHERE name LIKE %cap% -> returns cappy and lil cappy -> all names that are like cappy

SELECT * FROM  capybaras LIMIT 1 OFFSET 1; -> returns 2nd capybara in table

<!-- NOTE DELETE -->

DELETE FROM capybaras WHERE id = 2 LIMIT 1; -> deletes entire row where the id is 2

<!-- NOTE UPDATE -->

UPDATE capybaras
SET
applesEaten = 500
WHERE id = 2  -> if we don't target anything it will update all rows' applesEaten to 500
LIMIT 1 

##### ALTER TABLE

  ALTER TABLE capybaras
  ADD
  livesAtFarm BOOLEAN NOT NULL DEFAULT FALSE; -> provide default so other data will get new property

OR

DROP TABLE capybaras; -> move new property into create table -> run create table


## GREGSLIST BUILD

- create the car table in the DBSETUP
- insert cars into cars table

<!-- SECTION CONNECTING TO DB WITH C# -->
  - appsettings.Development.json
    - server = 'connection string'
    - userId = user we made
    - password = password for the user

  - STARTUP -> comment out config auth
  - write a model -> generate class temp, use prop snippet to generate properties
  - create model based off of the table -> do not need constructor on models

  - create CARSCONTROLLER -> generate api controller
  - 
    - private readonly CarsService _carsService -> dependancy
    - ctrl + . to generate constructor

#### REPO LEVEL
  In the CARSREPOSITORY

  - private readonly IDbConnection _db; -> right click to generate constructor

    internal List<Car> GetCars()
    {
      string sql = "SELECT * FROM cars;"

      List<Car> cars = _db.Query<Car>(sql).ToList();

      return cars;
    }

<!-- NOTE in STARTUP we have to add cars service/repo as dependencies -> will give error 500 if forgotten -->

#### GET CAR BY ID

<!-- SECTION DON'T DO THIS BECAUSE IT ALLOWS SQL TO BE PASSED TO OUR DB SO USERS CAN EDIT THE DB -->
internal Car GetCarById(int cardId)
{
  string sql = $"SELECT * FROM cars WHERE id = {carId};"

  Car car = _db.QueryFirstOrDefault<Car>(sql); ---> like FindOne in Mongoose

  return car;
}

<!-- SECTION PROTECTS AGAINST MALICIOUS USERS -->
internal Car GetCarById(int cardId)
{
  string sql = $"SELECT * FROM cars WHERE id = @carId;"

  Car car = _db.QueryFirstOrDefault<Car>(sql, new {carId}); ---> like FindOne in Mongoose

  return car;
}

- creates new pojo with a key of carId and value of what was passed down

- @ means we want to inject something into sql string

<!-- NOTE PARAMETERIZE ANYTHING WE WANT TO INJECT INTO A SQL STRING -->

<!-- SECTION -->
#### POST REQUEST

  string sql = @"
  INSERT INTO cars (make, model, color, price, year, ownedByGrandma)
  VALUES (@Make, @Model, @Color, @Price, @Year, @OwnedByGrandma);
  SELECT LAST_INSERT_ID()
  ;";

  int carId = _db.ExecuteScalar<int>(sql, carData); -> will post a car and return that new car's id

  carData.Id = carId;
  return carData;

  - in DBSETUP write method to get the last id inserted into our db


  - changed response in repo to INT and return INT to service

IN SERVICE LEVEL
  run Car car = GetCarById(carId)

<!-- REVIEW CREATE CAR REQUEST BETWEEN SERVICE AND REPO -->

<!-- SECTION -->
#### DELETE REQUEST

  - returning string to user so service and repo are void and are not expected to return anything

  internal void RemoveCar(int carId)
  {
    string sql = "DELETE FROM cars WHERE id = @carId;"

    _db.Execute(sql, new {carId})
  }

  set up error handling in service -> GetCarById and RemoveCar

    if(car == null)
    {
      throw new Exception("")
    }

<!-- SECTION -->
#### Put Request

  - supply with params and a body

  SERVICE
  
  internal Car UpdateCar(int carId, Car carData)
  {
    Car originalCar = GetCarById(carId);

    originalCar.Make = carData.Make ?? originalCar.Make; -> null check

    Car car = _carsRepository.UpdateCar(originalCar) -> original car is now storing our id
    return car;
  }

  internal Car UpdateCar(Car originalCar)
  {
    string sql = @"
      UPDATE cars
      SET
      make = @Make,
      model = @Model,
      color = @Color
      WHERE id = @Id -> dapper looks through object and finds all the properties
      LIMIT 1;
      SELECT * FROM cars WHERE id = @Id
      ;";

      <!-- _db.Execute(sql, originalCar); -->
      review repo for the return on an edit
      return 
  }


put ? on model to allow it to be null -> see CAR model
  - this sets prop to null on edits and sets value to null if not supplies so we can do a null check in service level of edit

<!-- REVIEW -->
  - QueryFirstOfDefault = give me one item back or null
  - ExecuteScalar = return the first numerical value
  - Execute = run sql and don't return anything
  - Query = returnn an array of things


## WEDNESDAY LECTURE

### SQL AND C# WITH AUTH

  - fill out appsetting in backend and env.js in client
  - change base url to 'https://localhost:7045'

  - execute create account table

  - create album table in dbSetup

<!-- NOTE ENUM IN SQL DATABASE -->
  category ENUM ('misc', 'cats', 'dogs', 'games') DEFAULT 'misc',

<!-- NOTE CREATOR ID IN SQL -->
  creatorId VARCHAR(255) NOT NULL -> data type should match whatever it's referencing

#### FOREIGN KEY
  FOREIGN KEY(creatorId) REFERENCES accounts(id) ON DELETE CASCADE -> when account is deleted, it will delete all data they made

  - account id must match something in the SQL account table

#### GETTING STARTED
  - create model/controller/service/repo

    - enum written as string in model
    - creatorId is string datatype

  @ when passing dapper an object --- DO NOT STRING INTERPOLATE

  - albumData.Id = albumId -> dont have a find by id method yet

 <!-- SECTION PULL USERS INFO FROM REQUEST BODY -->

    - example in account controller

    Account userInfo = await _auth0Provider.GetUserInfoAsync<Account>(HttpContext);

  - create another dependency in albums controller
    - private readonly Auth0Provider _auth0Provider

    - ctrl + . "add params to constructor"

  - IN POST REQUEST IN ALBUMCONTROLLER
      Account userInfo = await _auth0Provider.GetUserInfoAsync<Account>(HttpContext);

<!-- NOTE WHENEVER WE GET USER INFO THE METHOD MUST BE ASYNC AND WE AWAIT RESULTS -->

  public async Task<ActionResult<Album>> Create Album([FromBody] Album albumData)

  albumData.CreatorId = userInfo.Id; -> ALBUMCONTROLLER

<!-- NOTE HttpContext is like req and res in NODE -->

<!-- SECTION ADD AUTH TO METHOD -->
[Authorize]     only the post method now requires user to log in
[HttpPost]