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


  _Ex_
    First: 10.1
    Second: 20
    Sum: 30.1

    first = input("First: ")
    second = input("Second: ")
    sum = float(first) + float(second)
    print("Sum: " + sum) => error so
    print("Sum: " + str(sum))


    # NOTE Python doesnt know how to concatinate a float with a string 

    first = float(input("First: "))
    second = float(input("Second: "))
    sum = first + second

### Strings
  __Strings are immutable in Python__

  course = 'Python for Beginners'
    .upper() => returns NEW string, does not overwrite variable
    .lower() => returns NEW string, does not overwrite variable
    .find() => see if string contains character/sequence of characters => __index of frist character is 0__
    .replace() => change string content => .replace('for', '4') => output = Python 4 Beginners 
    
    _IN_ operator
    course = 'Python for Beginners'
    print('Python' in course) => output = true

### Math Operations
  
