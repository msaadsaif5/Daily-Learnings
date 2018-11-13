# stackalloc

`stackalloc` is a keyword in C# used to allocate memory block on to the stack. After the release of C# 7.2, `stackalloc` can be used in an unsafe context with `Span<T>`. `stackalloc` can only work with value types but not with the reference types. 

The main benefit of using stack memory instead on heap is performance, GC will not have to keep track of object to clean and your variables will be stored on system's cache. 

```
struct Point
{
    public int x;
    public int y;
}
...
Span<Point> s = stackalloc Point[5];
s[0].x = 1;
```

we can use stackalloc in unsafe code using pointers and we do not need to fix the instance as it is already fixed on stack

```
unsafe 
{
    int* array = stackalloc int[3] {1,2,3};
    *array = 23;
}
```
