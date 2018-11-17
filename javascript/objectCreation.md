# Objects Creation in JavaScript

How can we create objects in JavaScript? well there are multiple ways. 

## Object Literal
```
var Dog = {
    name: 'Tom',
    age: 12,
    color: 'white',
    toString: function(){
        return `${this.name}, the dog, has ${this.color} color and is ${this.age}`;
    }
}

//prints the json version of Dog object
console.log(JSON.stringify(Dog));
```
To access the properties, we can use the dot operator `Dog.age` or bracket notation `Dog["age"]`


## Object Constructor
Object constructor are equivalent to creating classes in C# or Java etc. We create an object with a function name that acts as a constructor to create the object. 

```
function Doggy(name, age, color){
    this.name = name;
    this.age = age;
    this.color = color;
    this.toString = function(){
        return `${this.name}, the dog, has ${this.color} color and is ${this.age}`;
    }
}

var doggy = new Doggy("Tom", 5, "Brown");
console.log(doggy);
```

we can do further operations on objects like, add a new property
```
Dog.weight = 30;
```
or delete existing one
```
delete Dog.age;
```
