# Implicit and Explicit Type conversions

We can add type conversion logic in user defined types by using keywords like `implicit` and `explicit`. 

Implicit conversion
Consider the following class
```
    public class Number
    {
        public int myInt {get; private set;}
        
        public Number(int i)
        {
            myInt = i;
        }

        public static implicit operator int(Number d){
            return d.myInt;
        }

        public static explicit operator Number(int i){
            return new Number(i);
        }
    }
```
I've defined two conversion operators, one is implicit and the other as explicit. Notic that whatever is in the argument is source and return value is the output.

So following code now works

```
    class Program
    {
        static void Main(string[] args)
        {
            var d = new Number(45);
            int myInt = d; //implicit conversion
            d = (Number)40; //explicit conversion
            Console.WriteLine($"myInt = {myInt}, d = {d.myInt}");
            Console.ReadLine();
        }
    }
```
