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

