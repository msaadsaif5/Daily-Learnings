# Loops in JavaScript

JavaScript has the following kinds of loops
* `for in`
* `for of`
* `while`
* `do while`
* `for`

## Sample Code

```
whileLoop();
forLoop();
forInLoop();
forOfLoop();

function forInLoop() {
  var txt = "";
  var persons = [
    { fname: "John", lname: "Doe", age: 25 },
    { fname: "John", lname: "Doe", age: 25 }
  ];
  for (var i in persons) { //iterats over indexes
    var person = persons[i];
    for (var property in person) {
      txt += person[property] + " ";
    }
  }
  console.log(txt);
}

function forOfLoop(){
    var txt = "";
    var persons = [
      { fname: "John", lname: "Doe", age: 25 },
      { fname: "John", lname: "Doe", age: 25 }
    ];
    for (var person of persons) { //iterates over index values    
      for (var property in person) {
        txt += person[property] + " ";
      }
    }
    console.log(txt);
}

function forLoop() {
  var input = 5;
  for (var i = 0; i < 10; i++) {
    input += i;
  }
  console.log(input);
}

function whileLoop() {
  var input = "This is a long string to find character z inside of it";
  var found = false;
  var index = 0;
  while (!found) {
    if (input[index] == "z") found = true;
    else index++;
  }
  console.log(`z was found at index ${index}`);
}


```
