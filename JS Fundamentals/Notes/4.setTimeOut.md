
- it is a webApi provided by browser run time in js
- it goes in macro task queue
- macro task queue has lowest priority and runs at end after call stack is empty after executing microTask queue


```
for (var i = 0; i < 5; i++) {
  // var has global scope so one instance is shared accross
  setTimeout(() => {
    console.log(i);
  }, 0);
}

// use let will print 1 to 4 becuase let has block scope and new ref is created every time
```
  

```
function run(time) {
  if (time > 10) return;
  time += 1;
  setTimeout(() => {
    console.log(time);
    return run(time);
  }, time * 1000);
}

run(1);
```


tricky : 
```
// if want to print sequencely when still using var
for (var i = 0; i < 5; i++) {
  function close(i) {
    setTimeout(() => {
      console.log(i);
    }, i * 1000);
  }
  close(i); // every time new copy of i will created
}
```


