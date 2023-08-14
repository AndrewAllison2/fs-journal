# CSharp

<!-- SECTION -->
## Monday

<!-- NOTE curly bois go on line underneath method -->

#### Declaring Variables

##### Strings

  - denote type of varibale when declaring

string name = "Name";

Console.WriteLine(name);

<!-- NOTE c# will not compile/run with errors in code -->

Most lines of code end with semicolon ;

char - single character

<!-- NOTE STRING INTERPOLATION -->

Console.WriteLine($"Hello, my name is {firstName} {middleName} {lastName}");

Call methods when using on strings -> error involving method and read only

<!-- NOTE C# is written in Pascal case -->

##### NUMBERS

 - int -> integer

 int num =3;

 int halfNum = 2.5; => cannot implicitly convert type double to int -> call data double
    so...
double halfNum = 2.5;

<!-- NOTE Double is data type for decimal numbers -->

Console.WriteLine(num + halfNum); -> works

double total = num + halfNum; -> works

##### Boolean

bool likesCats = true;

if(likesCats)
{
Console.WriteLine("This is true")
}

<!-- NOTE CONDITIONALS REQUIRE BOOL OR SOMETHING THAT EQUATES TO A BOOL -->
if(firstName == "Not Name")
{
  Console.WriteLine("This is my name")
}

  ... does not log

=== does not exist in C#
! bang op does exist

###### Array

int [] numbers = {1, 2, 3, 4, 5};

for(int i = 0; i > numbers.Length; i++)
{
  int number = number[i];
  Console.WriteLine(number);
}

<!-- SECTION -->
#### Lists

 - BUILD OUT NEW LIST
    List<string> names = new List<string>();

    names.Add("Sam");
    names.Add(name) -> variable declared above
    names.Add("Stinky")

    Adding strings to our names list ^

    foreach(string name in names)
    {
      Console.WriteLine($"My name is {name}")
    }

    names.Remove("Stinky") -> remove first thing name "Stinky" from list

    Edabit C# challenges


<!-- SECTION -->
### C# APP

  dotnet-auth

  program.cs is entry point to C# programs
  namespace = acts like export in js/ using acts like import -> namespace and public allows other parts of app to use this code

##### Models/Classes

  - set up model/classes -> right click to have vs generate template based on what we are setting up -> Cat.cs

<!-- NOTE PROP code snippet to generate code for schema -->

  public class Cat
  {
    public string Name {get; set;}
    public int Age {get; set;}
    public bool HasTail {get; set;}
    public double NumberOfLegs {get; set;}


  <!-- constructor -->
    public Cat(string name, int, age, bool hasTail, double numberOfLegs)

  <!-- pass values through constructor and assign them to class -->
    {
      Name = name;
      Age = age;
      HasTail = hasTail;
      NumberOfLegs = numberOfLegs;

    }
  }

##### Cats Controller

<!-- NOTE use right click new to create new controller -->


public class CatsController : ControllerBase
{
  <!-- this will apply to the FIRST method underneath it -->
  [HttpGet]

  public string Test()
  {

    return "Test worked";
  }
}

#### Get Cats

public class CatsController : ControllerBase
{
  private readonly CatsService _catsService;

  public CatsController(CatsService catsService)
  {
    _catsService = catsService;
  }

  [HttpGet]

  <!-- NOTE ActionResult allows us to return http responses like Ok and BadRequest -->
  <!-- NOTE right click generate constructor to build above out -->

  public ActionResult<List<Cat>> GetCats()
  {
    try
    {
      List<Cat> cats = _catsService.GetCats()
      return Ok();
    }
    catch (Exception e)
    {
      return BadRequest(e.message);
    }
  }
}

<!-- SECTION -->
#### SERVICE GETTIN' CATS

public class CatsService
{
  private readonly CatsRepository _catsRepository;

  public CatsService(CatsRepository catsRepository)
  {
    catsRepository
  }

  internal List<Cat> GetCats()
  {
    List<Cat> cats = _catsRepository.GetCats()
  }


}

#### Cats Repository

  - create CatsResposity

public class CatsRespository
{
  private List<Cat> dbCats;

  public CatsRepository()
  {
    dbCats = new List<Cat>();
    dbCats.Add(new Cat("Gopher", 2, true, 4));   <--- creating fake database
  }
  internal List<Cat> GetCats()
  {
    return dbCats;
  }

}


- build class
- controller
- service
- repository
- setup


<!-- SECTION -->
Unhandled exception error (dependancy)
  - startup builds out all services/repos -> go to startup and have it build out services/repo

  services.AddScoped<CatsRepository>();
  services.AddScoped<CatsService>();


#### Get Cat By Name
 - in controller

[HttpGet("{catName}")]

public ActionResult<Cat> GetCatByName(string catName)
{
  try
  {
    Cat cat = _catsService.GetCatByName(string catName);
    return Ok(cat)
  }
  catch(Exception e)
  {
    return BadRequest(e.message)
  }
}

pass this to service

 - in repo

 internal Cat GetCatByName(string catName)
 {
  Cat foundCat = dbCats.Find(cat => cat.Name == catName);
  return foundCat;
 }

##### Returned Null - Business Logic

in service

if(cat == null)
{
  throw new Exception($"No cat with the name of {catName}")
}

##### Post Request
[HttpPost]
public ActionResult<Cat> CreateCat([FromBody] Cat catData)
{
  Cat cat = _catsService.CreateCat();
  return Ok(cat);
}


today change repo in setup to AddSingleton

[HttpDelete("{catName}")]
public ActionResult<string> RemoveCat(string catName)