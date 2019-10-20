## Styling React

You can add CSS classes in JSX.

However: since class is a reserved keyword in JS, spell it className in JSX:

```react
class Message extends React.Component {
  render() {
    return <div className="urgent">Emergency!</div>
  }
}
```

You can inline CSS styles, but now style takes a JS object:

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