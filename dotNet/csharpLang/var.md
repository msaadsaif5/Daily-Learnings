# var keyword

Normally in a program, we specify type of a varaible by indicating its type i.e.,
* `int i` i is of type integer
* `string str` str is of type string
* `Person person` person is of type Person which is a user defined type, etc.

That is call explicit type. You are telling the compiler about what type of variable you are creating. But often times you do not want this, you want compiler to detect the type of variable for you. It is not exactly loose typing as can be done in many dynamically typed languages like JavaScript. It is more like a syntactic sugar and comes in handy with anonymous types in C#. 

Above variables can also be declared as below

* `var i = 10` i is of type integer which is detected by compiler
* `var str = "this is a string"` str is of type string detected by compiler
* `var person = new { Name = "Saad", Age = 99 };` person is of an anonymous type which is a user defined type, etc.

Note that we have to initialize at declaration time, because otherwise how would compiler know about type, as the only way it can infer the type is by the value of variable. 

Also note that, in case of anonymous type, you have no option other than using `var` and is not optional in this case. 

## Points to note:

* `var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.

* `var` cannot be used on fields at class scope.

* Variables declared by using var cannot be used in the initialization expression. In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`

* Multiple implicitly-typed variables cannot be initialized in the same statement.

* If a type named `var` is in scope, then the var keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.


