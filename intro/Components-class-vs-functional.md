# Components (class vs. Functional)

---------------------------------



There are two main ways of creating components in React. 

- Class Based components (object oriented)
- Functional Components (also known as presentational components)

> **NOTE:** functional components are much more component nowadays with the advent of react hooks with *React v16.8+* 



**What is a Class component?**

> A Class component is a React class with a render method...

`demo/hello/index.js`

```react
class Hello extends React.Component {
  render() {
    return <p>Hi Everyone!</p>;
  }
}
```

> simply a `js class object` with some react-specific sprinkles. 



**ReactDOM.render**: adds component to HTML

```react
ReactDOM.render(<Hello />,
  document.getElementById("root"));
```



**Functional Component**

> is simply a react component that accepts props and returns a react element. These are considered to be `pure components`  which means given the same arguments (props) it will always return the same data, each time. This means that we shouldn't have side-effects like fetching data or mutating any items of state from these components. 

```react
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>
}
```

> not how we're able to pull the name property off of the props object that gets passed into our component. 



