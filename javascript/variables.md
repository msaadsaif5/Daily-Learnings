# Variables in JavaScript

In JavaScript, we can declare variables in three ways 

* Using `var` keyword
* Using `let` keyword
* Using `const` keyword

`const` is as the name expresses, contains only the value that must be provided to it during declaration.

`var` can have different values. Once declared inside a function, it is available to whole function body, does not matter if it is declared after usage in the function as it will come on top anyway as called variable hoisting. Remeber that even if we can use a variable due to hoisting process, its inititalization occurs when its initialization statement runs, so we can get undefined variables if we use them before initialization.

Variables created using `let` keyword have block scopes. A block can be curly braces and their child blocks for example `if` block etc. `let` variables do not get hoisted to the top and raises exception when used before declaration. 

## Example
```
var a;
var b;
let c;
const d = 30; //initilization is must with declaration

initialize();
first();
second();
third();

function initialize(){
     a = 10;
     b = 20;
     c = 30;
    console.log('initialized');
}

function first(){

    var local = 45; //visible everywhere inside this function's code

    console.log(`value of global variable a outside blocked scope but inside first function scope is ${a}`);
    console.log(`value of local variable outside blocked scope but inside first function scope is ${local}`);
    
    if (true){
        local = 44;
        a = 9;
        console.log(`value of a inside blocked scope after updation is ${a}`);
        console.log(`value of local inside blocked scope after updation is ${local}`);
    }

    console.log(`value of a outside blocked scope but inside first function scope, after updation is ${a}`);
    console.log(`value of local outside blocked scope but inside first function scope, after updation is ${local}`);
}

function second(){
    console.log(`value of global variable a outside blocked scope but inside first function scope is ${a}`);

    //using local here will raise exception
    
    if (true){
        let local = 44;
        a = 9;
        console.log(`value of a inside blocked scope after updation is ${a}`);
        console.log(`value of local inside blocked scope after updation is ${local}`);
    }

    console.log(`value of a outside blocked scope but inside first function scope, after updation is ${a}`);
    //using local here will raise exception
}

function third(){
    c = 32;
    //d = 23; //invalid as d is constant
    
    console.log(`value of c after updation is ${c}`);
    console.log(`value of d is ${d}`);    
}
```