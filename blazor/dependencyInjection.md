# Dependency Injection in Blazor

Blazor provides DI out of the box. Services can be registered in `ConfigureServices(IServiceCollection services)` method in two  lifetime modes only.
* Transient - New instance whenever required
* Singleton - Single instance throughout the app

Blazor also provides `Scoped` lifetimes but they currently behave as `Signleton` so `Singleton` should be used instead. 

## Default Services

Blazor provide `IUriHelper` and `HttpClient` services using its `BrowserServiceProvider` which helps in working with app URIs, navigation and HTTP request/response. 

## Service in a Component
Service can be injected in a component by using `@inject` keyword

## Example

```csharp
public interface IOrderService {...}
public class OrderService : IOrderService {...}

..
//startup.cs
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton<IOrderService, OrderService>();
}
...

//component
@page "/orders"
@inject IOrederService orderService

```

The services can also be used in other C# classes in the app as regular DI works. 
