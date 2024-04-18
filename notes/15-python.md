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
  print(10 + 3) = 13
  print(10 - 3) = 7
  print(10 * 3) = 30

  print(10 / 3) => floating point number = 3.33333335
  print(10 // 3) => integer = 3
  print(10 % 3) => remainder of 10/3 = 1
  print(10 ** 3) => exponent multiplier = 1000

  Augmented Assignment Operator
    x += 3
    x *= 3

<!-- NOTE Python follows standard Order of Operations when doing math -->

### Logical Operators
__AND__
  price = 25
  print(price > 10 and price < 30)
  output = True

__OR__
  price = 5
  print(price > 10 or price < 30)
  output = True (because price is less than 30)

__NOT__
  price = 5
  print(not price > 10)
  output = True (because price is not greater than 10)

### If Statements
  work similar to Javascript if
  
  __elif__ is shorthand for if else

<!-- NOTE PYTHON USES INDENTATION FOR CODE BLOCKS INSTEAD OF {} -->

_Ex_
temp = 5
if temp > 30:
  print("It's a hot day!")
elif temp > 20:
  print("It's pretty nice out!")
elif temp < 15:
  print("Don't go outside!")

### WHILE LOOPS
  repeat code block multiple times

i = 1
  while i <= 5:
    print(i)
    i ++

i = 1
  while i <= 10:
    print(i * '*')
    i ++
  output => * for 1 ** for 2 ect

### Lists

names = ["John", "Bob", "Sam", "Mary"]
  print(names[0]) => return "John"

can use negative indexes => -1 is last index on list

names[0:3] => returns elemnts at index 0, 1, 2 => returns new list

##### LIST METHODS
  numbers = [1, 2, 3, 4, 5]

  numbers.append(6) => [1, 2, 3, 4, 5, 6] (append new item to end of list)

  numbers.insert(0, -1) => [-1, 1, 2, 3, 4, 5, 6] expects index then value

  numbers.remove(3) => [1, 2, 4, 5]

  numbers.clear() => empties array

  print(1 in numbers) => True (1 exists in the array)

  print(len(numbers)) = 5 (returns number of elements in the array)

### FOR LOOPS
  numbers = [1, 2, 3, 4, 5]
  for item in numbers:
    print(item)

    i = 0
    while i < len(numbers):
      print(numbers[i])
      i ++

  <!-- STUB THESE DO THE SAME THING ^^^^^^^ -->

### RANGE FUNCTION
  numbers = range(5) => returns range object (object that can store a sequence of objects)
    print(numbers) = range(0, 5)

  numbers = range(5)
  for number in numbers:
    print(number)

    if 2 values first value is starting point
    3rd value is step => if we pass 2 we return odd numbers

### TUPLES
  used to store a sequence of objects but they are __IMMUTABLE__

  numbers = (1, 2, 3) => parens for Tuple
  only have .count() and .index()

  used when data should not be changes of manipulated
