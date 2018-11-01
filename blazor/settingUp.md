# What is Blazor?

Blazor is an open source, full stack .NET web framework that uses C#.NET in browser as well as in the backend. It runs on WebAssembly that provides native performance in the browser. 

## Setting up on Mac OS
At this time, the pre-requisites are only .NET Core 2.1 SDK (2.1.402 or later) and a Blazor template that can be installed using command line. 

`dotnet new -i Microsoft.AspNetCore.Blazor.Templates`

and run the following commands to create your first demo application on Blazor

```
dotnet new blazor -o BlazorApp1
cd BlazorApp1
dotnet run
```