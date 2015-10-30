#React tutorial beginners 

##Lesson 1: What is React? 

React is simply a JavaScript library whose single purpose is to help you build large applications with data that changes over time. In a nutshell, React is simply the V in the Model View Controller architecture (MVC). As such, it is difficult to compare it to other frameworks like Angular. When building apps in React you build things one a time using components. React was built by Facebook and released in early 2013, there is also React Native, which uses React, to create native iOs and Android apps. But React is only for web browsers in the front end.  

##Lesson 2:  What is JSX? 

This is a JavaScript syntax that lets you write HTML inside your JavaScript. I know that might sound a little off, HTML inside a JavaScript?! According to Facebook, you don't have to use JSX with React but they highly recommend that you do since it is a concise and familiar syntax for defining tree like structures. You can read more about JSX [here](https://facebook.github.io/react/docs/jsx-in-depth.html) on the facebook API docs.  The browsers don’t recognise a JSX files, JSX files get compiledto JavaScript that are then passed to the React.createElement function. 

####JSX syntax 

```javascript 
{
  render: function() {
    return <div>Hello World!</div>
      
  }
}
```
This compiles to JavaScript

```javascript 
{
  render: function() {
   return React.createElement('div', null, 'Hello World!');
  }
}
```

In React it is easier to write code in JSX than writing it in Vanilla JS,espcially when you start to nest more html elements - the function call in the vanilla js example will get more complex. 

JSX is an extension of javascript that lets us write what looks like HTML alongside our javascript
JSX must first be complied from jsx to javascript so that the browser canunderstand what's going on
We use JSX because it's a lot more clear and concise about the HTML structure and React components than the equivalent Javascript.  

Lesson 3: coming soon 



 
