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
<!-- NOTE use new to create new controller -->
