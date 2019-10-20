# Standard App Layout

---------------------------------

It's conventional for the top-level component to be named App. This allows the app component to render all of the other components. 

`App.js`

```react
class App extends React.component {
  render() {
    return (
    	<div>
      	<h1>Greetings!</h1>
        <Hello/>
        <Goodbye/>
      </div>
    )
  }
}
```



---------------------------------





`demo/hello/index.js`

```js
class Hello extends React.Component {
  // extends the React Component Object -inheriting default features of a react class object
  render() {
    // render method is required with class based objects.
    return <p>Hello 🌎!</p>;
    // return statement is required to defined rendered output.
  }
}

ReactDOM.render(<Hello />, document.getElementById('root'));

// export default Hello
// exports our component making it available to any other render method via import statement.


```

`index.html`

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>First Component</title>
</head>

<body>
  <div id="root"></div>
  <!--application can render elements/components by mounting to this root div element-->
  <script src="https://unpkg.com/react/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom/umd/react-dom.development.js"></script>

  <script src="https://unpkg.com/babel-standalone"></script>
  <!--must load any files we want to import jsx from here-->
  <script src="Hello.js" type="text/jsx"></script>

<!-- Hello Component gets defined before index, since index is where we want to use the component, this ensures that it is availble to index when index gets parsed.-->
  <script src="index.js" type="text/jsx"></script>

  </script>
</body>

</html>

```

```react

class App extends React.Component {
	render() {
		return (
				{/* extracting the hello component  */}
				{/* <h1>Hello 🌎!</h1> */}
				<Hello />
		);
	}
}

ReactDOM.render(<App />, document.getElementById('root'));

```



**Rendering multiple elements/components**:

```react
class App extends React.Component {
	render() {
		return (
      <div> 
        {/* wrapper div element can wrap any number of elements, but cannot have any sibling elements itself */}
        <Hello />
        <Hello />
      </div>  
		);
	}
}
```

> when rendering multiple components and/or html elements, they must all be wrapped within a single enclosing wrapper element such as a <div> or <ul> or event react's newer <> fragments.
>
> - this is because the return statement only renders one singular wrapping element. 