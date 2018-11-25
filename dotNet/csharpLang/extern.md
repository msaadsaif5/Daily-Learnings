# extern Modifier
 
The `extern` modifier is used to refer to a method that is implemented in external/unmanaged assemblies. In a .Net program, we can add references to other managed assemblies but if we have an assembly that does not have a managed code then that cannot be refered inside your .Net program.

To call a method implemented in unmanaged code, we have to do the following
* Declare a `static` `extern` method with same name, arguments and return value as in the unmanaged code
* Add `DllImport` attribute on top of this method declaration
* Make unmanaged assembly accessible to the running managed code
* Call the method declaration that will call unmanaged mathod behind the scenes for you

## Example
Below code can be used to issue calls to `MessageBox` method of unmanaged Win32 dll  
```
[DllImport("User32.dll", CharSet = CharSet.Unicode)]
        public static extern int MessageBox(IntPtr h, string m, string c, int type);

        public static void First()
        {
            string myString;
            Console.Write("Enter your message: ");
            myString = Console.ReadLine();
            MessageBox((IntPtr)0, myString, "My Message Box", 0);
        }
```
