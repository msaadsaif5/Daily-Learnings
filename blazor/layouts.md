# Layouts
 Layouts are simple `.cshtml` razor files that define the base template of the page, such as menu items, copyright messages or logos etc. As the app may consist of more pages, a unified layout is the best way to write common logic at one place. 

 Blazor supports nested layouts so that we can define layout within a layout and so on. 

 To write a layout, create a `.cshtml` file and inherit it from `BlazorLayoutComponent` and define `@Body` where you want your components to be rendered. In the component razor view, we use
 `@layout layoutName` to set its layout. 

 ## Example

`MainLayout.cshtml`
 ```
 @inherits BlazorLayoutComponent

<header>
    <h1>Welcome to Blazor</h1>
</header>

<nav>
    <a href="master-data">Introduction</a>
    <a href="invoicing">Layouts</a>
    <a href="accounting">Components</a>
</nav>

@Body

<footer>
    &copy; by @CopyrightMessage
</footer>

@functions {
    public string CopyrightMessage { get; set; }
    ...
}
```

and to use a layout in a component such as in `HomeComponent.cshtml` 

```
@layout MainLayout

@page "/home"

<h2>Home</h2>
...
```