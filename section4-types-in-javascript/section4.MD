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
  
