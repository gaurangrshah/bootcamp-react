# React (REMOTE )Hello World Example

- using cdn links

- Use Any dev server: 

  - [Live Server]:https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer



`index.html`:

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
  <script src="https://unpkg.com/react/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom/umd/react-dom.development.js"></script>

  <script src="https://unpkg.com/babel-standalone"></script>
  <script src="index.js" type="text/jsx"></script>

</script>
</body>
</html>
```



`index.js`

```js
class App extends React.Component {
	render() {
		return (
			<div>
				<h1>Hello 🌎!</h1>
			</div>
		);
	}
}

ReactDOM.render(<App />, document.getElementById('root'));

```

