# Hoisting

## IIFE

Normally, variable declarations, are "hoisted" up to the top of whatever function they are declared in (or global if no function exists).  This can lead to some weird moments:

```JavaScript
var a = 2;

if(true){
    var a = 4;
}

console.log(a); //in many programming languages, this would be 2
```

and a famous interview question:

```JavaScript
for(var i=0; i<5; i++){
    setTimeout(function(){
        console.log(i) //you'd expect 0,1,2,3,4
    },500 * i);
}
```

IIFE - Immediately Invoked Function Expression - often used to create a block of scope. This is not an ES6 thing, but rather an example of an old way to get block scoping.

```JavaScript
var a = 2;

(function IIFE(){
    var a = 4;
    console.log ('Inside the IFFE, the value of a is', a ); //"Inside the IFFE, the value of a is 4"
})();

console.log ( 'Outside the IFFE, the value of a is', a ); //"Outside the IFFE, the value of a is 2"
```

And now the loop with setTimeout:

```JavaScript
for(var i=0; i<5; i++){
  (function(i){
    setTimeout(function(){
      console.log(i)
    },500 * i);
  })(i)
}
```

## Block Scoping with let

A new way to get block level scoping is with the keyword let, and the use of `{}` as in any `{}`, not just tied to a function! Note: `let` is NOT meant to completely replace `var`!

```JavaScript
var a = 2

{
    let a = 4
    console.log( 'the value of b inside the `{}` is', a); //"block level scope"
}

console.log ('the value of b outside of the `{}` is', a) //"global scope"
```

And now the loop with setTimeout:

```JavaScript
for(let i=0; i<5; i++){
    setTimeout(function(){
        console.log(i) //you'd expect 0,1,2,3,4
    },500 * i);
}

console.log(i); //notice i is not defined outside of the loop
```
