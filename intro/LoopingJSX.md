# Looping thru JSX

---------------------------------



It’s common to use array.map(fn) to output loops in JSX:

```react
class Messages extends React.Component {
  render() {
    const msgs = [
      {id: 1, text: "Greetings!"},
      {id: 2, text: "Goodbye!"},
    ];

    return (
      <ul>
        { msgs.map(m => <li>{m.text}</li>) }
        {/* mapping thru the messages array of objects and returning an <li> for each item on the array. */}
      </ul>
    );
  }
}
```

---------------------------------

### Demo: Friends!

`demo/friends/Friend.js`

```react
class Friend extends React.Component {
  render() {
    const { name, hobbies } = this.props;
    return (
      <div>
        <h1>{name}</h1>
        <ul>
          {hobbies.map(h => <li>{h}</li>)}
          {/* render each hobby */}
          
        </ul>
      </div>
    );
  }
}
```

`demo/friends/index.js`

```react
ReactDOM.render(
  <div>
    <Friend name="Jessica" hobbies={["Tea", "Frisbee"]} />
    <Friend name="Jake" hobbies={["Chess", "Cats"]} />
  </div>,
  document.getElementById("root")
);
```



**NOTE**: we can also predefine the map as a function:

```react
import React, { Component } from "react";

export default class Friend extends React.Component {
  render() {
    const { name, hobbies } = this.props;

    // extracted render hobbies returning just the values need to render each hobby as an <li>
    const renderHobbies = hobbies.map(h => <li>{h}</li>);

    return (
      <div>
        <h1>{name}</h1>
        <ul>{renderHobbies}</ul>
        {/* passing the values stored via renderHobbies */}
      </div>
    );
  }
}
	
```

