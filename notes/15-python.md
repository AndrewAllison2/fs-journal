### Getting Started
  create app.py file

#### VARIABLES
  variable name = value

  _Ex_
  age = 30
  print(age)

  executed top to bottom => will overwrite variables when redeclared

<!-- NOTE Python is case sensitive => bools = True/False -->

# RECIEVING INPUT
  name = input("What is your name?")
  print("Hello " + name)

  <!-- STUB string concatination ^^^^  -->

# MANIPULATE DATA TYPES
  birth_year = input("Enter your birth year: ")
  age = 2024 - birth_year
  print(age)

  __(threw error => int vs string)__

  USE INT FUNCTION!

  birth_year = input("Enter your birth year: ")
  age = 2024 - int(birth_year)
  print(age)

__VALUE CONVERSION FUNCTIONS__
  - int() => convert value to int
  - float() => convert value to floating point number(num w/ decimal point)
  - bool() => convert value to bool
  - str() => convert value to string
