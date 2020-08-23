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
  
  
  
