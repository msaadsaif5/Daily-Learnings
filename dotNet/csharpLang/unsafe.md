# Unsafe keyword

In C#, the memory is managed by the CLR or garbage collector, so we do not have to deal with pointers. But it doesn't restrict users to do so. It provides a special `unsafe` keyword, that allow us to work with pointers inside unsafe context. Unsafe code has to be compiled with `/unsafe` switch and it is not verfied by the CLR

```
public class Test
{
    int i = 10;

    public unsafe int Run()
    {
        fixed (int* ip = &i)
        {
            Console.WriteLine($"address of i before updation: {((IntPtr)ip).ToString()}");
        }

        i = i + 1;

        fixed (int* ipNew = &i)
        {
            Console.WriteLine($"address of i before updation: {((IntPtr)ipNew).ToString()}");
        }

        return i;
    }
}
```
The above code uses unsage keyword in the method defintion to tell compiler that its going to use pointers inside of it. Here, the fixed statement is responsible to tell garbage collector to not move the memory location of our variable i.e. to pin it exactly on one location.
