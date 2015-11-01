#React tutorial beginners 

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

Lesson 3: Hello React!

Before you create any React component you need to get the library, you can download the latest and greatest version of react from the official Facebook g Github page [here](https://facebook.github.io/react/downloads.html) and then you will have a folder that contains several files.

As of the time of this writing (11/2015), you will see two files and a read me file. One folder contains the react minified and non minified versions and the other folder contains some cool examples written in react. 

If you like using JSX, Babel provides an in-browser ES6 and JSX transformer for development called browser.js that can be included from a babel-core npm release or fromCDNJS. Include a <script type="text/babel"> tag to engage the JSX transformer.

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


    <style>
      img {
        width: 150px; 
      }
    </style>
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



 
