### Section Overview
  - Can you explain how JS works
  
### JavaScript Engine
  - Computer doesnt really know what JS is, it understands 1s and 0s
  - There are many different kinds of JavaScript Engines, also known as ECMAScript Engines
  - JavaScript Engines take in JS files and convert it to a language that a computer can understand
  - Google built their own JS engine (V8) for google maps, because other JS engines were too basic for their application (google maps)
  - Google built their own browser to be able to control more of the market.
  
### Who created the first JavaScript Engine?
  - Brendan Eich (also createor of JavaScript)
  
### Inside the Engine
  - Whats inside the JavaScript Engine?
  - Before the JS Engine reads the JS File, it does something called 'Lexical Analysis'.
  - Lexical Analysis breaks the code into something called tokens.
  - Tokens are formed into an AST (Abstract Syntax Tree) -> (astexporer.net is an online tool to demo this)
  - Parser -> AST -> Interperter -> Profiler -> Compiler -> Optimized Code -> Computer
  
### What problem do you see with everybody creating their own engines in JavaScript?
  - ECMAScript is the governing body of JavaScript
  - ECMAScript tells engines creators how JavaScript should be standardized
  - Ex. Google interested in having fastest engine so that more people use their browser to create more ad revenue

### Interpreters and Compilers
  - Two ways to run JavaScript, Interpreter and Compiler
  - Interpreter translates and read JS files line by line. 
  - Compilers tries to understand what the JS files want to do. 
  - Interpreter will read a JS file line by line and spit out 'Bytecode'
  - Compiler wll read a JS file and spit out 'Machine Code' to give to a CPU so that the CPU can run the code. 
  
### Babel + TypeScript
  - Babel & TypeScript are heavily used in the JavaScript ecosystem.
  - Babel is a JavaScript compiler that takes your modern JS code and returns browser compatible JS (older JS code).
  - Typescript is a superset of JavaScript that compiles down to JavaScript.
  - Both do exactly what compilers do: take one language and convert it into a different one.
  
### Inside the V8 Engine
  - One problem an Interpreter may encounter is running same code more than once (for loops) can make it really slow.
  - JIT Compiler (Interpreter + Compiler)
  - Google's V8 JS Engine Example (Parser -> AST -> Interpreter (Spits out bytecode) -> Profiler -> Compiler -> Optimized Code
  - Parse: Code is parsed into AST (Abstract Syntax Tree)
  - AST: Code initially goes to interpreter
  - Interpreter: Spits out Bytecode that can be interpreted by JS Engine 
  - Profiler: Monitor and watches code as it runs
  - Compiler: As application is running, takes code and compiles/modifies it, making optimizations
  - Optimzed Code: 
  
  
  
  
  
  
  
  
