# Explicit Implementation of Interfaces

C# allows to implement interfaces either implicitly or explicitlty. If done implicitly, the methods of interface are public and can be accessed through implementers instance i.e. the `Print` method of `IPrintable` interface below can be accessed from `Report`'s instance. 

```
  class Report : IPrintable<Report>, IDownloadable
    {
        public int Id { get; set; }
        public string Title { get; set; }
        public DateTimeOffset GeneratedOn { get; set; }

        //implicit implementation
        public void Print(Report obj)
        {
            Console.WriteLine($"Report with title '{Title}' was generated on {GeneratedOn}");
        }

        //explicit implementation
        void IDownloadable.Download(string path, string format)
        {
            //download logic here
        }
    }
```

However, explicitly implemented methods cannot be public and in this case, can only be accessed through `IDownloadable` instance as shown in below code.

```
var report = new Report { Id = 1, Title = "MyReport", GeneratedOn = DateTimeOffset.Now };
report.Print(report);

//Download method is not accessible as Reprot class implements the IDownloadable interface explicitly
//report.Download(@"C:\", "pdf");

//can access after casting to IDownloadable interface
((IDownloadable)report).Download(@"C:\", "pdf");
```

## Use Cases of explicit implementation
* If you have same method signatures in multiple interfaces then you will be able to differentiate among them and call the appropriate implementation only. 
* If you want to hide a method from the class object instance unless the user casts the instance to appropriate interface first. 

