# Boxing & Unboxing in CSharp

## Boxing
Let a value type `int i = 555` allocated in the stack memory. If that value type is assigned to an `object` i.e. `object o = i;` then we have successfully boxed `i` in the heap memory as `object o`. Behind the scenes, it has created an object instance on the heap and copied the value into the new object. Note that this value is a copy of the `value-type` value assigned to the variable i. Boxing is an implicit conversion but can also be done explicitly like `object o = (object)i;`

## Unboxing

Unboxing is an explicit conversion of an object to a value type. Unboxing is done after verfying the boxed object type as it should match with the type it is being unboxed to. Following statements demonstrate both boxing and unboxing operations.

```
int i = 555;      // a value type 
object o = i;     // boxing 
int j = (int)o;   // unboxing
```

Attempting to unbox a reference to an incompatible value type causes an `InvalidCastException`.

