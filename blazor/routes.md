# Routing 

Blazor provides routing capabilities by using the `@page` directive on top of the component. The syntax is simple

`@page "yourRoute"`

We can also provide multiple page directives and that component will get hit by all specified routes. 

## Passing parameters thorugh route

We can specify parameter through route simply by adding the case insensitive name of component's parameter inside curly braces, in the route

`@page "/people/{name}"`

where `name` is a component parameter defined as 

```
@functions
{
[Parameter] 
string Name {get; set; } = "Saad"
}
```
## Route Constraints

We can also specify constraints on a route. For example 
`@page "/people/{id:int}` specifies that `id` should only be an `int`. All basic constraints can be applied using the same format. 