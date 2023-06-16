# Intro to JavaScript
01. Which keywords are used to declare a variable in JavaScript?

    > Let, Const, Var

02. What is the definition of a function?

    > A subprogram that can be invoked to perform a particular task

03. What are the `SOLID` principles?

    > Single Responsibility, Open-Closed Principle, Liskov Substitution Principle, Interface Segregation, Dependency Inversion 

04. Given this array: How could you remove the `pineapple`?

    ```js
    let fruit = ['apple', 'banana', 'pineapple', 'orange', 'strawberry']
    ```

    > let pineapple = fruit[2]

05. Given these two objects: How could you add each to the others friends arrays?

    ```js
    let you = {
        name: "You",
        hair: true,
        friends: []
    }
    let them = {
        name: "Them",
        hair: false,
        friends: []
    }
    ```

    > you.friends += them.friends

06. Give an example of a JavaScript `Conditional`:

    > if statement

    if(numb > 10)
    return

07. What is the main difference between `parameters` and `arguments`?

    > Parameters are the names created in the function definition. Arguments are the values function recieves from parameters.

08. Instead of writing everything to the console, what is a better way to debug your code?

    > Writing checks that can be used multiple times to make sure new code is working.

09. What is the difference between a `primitive` value and a `reference` value?

    >   A primitive value is the assigned value of a variable. Reference values can be null, and refer to information related to a variable. 

10. Demonstrate a loop that prints the numbers between -100 and 100?

    > for (let i = 0; i < numb.length; i++) {
  const element = numb[i];
    if (element > -101 && element<101) {
      console.log(element);
    }
}
