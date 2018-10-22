# Weak Reference
Normally, when a type contains any other type, it creates a strong reference that doesn't get garbage collected, until its out of scope. However, We can also create weak reference of an object, which does not stop garbage collector to claim the object. In that case, the refered object is only available only until it is garbage collected and has to be recreated if reclaimed by the garbage collector.

Weak references are useful for objects that consume a lot of memory but can be easily recreated if reclaimed by the GC. 

Following Cache class creates weak referneces of cached objects and recreastes them if accessed after garbage collection.

```
public class Cache
{
    // Dictionary to contain the cache.
    static Dictionary<int, WeakReference> _cache;

    // Track the number of times an object is regenerated.
    int regenCount = 0;

    public Cache(int count)
    {
        _cache = new Dictionary<int, WeakReference>();

        // Add objects with a short weak reference to the cache.
        for (int i = 0; i < count; i++)
        {
            _cache.Add(i, new WeakReference(new Data(i), false));
        }
    }

    // Number of items in the cache.
    public int Count
    {
        get { return _cache.Count; }
    }

    // Number of times an object needs to be regenerated.
    public int RegenerationCount
    {
        get { return regenCount; }
    }

    // Retrieve a data object from the cache.
    public Data this[int index]
    {
        get
        {
            Data d = _cache[index].Target as Data;
            if (d == null)
            {
                // If the object was reclaimed, generate a new one.
                Console.WriteLine("Regenerate object at {0}: Yes", index);
                d = new Data(index);
                _cache[index].Target = d;
                regenCount++;
            }
            else
            {
                // Object was obtained with the weak reference.
                Console.WriteLine("Regenerate object at {0}: No", index);
            }

            return d;
        }
    }
}
```
