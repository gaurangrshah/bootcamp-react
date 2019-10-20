# React Props 

---------------------------------

## Properties - aka. Props

Props allow us to create dynamic re-usable components. 

> This often means making it configurable or customizable similar to how arguments make functions configurable. 

`Hello.js`

```react
class Hello extends React.Component {
  render() {
    return <p>Hi Everyone!</p>;
  }
}
```



> It would be better if we could *configure* our greeting.
>
> Our greeting will be *Hi ______ from ______*.
>
> Let’s make two “properties”:
>
> - to
>
>   Who we are greeting
>
> - from
>
>   Who our greeting is from



### Demo: Hello-2

`demo/hello-2/index.js`

```react
ReactDOM.render(
  <Hello to="me" from="you" />,
  document.getElementById("root")
);
```

> Set properties on element; get using this.props.propName.



**Props are also immuatable:**

> - this means that data from props should not be acted upon directly.
>
> react provides other paradigms such as state, in order to mutate data and/or functionality.



`demo/hello-2/Hello.js`

```react
class Hello extends React.Component {
  render() {
    return (
      <div>
        <p>Secret Message: </p>
        <p>Hi {this.props.to} from {this.props.from}</p>
      </div>
    );
  }
}
```



Props can consist of any type of data:

- numbers, arrays, objects, booleans, and functions/methods. 

`index.js`

```react
class App extends React.component {
  render() {
    <div>
    	<Hello
        to="Ringo"
        from="Paul"
        num={3}
        data=([1, 2, 3, 4, 5])
        isFunny={true}
      />
      <Hello to="Ringo" from="Paul"/>
    </div>
  }
}
```

`Hello.js`

```react
class Hello extends React.component {
  
  console.log(this.props) // will output all provided props.

// this.props = { to: "Ringo", from: "Paul", num: 3, data: [1, 2, 3, 4, 5]}

  render() {
    return (
    	<div>
      	Hi {this.props.to} from {this.props.from}
      </div>
    )
  }
}
```



**Booleans As Props:**

`index.js`

```react
class App extends React.component {
  render() {
    <div>
    	<Hello
        isFunny={true}
      />
      <Hello to="Ringo" from="Paul"/>
    </div>
  }
}
```

this can also be provided as:

```react
class App extends React.component {
  render() {
    <div>
    	<Hello
        isFunny

        {/* this.props = { isFunny: true } */}
      
      />
      <Hello to="Ringo" from="Paul"/>
    </div>
  }
}
```



`index.js`

```react
class App extends React.component {
  render() {
    <div>
    	<Hello
        to="Ringo"
        from="Paul"
        bangs={4}
      />
    </div>
  }
}
```

`Hello.js`:

```react
class Hello extends React.component {
  render() {
    let bangs = "!".repeat(this.props.bangs)
    return (
    	<div>
        <p>Hi {this.props.to} from {this.props.from}{"!".repeat(this.props.bangs)}</p>
      </div>
    )
  }
```

`-OR-`

```react
class App extends React.component {
  render() {
    <div>
    	<Hello
        to="Ringo"
        from="Paul"
        img="https://pathtoimage/image.jpg"
      />
    </div>
  }
}
```

```react
class Hello extends React.component {
  render() {
    return (
    	<div>
      	Hi {this.props.to} from {this.props.from}
        <img src={this.props.img}/>
      </div>
    )
  }
```



---------------------------------

Slot machine:

`Machine.js`

```react
import React, { Component } from "react";

export default class Machine extends Component {
  render() {
    // destructure the provided props from the props object
    const { s1, s2, s3 } = this.props;

    // check if winner: using short circuit
    const winner = s1 === s2 && s2 === s3;

    return (
      <div>
        <h1>Slot Machines!</h1>
        {/* <span role="img">{this.props.s1 || "🍊"}</span> */}
        {/* refernce items from props directly */}
        <span role="img">{s1}</span>
        <span role="img">{s2}</span>
        <span role="img">{s3}</span>
        {/* handles logic to determine output based on the value of winner */}
        <p>{winner ? "Winner" : "Loser!"}</p>
      </div>
    );
  }
}

```

`index.js`:

```react
import Machine from "./Machine";

function App() {
  return (
    <div className="App">
      <Machine s1="🍇" s2="🍇" s3="🍇" />
    </div>
  );
}
```

![slotmachine](https://tva1.sinaimg.cn/large/006y8mN6gy1g84ltubufeg30xk0m27wk.gif)

