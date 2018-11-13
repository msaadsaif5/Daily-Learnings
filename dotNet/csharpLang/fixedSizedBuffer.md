# Fixed Size Buffer

Last time I learned about [Fixed Statements](fixed.md) and how it is used to pin some data structure on to memory. 

What if we have some sort of data structure that needs to hold off to a fixed length block of memory and that in being interoped with some other languages or frameworks, so we need it to be pinned in memory. 

Normally when we create an array inside a data structure. 

```
struct Buffer
{
    public int size;
    public byte[] data;
}
```
 It stores the address of data in struct and rest of the data in heap. 

 To create a fixed sized buffer in struct, we can do something like below:

```
unsafe struct BufferInterop
{
    public int size;
    public fixed byte data[128];
}
```
Above struct will hold byte data of a fixed size memory, that will also be pinned down so GC cannot collect it.

The unsafe struct will only be accessed through unsafe context. 

Unsafe buffers differ from regular arrays in the following ways:

* You can only use unsafe buffers in an unsafe context.
* Unsafe buffers are always vectors, or one-dimensional arrays.
* The declaration of the array should include a count, such as char id[8]. You cannot use char id[].
* Unsafe buffers can only be instance fields of structs in an unsafe context.
* Unsafe buffers takes more memory space than usual i.e., a bool is of 1 byte and a character is of 2 bytes. 

