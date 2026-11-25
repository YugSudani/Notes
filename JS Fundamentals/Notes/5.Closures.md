Closure is the combination of inner function with access to its outer/lexical environment.

```
function outest() {
  let a = 1;
  return function outer() {
    let b = 10;
    return function inner() {
      console.log(a, b, c);
    };
  };
}
let c = 100;
// short way
outest()()();

// usual way
// let collection = outest();
// let nestedColl = collection();
// nestedColl();
```

Benefits : 

Eg. Data Hiding


```
function outest() {
  let ct = 0;

  this.increment = function () {
    ct++;
    console.log(ct);
  };

  this.decrement = function () {
    ct--;
    console.log(ct);
  };
}

let collection = new outest();
collection.increment();
collection.increment();
collection.decrement();
```


Disadvantage: 

- consumes more memory because until scrip ends garbage collector can not wipe out outer function variables from memory.
- **Garbage Collection (GC) in JavaScript** is an automatic memory management process that identifies and removes objects that are no longer reachable or needed by the program, freeing up memory.