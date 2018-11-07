# Blazor Components

Blazor apps are built using components. A component is a self-contained chunk of user interface (UI), such as a page, dialog, or form. A component includes both the HTML markup to render along with the processing logic needed to inject data or respond to UI events. Components are flexible and lightweight, and they can be nested, reused, and shared between projects.

Component uses HTML and CSS to build UI. Dynamic rednering logic is added using C# Razor syntax. C# is used inside funtion tag for data fetching storing logic.

After initial rendering, Components regenerates their render tree upon events and callbacks to apply changes to browser's DOM

Once dclared, they can be using in tags similar to HTML, for example following component `hello.cshtml`

```
<h1> Hello @Name </h1>

@functions{
    string Name {get; set:}
}
```
can be used as `<hello />` inside any other component or `.cshtml` class. 