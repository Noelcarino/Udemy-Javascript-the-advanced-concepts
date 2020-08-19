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

### Writing Optimized Code
  - 'inline caching' optimizes code that is run multiple times.
  - 'Hidden Classes'
  - When instantiating object properties, we want to make sure it is in the same order.
  - Key take away from these is to write code that is predictable.

### WebAssembly
  - Why not use machine code from the beginning?
  - Other competing browsers would have to agree on some binary executable format or standard that can understand machine code.
  - Having other browsers agree on an executable format to run JavaScript lead to browsers not getting along.
  - 'WebAssembly' is a standard binary executable format.
  
### Call Stack and Memory Heap
  - We need a place to store and write information (store our variables, objects, data of apps).
  - We need a place to run and keep track of whats happening line by line in our code.
  - 'Memory Heap' place to store and write information.
  - 'Call Stack' plae to run and keep track of whats happening.
  - 'Memory Heap' where memory allocation happens.
  - 'Call Stack' is where the engine keeps track of where code is in execution.
  - When defining a number, we are allocating memory for the number
  - When defining a string, we are allocating memory for the string
  - When defining an object, we are allocating memory for object and its values.
  - 'Memory Heap' is a simply a free store, large region in memory provided by JS Engine.
  - Whenever a function is being called, it checks allocated memory for function, then adds function to call stack that operates in 'First In Last Out' mode

### Stack Overflow
  - 'Stack Overflow' is when happens when you call a function within a function over and over
  - 'Recursion' is a function that calls itself, it is also an example of creating a Stack Overflow
  - Back in the day, when the call stack kept increasing / stack overflow happened, the browser would crash. Now there is a maximum call stack size.

### Garbage Collection
  - JavaScript is a garbage collected language, meaning when JavaScript allocates memory, it cleans up the used allocated memory when its done being used.
  - Allocated memory is cleaned up because of limited memory.
  - In a low level language like C, you control the memory waste managment, which is dangerous / and also why the language is fast and memory efficient.
  - Having control of memory waste management allows you to optimize it.
  - If we define a variable inside a function, the variable will be marked and sweeped once the call stack is done.

### Memory Leaks
  - An example of creating a memory leak is an endless for loop that continues pushing into an array.
  - There are three common memory leaks: Global Variables, Event Listeners, setIntervals
  - 'Global Variables' - We don't want too many global variables because too much memory will be allocated.
  - 'Event Listeners' - Event listeners are continously added in the background, never removed when we don't need them.
  - As users goes back and forth between single page applications, event listeners are continously added, not removed.
  - 'setInterval' - if setinterval is not cleared / keeps running, the objects being referenced inside the function will never be cleared for allocated memory.
  - An real world example is SoundCloud's incident. They had an application that worked on a gaming device which allowed it to run in the background of the game console.
  - Because the application wasn't closed for hours, the memory leak kept increasing. 
  
### Single Threaded
  - JavaScript is a single threaded language, meaning only one set of instructions is executed at a time.
  - One way to check if a language is single threaded is how many call stacks it has. JavaScript only has one call stack.

### Exercise: Issue with Single threaded Code
  - What problems do you see with synchronous code?
  - It will make it really difficult if we have long running tasks.
  - An example is Twitter, running on one function. We can reveal this by adding the alert function to the call stack. 

### JavaScript Runtime
  - JavaScript is a single threaded programming language, it only has one stack, one heap.
  - If any other program wants to execute something, it has to wait until the previous program is finished executing.
  - Web Browser is working in the background while synchronous JavaScript code is running.
  - Web API is being used to communicate
  - The window object is provided by the browser.
  - Browsers use low level programming languages in the background. 
  - Web APIs are asynchronous, meaning, we can instruct the APIs to do something in the background and return data.
  - The setTimeout function is sent to the web API instead of the call stack.
  - After the function is done being sent to the Web API, it is then sent to the Callback Queue
  - Now matter how fast setTimeout wil execute, it still must be sent to the WebAPI, and then sent to the Callback queue.
  
  
