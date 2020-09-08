### JavaScript Types
  - Types in JavaScript are: number, boolean, string, undefined, null, Symbol('just me') -> ES6, objects

### Array.isArray()
  - We can use the 'isArray()' function to check if something is an array.
  ```
    var array = [1,2,3];
    
    // same as
    
    var array = {
      0: 1,
      1: 2,
      2: 3
    }
  ```

### Pass By Value vs Pass By Reference
  - 'Primitive' types are immutable.
  - When we are passing by value, we are copying a value and creating it somewhere else in memory. 
  - When we are passing by reference, we have objects point to the same location in memory.
  - If we want to clone an object properly without 'pass by reference' we can use this code:
  
  ```
    let obj = {a: 'a', b: 'b', c: 'c'};
    
    // we can clone 'obj' using the following code
    let clone = Obj.assign({}, obj};
    let clone2 = {...obj} // this is much cleaner
    
    // A better way to clone at a deeper level
    let superClone = JSON.parse(JSON.stringify(obj));
  ```
  
### Exercise: Compare Objects
  - How would you compare two objects if they are pointing to a different location in memory but still have the same properties?

### Exercise: Pass By Reference 
  ```
    const number = 100
    const string = "Jay"
    let obj1 = {
      value: "a"
    }
    let obj2 = {
      value: "b"
    }
    let obj3 = obj2;

    function change(number, string, obj1, obj2) {
        number = number * 10;
        string = "Pete";
        obj1 = obj2;
        obj2.value = "c";
    }

    change(number, string, obj1, obj2);

    //Guess the outputs here before you run the code: 
    console.log(number); 
    console.log(string);
    console.log(obj1.value);
  ```
  Solution:
  ```
    100
    Jay
    a
  ```
  - The values are being passed inside the function and a new space in memory is being allocated but not reassigned to the original global value. The global values stay the same.

### Type Coercion
  - 'Type Coercion' the language converting a certain type to another type
  - Do all languages have type coercion? - Yes.
  ```
    1 === '1'
  ```
