# Type Coercion

JavaScript is a weekly typed language, that means it allows writing code that merges values of different types in any way. So we can write something like `"string" + 1` and it will not complain, like in other strongly typed languages such as C# or Java. 

What JavaScript's just in time compiler does is, it tries to convert values to different types, based on operators and type of operands involved. In above scenario, it converts 1 to `'1'` so it can be appended with `string` to produce `string1` as a result. That implicit type coversion is called type coercion or conversion. 

## Some examples
```
console.log(3 * null); //0
console.log("6" - 1); //5
console.log("6" + 1); //61

console.log("five" * 2); //NaN
console.log(false == 0) //true

console.log(null == undefined); //true
console.log(null == 0); //false

console.log(true + false); //1
console.log(21 / "7"); //3
console.log("number" + 15 + 3); //number153
console.log(15 + 3 + "number"); //18number
console.log([1] > null); //true as > operator triggers [1] to numeric conversion i.e 1 > 0
console.log("foo" + + "bar"); //fooNaN as unary operator + has higher precedence "foo" + (+"bar") = "foo" + NaN = fooNaN
console.log('true' == true); //false as == operator triggers numeric conversion so 'true' becomes NaN
console.log(false == 'false'); //false as == operator turns 'false' to NaN, so false == NaN = false 
console.log(null == ''); //false as null does not get converted to numeric and null == '' is false
console.log(!!"false" == !!"true"); //true
console.log(['x'] == 'x'); //true
console.log([] + null + 1); //null1
console.log([1,2,3] == [1,2,3]); //false as arrays are two different instances and == check for object's identity not equality

//{}+[]+{}+[1]
//==> +[]+{}+[1]
//==> 0 + {} + [1]
//==> 0 + '[object Object]' + [1]
//==> '0[object Object]' + [1]
//==> '0[object Object]' + '1'
//==> '0[object Object]1'
console.log({}+[]+{}+[1]); //[object Object][object Object]1
console.log(!+[]+[]+![]); //truefalse
console.log(new Date(0) - 0); //0
console.log(new Date(0) + 0); //Thu Jan 01 1970 03:00:00 GMT+0300 (Standard Time)0
```