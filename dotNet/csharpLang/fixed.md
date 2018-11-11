# Fixed statements

Garbage collector can relocate variables unpredictably during the execution of a program. If we were to write unsafe code i.e. accessing varaibles using their addresses through pointers, then we do not require that relocating behavior as our pointers could point to garbage data, if the variable under the hood is relocated or garbage collected. 

The solution to this problem is `fixed statements`. Fixed statements can be used to tell GC to not relocate or move the variable if it is inside the fixed statement.

Pointers and Fixed statements can only be used inside `unsafe` code. 

```
string s = "some string";
unsafe
{
    //char* p = s; //not allowed

    fixed (char* sp = s) //works after fixing string in memory
    {
        //sp++; //invalid as sp is scoped in fixed statement and is readonly

        char* spCopy = sp;
        spCopy++; //works

    }
}
```

In case of a custom implementaion such as a class, we can pin down its fields that would also pin its instance. 

```
class RandomData
{
    public int _size;
    public string Value { get; set; }
}

unsafe
{
    RandomData data = new RandomData() { _size = 1, Value = "some value" };

    fixed (int* ip = &data._size) //data instance variable is now pinned
    {

    }
}
```
