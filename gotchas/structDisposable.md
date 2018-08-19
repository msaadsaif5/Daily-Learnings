# Structs and IDisposable

Structs are value types that means their value gets copied each time it is passed to other variables or as method arguments.
If a struct happens to contain a reference type such as a list then that obviously will created on the heap, and pointer will be 
stored in the struct. 
Now if we implement IDisposable on this struct that disposes this reference type i.e. list. Then any copy of struct can call the dispose or it will
be automatically called by GC. In this case, the other copies will be referencing to null as the list in the heap has been disposed. 

In general, struts and mutability does not play nicely together and should be avoided. A class should be preferred choice if reference types are required. 