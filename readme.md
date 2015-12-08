#React Tutorial Beginners 

##Lesson 1: What is React? 

React is simply a JavaScript library whose single purpose is to help you build large applications with data that changes over time. In a nutshell, React is simply the V in the Model View Controller architecture (MVC). As such, it is difficult to compare it to other frameworks like Angular. When building apps in React you build things one a time using components. React was built by Facebook and released in early 2013, there is also React Native, which uses React, to create native iOs and Android apps. But React is only for web browsers in the front end.  

##Lesson 2:  What is JSX? 

This is a JavaScript syntax that lets you write HTML inside your JavaScript. I know that might sound a little off, HTML inside a JavaScript?! According to Facebook, you don't have to use JSX with React but they highly recommend that you do since it is a concise and familiar syntax for defining tree like structures. You can read more about JSX [here](https://facebook.github.io/react/docs/jsx-in-depth.html) on the facebook API docs.  The browsers don’t recognise JSX files, JSX files get compiled to JavaScript that are then passed to the `React.createElement` function. 

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

In React it is easier to write code in JSX than writing it in Vanilla JS, espcially when you start to nest more html elements - the function call in the vanilla js example will get more complex. 

JSX is an extension of javascript that lets us write what looks like HTML alongside our javascript
JSX must first be complied from jsx to javascript so that the browser can understand what's going on.
We use JSX because it's a lot more clear and concise about the HTML structure and React components than the equivalent Javascript.  

##Lesson 3: Hello React!

Before you create any React component you need to get the library, you can download the latest and greatest version of react from the official Facebook g Github page [here](https://facebook.github.io/react/downloads.html) and then you will have a folder that contains several files.

As of the time of this writing (Nov 2015), you will see two files and a read me file. One folder contains the react minified and non minified versions and the other folder contains some cool examples written in react. 

To quickly get started writing react apps, you will need to have a browser side jsx converter and if you also want to write ES6 then you can use browser.js, which is provided by Babel that will transform your jsx code into js and also transpile ES6 into ES5 for browsers that don't yet fully support ES6. For the purposes of this tutorial, we will include browser.js via a CDN and include it in our HTML file. 

Here is our boiler plate code for writing a simple Hello React! To the screen. 

```javascript 

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>React Tutorial</title>
    <!-- Not present in the tutorial. Just for basic styling. -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" integrity="sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.0/react.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.0/react-dom.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.6.15/browser.js"></script>
  </head>
  <body>
    <div class="container">
      <div class="row">
        <div id="content">
          
        </div>
      </div>
    </div>
    
    
    <script type="text/babel">

      var Hello = React.createClass({
      render: function(){
            return (
      
                <h1>Hello React!</h1>

              )
          }
        });


      ReactDOM.render(
        <Hello />,
        document.getElementById('content')
      );

    </script>
  </body>
</html>


```

##Lesson 4: Props

Now that we know how to render content to the page, we want to be able to provide some data that can be used by the component. The simple Hello React example we created is just a static component. We're going to expand our Hello React example and this time we will provide some data that can be used by the component.

Since we already have the Bootstrap framework in our boiler plate code, we will use the badge component. So I'm just going to copy the HTML code along with classes. Here's how our code will look like: 

``` javascript 

var Badge = React.createClass({
    render: function() {
      return <button class="btn btn-primary" type="button">
        Messages <span class="badge">4</span>
      </button>
    }
  });

ReactDOM.render(
        <Badge />,
        document.getElementById('content')
      );

```

When creating React components the converntion is to make the first letter of the name of the component upper case,  this is not required but it is general convention used by React developers. When you load up the file in the browser, you will find that the CSS styling is not being applied. This is one of the many 'Gotchas' you will come across when using React for the first time. You probably got an error in the form `Unkown DM property class. Did you mean className?`. As you know, class is a reserved keyword in JavaScript and in JSX, class refers to a component, and as such, you can not use it inside your JSX file. Whenever you are working with DOM elements instead of using class to apply CSS class names, you have to use className for your styling to be be applied.  

Here is our updated code with the correcy usage of class in JSX files as className: 

``` javascript 

var Badge = React.createClass({
    render: function() {
      return <button className="btn btn-primary" type="button">
        Messages <span className="badge">4</span>
      </button>
    }
  });

ReactDOM.render(
        <Badge />,
        document.getElementById('content')
      );

```

Right, this lesson was all about props, so let's cut to the chase. First of all what are props? Props in React is simply an object that a component has access to. The data inside this object is passed to the component when the component is rendered. This will make more sense when we write it in code. So, the first step in our example is to create an options object, this object will be passed in when we render the component. 



``` javascript 

var options = {
  
title: 'Inbox',
number: '19'
  
}

```

Now, in the next step I'm going to replace the hard coded string 'Messages' with this.props.options.title and the number with this.props.options.number: 

``` javascript 

var Badge = React.createClass({
    render: function() {
      return <button className="btn btn-primary" type="button">
        {this.props.options.title} <span className="badge">{this.props.options.title}</span>
      </button>
    }
  });

ReactDOM.render(
        <Badge />,
        document.getElementById('content')
      );


```

A quick explanation on what is happening here: in the first step we created an object called options, this object has two keys a title key and a number key. Then we replaced the hard coded 'Message' string and number with `{this.props.options.title}` note the use of the curly braces, this is important as it tells React that this is JavaScript code that needs to be executed. Every component in React is an object, and just like you have access to the Window and the 'this' keyword in the DOM, every React component is given an empty props object. Whenever you create a component and then render that component using React's render method you have the option to attach data to the empty props object that can be used inside the component via `{this.props}`. Now for the last step, we have to pass the options object when the component is rendered: 

```javascript 

ReactDOM.render(
        <Badge options=options/>,
        document.getElementById('content')
      );

```

Here we are simply naming the object that will be attached to the props object as options and passing in our options object that we created earlier. Here is the code altogether so far: 

``` javascript 

var Badge = React.createClass({
    render: function() {
      return <button className="btn btn-primary" type="button">
        {this.props.options.title} <span className="badge">{this.props.options.number}</span>
      </button>
    }
  });

ReactDOM.render(
        <Badge options=options/>,
        document.getElementById('content')
      );

```

When you click on save and refresh your screen you should see the button update with our title from the options object that is attached to props, likewise the number should also change to 19. So there you have it! You have now learned what props are in React. In the next lesson we will create a composition of components, in other words, we will create views within views. 

##Lesson 5: Views within views

In react you can nest components inside other components. Just like you have child elements inside a Div, you can create a component and that component will also render other components. Remember, these components are just elements, so you can have a component that just returns a li element, for example. 

In lesson 3 we created a simple React component that rendered a h1 element on the screen. We will nest this component inside another component. First, let's create a component that will return a p element with a some description text: 

``` javascript 

var Description = React.createClass({
  render: function(){
    return (
      <p>React is simply a JavaScript library whose single purpose is to help you build large applications with data that changes over time. In a nutshell, React is simply the V in the Model View Controller architecture (MVC)
      </p>   
      );
    }
  });

```

The Description component returns a p element with description text, this component will be returned as nested component inside a container component, which we will now create: 

``` javascript 

var Container = React.createClass({
  render: function(){
    return (
      <div>
        <Hello />
        <Description /> 
      </div>
      );
    }
  });
```
This component will act as a container for the two other components, so this component returns a div whose children are two other components, the Hello component and the Description component. Note the use of the self closing tag, this is important otherwise React will throw an error. 

Next we need to render the Container component instead of the Hello component that we were rendering before: 

```javascript 
  ReactDOM.render(
    <Container />,
    document.getElementById('content')
    );
```

When the Container component is rendered by React it contains other nested components inside, so React will also render the nested components and return them as individual elements on the page. Here is the code altogether: 

```javascript 
var Hello = React.createClass({
   render: function(){
    return (
      <h1 className="text-center">Hello React!</h1>
      );
    }
  });

var Description = React.createClass({
    render: function(){
      return (
        <p>React is simply a JavaScript library whose single purpose is to help you build large applications with data that changes over time. In a nutshell, React is simply the V in the Model View Controller architecture (MVC)
        </p>   
      );
    }
  });

var Container = React.createClass({
  render: function(){
    return (
      <div>
        <Hello />
        <Description /> 
      </div>
      );
    }
  });


ReactDOM.render(
  <Container />,
    document.getElementById('content')
  );
```
