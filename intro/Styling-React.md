## Styling React

You can add CSS classes in JSX.

However: <u>since class is a reserved keyword</u> in JS, which is why we use`className` in JSX:

```react
class Message extends React.Component {
  render() {
    return <div className="urgent">Emergency!</div>
  }
}
```



You can inline CSS styles, although: 

> **NOTE:** the <u>syntax of the css properties, is written in `camel case`</u> with JSX

```react
class Box extends React.Component {
  render() {
    return <b style={{color: 'blue', backgroundColor: 'white'}}>{this.props.message}</b>;
  }
}
```

and we can also predefine classes as Javascript Objects:

```react
class Box extends React.Component {
  render() {
    const colors = {
      color: 'blue',
      backgroundColor: 'white',
    };

    return <b style={colors}>{this.props.message}</b>;
  }
}
```

We can also lass in the styles as props into the component, allowing for more dynamic styling. 

```react
class Box extends React.Component {
  render() {
    const colors = {
      color: this.props.favoriteColor,
      backgroundColor: this.props.otherColor,
    };

    return <b style={colors}>{this.props.message}</b>;
  }
}
```

> **NOTE:** Inline styles are generally less performant, and can cause unexpected repaint issues. Insread classes are generally the perferred method of styling components



There are several reserved keywords in React, because they conflict with other html attributes or properties:

[DomElements List]: https://reactjs.org/docs/dom-elements.html
[Javascript Reserved Keywords]: https://www.w3schools.com/js/js_reserved.asp





