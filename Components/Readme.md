# ReactJS : [1] - The Components

__Components__ _are building blocks of all ReactJS applicatios and most of the ReactJS apps are made up of by combining different components._

### Defining ReactJS Component

_A_ __Component__ _in ReactJS is an entity which is capable of_ __rendering__ _something on the screen, always or on demand_

_That's the precise reason why each and every_ __Component__ _is having a single_ __render()__ _function_.

## 1.1 - Hello World ReactJS HTML

_The first step to getting ReactJS up and running is to get a Hello World HTML from_ [here](https://facebook.github.io/react/docs/installation.html)

_The HTML file will have following contents_

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello World</title>
    <script src="https://unpkg.com/react@latest/dist/react.js"></script>
    <script src="https://unpkg.com/react-dom@latest/dist/react-dom.js"></script>
    <script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
  </head>
  <body>
    <div id="root"></div>
    <script type="text/babel">

      ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('root')
      );
    </script>
  </body>
</html>

```
_For our own understanding of ReactJS, We'll change the contents inside_
```
<script type="text/babel">

```
_The_ __babel__ _is a_ __Transpiler__ _which converts the_ __JSX__ _code into plain_ __JavaScript__ _code, so that it can be interpreted by JavaScript Engine of the Browser_

## 1.2 - Understanding ReactDOM

__ReactDOM__ _is react representation of HTML DOM which put the contents into the HTML DOM albeit smartly. Many a times it doesn't redraw complete DOM but a subset to make it fast. I'll love to talk on this topic but on a different series. To start our ReactJS journey, its okay to intrepret_ __ReactDOM__ _as_ __HTML DOM__ _and its_ __render(...)__ _function is used for rendering the elements inside_ __HTML DOM__

## 1.3 - Including more than 1 HTML tags inside ReactDOM.render(...)

_By default,_ __ReactDOM.render(...)__ _function takes only 1 element, however its possible to provide more than one element inside by enclosing the tags within 'div'. For example, we can write the code as_

```
ReactDOM.render(
 <div>
  <h1>Hello world!</h1>
  <br/>
  <h2>A ReactJS Application</h2>
 </div>,
 document.getElementById('root')
);
```
_We can render almost anything using the above function but in all ReactJS applications, we render_ __Components__ _instead of individual HTML elements.
However, before we can render components, we need to create one._

## 1.4 - Creating ReactJS Components

__Note : We'll be using ES6 syntax for components. ReactJS components can be created using ES5 syntax and that has its own learning curve__

_We can create a ReactJS component using ES6 class syntax as_

```
class FirstReactComponent extends React.Component {
}
```
_As stated earlier, each ReactJS components comes with a single_ __render(...)__ _function which means all app related rendering elements shall be embedded inside this function. We can write the function as_

```
class FirstReactComponent extends React.Component {
render() {
 return(
  <div>
   <h1>Hello world!</h1>
   <br/>
   <h2>A ReactJS Application</h2>
  </div>
  );
 }
}

```
_So we have a ReactJS component which is capable of rendering a 'h1' and an 'h2' tag_

## 1.5 - Rendering ReactJS Components inside HTML

_With_ __FirstReactComponent__ _we have a react component with a_ __render()__ _function which contains the stuffs that need to be rendered. We render ReactJS components in the same way as we render any native HTML components._

_To render ReactJS component, we'll use the following syntax in_ __ReactDOM.render(...)__ _function_

```
ReactDOM.render(<FirstReactComponent/>, document.getElementById('root'));
```

## 1.6 - Creating Multiple Components

_Any functional react application will have more than one component and all of them has to be rendered at some point of time. Since we use_ __ReactDOM.render(...)__ _function for rendering components, we can render multiple components wrapped inside 'div'_

```
class SecondReactComponent extends React.Component {
 render() {
  return(
   <h2>I am 2nd React Component </h2>
  );
 }
}
 class FirstReactComponent extends React.Component {
render() {
 return (
  <div>
   <h1>Hello world!</h1>
   <br/>
   <h2>A ReactJS Application from Component</h2>
  </div>
  );
 }
}

ReactDOM.render(<div>
  <FirstReactComponent/>
  <SecondReactComponent/>
 </div> ,
 document.getElementById('root')); 

```

## 1.7 - Rendering 1 ReactJS component inside another

_Each ReactJS component can have only one_ __render(...)__ _function, however this doesn't prevent us from calling another component_ __render(..)__ _function inside it. The code with exact same behaviour can be replicated by calling_ __SecondReactComponent__ from inside __FirstReactComponent__

```
 class SecondReactComponent extends React.Component {
  render() {
   return(
    <h2>I am 2nd React Component </h2>
   );
  }
}

class FirstReactComponent extends React.Component {
 render() {
  return (
   <div>
    <h1>Hello world!</h1>
    <h2>A ReactJS Application from Component</h2>
    <SecondReactComponent/>
   </div>
  );
 }
}

ReactDOM.render(<FirstReactComponent/>,	document.getElementById('root'));
   
  ```
## 1.8 - Multiple Usage of ReactDOM.render(...) function

__ReactDOM.render(...)__ _function can be used multiple times as it works on the elements specified by_ __document.getElementById(...)__. _If we use it for the same element, then it will override the existing one. For example, if we use this function to render_ __SecondReactComponent__ _as_

```
ReactDOM.render(<FirstReactComponent/>, document.getElementById('root')); 
ReactDOM.render(<SecondReactComponent/>, document.getElementById('root')); 

```

_it will override the_ __FirstReactComponent__ _and render the_ __SecondReactComponent__ _at the same 'div'. i.e 'root'. To avoid the overriding problem we can create multiple <div> areas which can be rendered by multiple_ __ReactDOM.render(...)__ _functions. so we can change the HTML to have two 'div' areas namely 'first' and 'second'_

```
<body>
    <div id="First"></div>
    <div id="Second"></div>
    <script type="text/babel">
    class SecondReactComponent extends React.Component {
      render() {
        return(
          <h2>I am 2nd React Component </h2>
        );
      }
    }

    class FirstReactComponent extends React.Component {
      render() {
        return (
          <div>
            <h1>Hello world!</h1>
            <h2>A ReactJS Application from Component</h2>
            <SecondReactComponent/>
          </div>
         );
      }
    }

    ReactDOM.render(<FirstReactComponent/>, document.getElementById('First')); 
    ReactDOM.render(<SecondReactComponent/>, document.getElementById('Second')); 
    </script>
  </body>

```
_In this case, both 'First' and 'Second' <div> will be rendered at their respective places in the HTML._

## 1.9 - Summary

_Components are basic building blocks of ReactJS applications. Components can be nested to create parent child relationship or can be clubbed inside 'div' within the render function._

