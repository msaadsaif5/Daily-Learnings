# CSS Pseudo-elements

Pseudo element is used to style part of an element or to insert content before/after the content of an element. This way, you can define the style related common content in the CSS rather than the HTML

For example, if you have to use an overlay on any element, you would typically define a `div` inside HTML element but by using pseudo element in CSS we can define it like below:
```
    body#bg-img:after {
      content: '';
      position: absolute;
      top: 0;
      right: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      background: rgba(68, 68, 68, 0.7); 
      }
```
The "after" is a pseudo element that will insert the specified content after body element that has id `bg-img`. Content in this case is empty as we are just setting background overlay, but it could be an image or anything else. 

We can also use pseudo element to style the portion of element that is selected by user e.g. selected text inside `p` element like below:

```
::selection {
    color: red;
    background: yellow;
}
```