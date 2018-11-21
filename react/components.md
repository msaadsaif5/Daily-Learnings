# React Components

React has powerful concept of components that can be modeled as per application model. Components are suitable when you have a common UI that needs to repeated or if you want to make it reusable, such as panels, login forms etc. Components behave much like JavaScript functions and accept `props` which is shorthand for properties, to allow them take input from their parent elements. 

Components are of two types
* Function Components
* Class Components

## Function Components
They are literlly javaScript functions that takes `props` and reuturn `JSX`, which is syntax extension to JavaScript and can blend HTML and JavaScript.
```
function UserInfo(props){
    return ( <h1>{props.name}</h1>
            <div className='UserJoining'>{props.joiningDate}</div> );
}
```
So every function that accepts a single `props` argument and return a React element is a valid React funtion component. 

## Class Components
We can create React components using ES6 classes in javaScript. The above function component can be written in class component as
```
class UserInfo extends React.Component{
    render(){
        return ( <h1>{this.props.name}</h1>
            <div className='UserJoining'>{this.props.joiningDate}</div> );
    }
}
```
Note that we user `this` keyword to refer to the `props` for this component. Above two components are same from React point of view. 

## Rendering Components
Now that we have created our components, we can easily, render it on ReactDOM that then takes care of rendering it on browser's DOM. 
```
ReactDOM.render(){
    <UserInfo name='saad' joiningDate='12-12-2000'/>,
    document.getElementById('root')
};
```
we can also assign our component to a React element and pass that to render method

```
const element = <UserInfo name='saad' joiningDate='12-12-2000'/>;
ReactDOM.render(){
    element,
    document.getElementById('root')
};
```

You may be wondering, how the `name` and `joiningDate` are converted to `props` in the component? Well, React converts all attributes to a single parameter in the `props` variable so that its easier to write components with just one argument. `props` are also readonly so the passed values cannot be modified from inside the components, which provides safety that your passed arguments won't be changed inside the component.

