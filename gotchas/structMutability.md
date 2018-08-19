# Structs and Mutability

Structs are value types that means their value gets copied each time it is passed to other variables or as method arguments.
If a struct happens to contain a reference type such as a list then that obviously will be created on the heap, and pointer value will be 
stored in the struct. 
Now if we implement `IDisposable` on this struct that disposes this reference type i.e. list. Then any copy of struct can call the dispose or it will
be automatically called by GC once that particular copy goes out of scope. If disposed was called on a copy of original struct then we have not actaully disposed the list, instead we have just set the value of list pointer copy to `null`.
If we were to actually dispose the list, then we must call the dispose method on original struct instance.

In general, structs and mutability does not play nicely together and should be avoided as there can be mutiple copies of struct and muting one will not apply the change to other copies. Idempotent interfaces, such as `IComparable` and `IEquatable`, however, can be implemeneted as they do not mutate the object in any way.