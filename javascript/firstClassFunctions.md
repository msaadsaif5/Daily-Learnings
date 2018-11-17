# First Class Functions

In programming languages, there is a concept of first class and second class citizens. A first class citizen is one that can be passed as argument, can be returned from a function, can be modified and assigned to a variable. Some first class citizens include, a type, object, entity or value.  

In languages such as C, a function is a second class citizen. But JavasSript supports passing functions as arguments to other functions, returning them as the values from the other functions, and assigning them to variables or storing them in data structures and hence are first class citizens. 

### Assigning function to variable

```
const hello = function() {
   console.log("hello world");
}
// Invoke it using the variable
hello();
```

### Pass functions as an argument
```
function sayHello() {
   return "Hello, ";
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name);
}
// Pass `sayHello` as an argument to `greeting` function
greeting(sayHello, "JavaScript!");
```

### Return a Function
```
function sayHello() {
   return function() {
      console.log("Hello!");
   }
}
```
A function that returns a function is called Higher-Order Function. Inner function can be invoked as 

```
const myFunc = sayHello();
myFunc();
```
or by using double paranthesis as
`sayHello()();`

