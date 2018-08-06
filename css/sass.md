# Syntactically Awesome StyleSheets (SASS)

Sass is a prepocessor that allow us to use features that do not exist in CSS yet like variables, mixins, inheritance and other.
Sass processes the .scss files and generates .css files that are used in web applications.

## Basics

1. Define variable starting with `$` i.e. `$primary-color: #333;`
2.  Nest CSS selectors
```
nav {
    ul {
    margin: 0;
    padding: 0;
}

    li { display: inline-block; }
}
```
Geenrated CSS will get something like this:
```
nav ul {
    margin: 0;
    padding: 0;
}

nav li { display: inline-block; }
```
3.  Create partial files by prepending underscore in the file name like `_partial.scss` and import partial files using `@import = 'partial'`
4.  Inherit properties of one selector from another and avoid repeating yourself. In below code example, `.success` and `.error` both will get shared properties in generated CSS
    
```
// This CSS will print because %message-shared is extended.
%message-shared {
    border: 1px solid #ccc;
    padding: 10px;
    color: #333;
}

.success {
    @extend %message-shared;
    border-color: green;
}

.error {
    @extend %message-shared;
    border-color: red;
}
```

5.  Do math in CSS with basic operators like +,-,\*,/ and %
