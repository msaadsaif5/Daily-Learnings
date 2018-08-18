# Overflow in Integral Types

Overflow can occur if an integral type is assigned a value that is outside the bounds of its maximum or minimum values. 
e.g. 
```
int firstValue = Int32.MaxValue; //2147483647
int secondValue = 5;
int result = firstValue + secondValue; // Outputs -2147483644, which is 5 less than min value of Int32, -2147483648
```
So by default, in an expression, C# compiler doesn't throw an exception if overflow occures, instead it gives the wrong result.

But we can run this code in `checked` context that will throw an Overflow exception if overflow occurs. The syntax is

```
checked {
    try {
    int firstValue = Int32.MaxValue; //2147483647
    int secondValue = 5;
    int result = firstValue + secondValue; // throws overflow exception
    }
    catch (System.OverflowException e) {
        Console.WriteLine("CHECKED and CAUGHT:  " + e.ToString());
    }
}
```

We can also run code under unchecked context using `unchecked` keyword, that will not throw overflow exception and will also prevent 
compiler errors in case of constant assignments e.g. 
```
unchecked {
    int result = 2147483647 + 10;
}
```