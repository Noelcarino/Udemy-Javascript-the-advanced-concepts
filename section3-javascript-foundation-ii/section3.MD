### Execution Context
  - As soon as the JS Engine sees '()', it creates something called an Execution Context.
  - After the JS Engine creates an Execution Context, it adds it to the Call Stack.
  - Global Execution context is the base execution context.
  - Global Execution context is created initially under the hood.
  - Global Execution context gives us two objects: 'Global Object' and 'this'.
  - In the browser, the global object is 'window'.
  - Creation phase is the first phase in the JavaScript engine.
  - Execution phase is the 2nd phase in the JavaScript engine.
  
### Lexical Enviornment
  - Lexical Environment is simply where we write something.
  - Lexical Analysis is when the JS Engine checks where the code was written.
  - In JavaScript our lexical scope (available data + variables where the function was defined) determines our available variables. Not here the function is called (dynamic scope)
  - Global Lexical environment is the very first lexical environment.

### Hoisting
  - In the creation phase, there is one more step, hoisting.
  - Hoisting is the behavior of moving functions and variables to the top of their respective environments during compilation phase
  - If we console a variable before we define it, it is undefined.
  - If we console a function before we define it, it is defined because of hoisting.
  - Hoisting is the JavaScript engine allocating memory for the variables and functions that it sees in our code during creation phase, before its executed.
  - If there is a '()' surrounding the defined function, it won't hoist the function.
  - 'const' and 'let' are not hoisted.
  - 'Function Expression' is a function defined by a variable
  - 'Function Declaration' is a regular defined function
  
### Exercise: Hoisting 1, 2, & 3

  Code:
  ```
  var favoriteFood = "grapes";
  var foodThoughts = function(){
    console.log("Original favourite food: " + favouriteFood);
    
    var favouriteFood = "sushi";
    
    cosole.log("New favourite fooD: " + favouriteFood);
  };
  
  foodThoughts();
  ```
  
  Execution:
  - The code will display:
  ```
    Original favourite food: undefined
    New favourite food: sushi
  ```
  - The reasoning is because inside the function expression, favouriteFood is hoisted and set as undefined, then the code console is executed with favouriteFood as 'undefined'
  
  Code:
  ```
  function bigBrother(){
    function littleBrother() {
      return 'it is me!';
    }
    return littleBrother();
    function littleBrother() {
      return 'no me!';
    }
  }

  // Before running this code, what do you think the output is?
  bigBrother();
  ```
  
  Answer:
  ```
    'no me!';
  ```
  - The reasoning is because the second function declaration of littleBrother is hoisted to the top of the function declaration bigBrother 
  
### Function Invocation
  - A function declaration is a function that starts with a function keyword
  - A function declaration is defined at parse time, when compiler is initially looking at code, and hoisting/allocating memory
  - A function expression is a function that starts with the var keyword
  - A function expression is defined at runtime
  - A function invocation is simply running/calling a function
   
### Arguments
  - Instead of using 'arguments', we can use the 'Array.from(arguments)' to change arguments into an array, which allows us to use array methods.
  - In each execution context, we create a new 'arguments' object.
  
### Variable Environment
  - Execution context also contains a variable environment.
  - variable environment is where information is stored
  - Each execution context has its own variable environment.

### Scope Chain
  - Each execution context has a link to its parent (outer environment)
  - Each function has their own variable environment
  - Each variable environment has a 'scope chain', gives us access to parent chain (global environment)
  - In JavaScript our lexical scope (available data + variables where the function was defined) determines our available variables. Not where the function is called (dynamic scope)
  - If a function returns a function, we can add another parenthesis too the end of the function we called -> sayMyName()()

### [[scope]]
  - When a function is called, an environment is created for the new scope it enters.
  - If we defined a function, we can find that function within [[scopes]], where we can find the type of scope it is in.

### Exercise: JS is Weird
  - 'use strict' prevents variable leakages
  - In a case where we use 'use strict', we would use it to prevent variables not defined using 'var'.
  - Example 1:
  
  ```
    function weird() {
      height = 50;
      return height
    }
    weird()
  ```
  - returns 50.
  - adding 'use strict' example
  ```
    'use strict'
    function weird() {
      height = 50;
      return height
    }
    weird()
  ```
  - returns 'ReferenceError: height is not defined'
  
  -Example 2:
  ```
    var heyhey = function doodle() {
      // do something
      return 'heyhey'
    }
    heyhey()
  ```
  - returns 'heyhey'
  - but running 'doodle()' returns 'ReferenceError: doodle is not defined, because doodle is added to its own execution context variable environment

### Function Scope vs Block Scope
  - To be Functionaly scoped means that any time we have a function, JavaScript creates a new environment. 
  - To be Block scoped means that we cannot access we cannot access anything within '{}'.
  
### Exercise: Block Scope
  ``` 
    function loop() {
      for (let i = 5; i < 5; i++){
        console.log(i)
      }
      console.log('final', i)
    }
    loop()
  ```
  - returns i is not defined. 
  - this is the case because of the 'let' keyword. 'i' is only defined within the block scope
  
### IIFE
  - Immediately Invoked Function Expression:
    ```
    (function(){

    })();
    ```
  - IIFE alows us to call immediately as JS is executing

### this Keyword
  - 'this' is the object that the function is a property of
  - When we do something inside of a function, we have access to the 'this' keyword
  - we don't want 'this' to refer to the global object, rather the function that it is in, we can add 'use strict' to fix that
  - example of using 'this' keyword
  ```
    cont obj = {
      name: 'Billy',
      sing: function() {
        return 'lalala ' + this.name
      },
      singAgain(){
        return this.sing() + this.name + '!'
      }
    }
  ```
  - Example 2
  ```
    function importantPerson(){
      console.log(this.name+'!')
    }
    
    const name = 'Sunny';
    const obj1 = {
      name: 'Cassy',
      importantPerson: importantPerson
    }
    const obj2 = {
      name: 'Jacob',
      importantPerson: importantPerson
    }
  ```
  - We can access obj1 and obj2 'importantPerson' using [obj1.importantPerson || obj2.importantPerson]

### Exercise: Dynamic Scope vs Lexical Scope
  - Exercise 1
  ```
    const a = function() {
      console.log('a',this)
      const b = function() {
        console.log('b',this)
        const c = {
           hi: function() {
           console.log('c', this)
          }
        }
      }
    }
  ```
  
        c.hi()
      }
      b()
    }
    a()
  ```
  - Exercise 2
  ```
    const obj = {
      name: 'Billy',
      sing() {
        console.log('a', this);
        var anotherFunc = function(){
          console.log('b', this)
        }
        anotherFunc()
      }
    }
  ```
  - calling obj.sing() returns the obj of the function we called, however, 'anotherFunc()' returns this window.
  - 'this' keyword is not lexically scoped. Means it doesnt matter where it was written, but how it was called.
  - In JavaScript our lexical scope (available data + variables where the function was defined) determines our available variables. Not where the function is called (dynamic scope)
  - Everything in JavaScript is lexically scoped, except for 'this' keyword
  - 'Arrow Functions' help fix the behavior of 'this'. It will lexically bind the 'this' keyword
