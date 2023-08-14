# CSharp

<!-- SECTION -->
## Monday

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