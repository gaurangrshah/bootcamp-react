# Default Props

---------------------------------

Default props allow a way to provide a fallback option in case our data is not available when expected:

```react
import React, { Component } from "react";

export default class Hello extends React.Component {
  render() {
    let bangs = "!".repeat(this.props.bangs);
    return (
      <div>
        Hi {this.props.to} from {this.props.from} {bangs}
        {/* outputs the number of bangs calculated from props */}
        <img src={this.props.img} />
      </div>
    );
  }
}

```

`index.js`

````js
import Hello from "./Hello";

function App() {
  return (
    <div>
      <Hello to="Ringo" from="Paul" bangs={4} />
      <Hello to="George" from="Faul" />
    </div>
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

````



Currently if we do not provide any value for `bangs`  prop value, then our applicationd does not display any of the `exclamation points.`

![image-20191020015658453](https://tva1.sinaimg.cn/large/006y8mN6gy1g84mj3mfhrj30e504574e.jpg)



In order to rectify this we can provide our default props:

`Hello.js`

```react
import React, { Component } from "react";

export default class Hello extends React.Component {
  static defaultProps = {
    // providing default values for necessary fields.
    from: 'Anonymous',
    bangs: 1
  }
  render() {
    let bangs = "!".repeat(this.props.bangs);
    return (
      <div>
        Hi {this.props.to} from {this.props.from} {bangs}
        {/* outputs the number of bangs calculated from props */}
        <img src={this.props.img} />
      </div>
    );
  }
}


```

![image-20191020015927607](../../../Library/Application Support/typora-user-images/image-20191020015927607.png)