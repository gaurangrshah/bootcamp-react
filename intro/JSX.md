## JSX

> `javascript xml syntax`
>
> jsx allows us to write html like javascript syntax to render elements. 

### Using JSX

![image-20191019213941186](https://tva1.sinaimg.cn/large/006y8mN6gy1g84f3jhefpj30lx09cach.jpg)

- JSX isn’t legal JavaScript
  - It has to be “transpiled” to JavaScript
- You can do this with [Babel](https://babeljs.io)

```react
class JSXDemo extends React.component{
  render() {
   return (
   	 <div>
      <h1>My Image</h1>
      <img src="https://pathtoimage.com/image.jpg"/>
    </div>
   )
  }
};

ReactDOM.render(<JSXDEMO/>, document.getElementById('root'));
```



## Embedding Javascript into JSX:

> embedding javascript into JSX allows us to markup dynamic content very easily:

```react
class JSXDemo extends React.component{
  render() {
   return (
   	 <div>
       {/* the expression in the curly braces will get evaluated to 16.8 and that is what is then rendered to the browser */}
      <h1>My number is: {2 * 8.4}</h1>
       {/* //=> "My number is 16.8" */}
    </div>
   )
  }
};

ReactDOM.render(<JSXDEMO/>, document.getElementById('root'));
```



**Execute Function in JSX**

```react
<div>
  <h1>{getMood()}</h1>
</div>
```

> `getMood()` is a function, and we can call it inline which will return back any elements that get rendered by it, based on this usage we'd most likely expect this to return a string.



**Conditionals in JSX**:

```react
if (score > 100) {
  return <b>You win!</b>
}
```

You can also “re-embed” JavaScript in JSX:

```react
if (score > 100) {
  return <b>You win, { playerName }</b>
}
```

> looks for JavaScript variable playerName)



Deeper look at dynamic data in `jsx`:

```react
function getNum() {
  return Math.floor(Math.random() * 10) + 1;
  // generates a random number
}

class NumPicker extends React.component{
  render() {
    const num = getNum()
   return (
 		<div>
    	<h1>Your Number is{num}</h1> 
       <p>{num === 7 ? 'Congrats' : 'Unlucky'}</p>
       {num === 7 ? <img src="pathtoimage.com/image.jpg"/> : null }
    </div>
   )
  }
}
```

> here we're generating a random number and outputting it to the dom using the `getNum()` function.
>
> then we conditionally provide a message based on the random number, we give a positive message if num = 7 & display an image as well, otherwise we'll provide a negative message, and display no image by rendering null instead.

**Using the short circuit operator**

```react
function getNum() {
  return Math.floor(Math.random() * 10) + 1;
  // generates a random number
}

class NumPicker extends React.component{
  render() {
    const num = getNum()
   return (
 		<div>
    	<h1>Your Number is{num}</h1> 
       <p>{num === 7 ? 'Congrats' : 'Unlucky'}</p>
       
       {num == 7 && <img src="pathtoimage.com/image.jpg"/> }
       
    </div>
   )
  }
}
```

> here we're able to display the image ONLY when num = 7  effectively doing the same as above but with a bit shorter syntax.



We can also conditionally render by pre-defining a message, conditionally based on the ouput:

```react
class NumPicker extends React.component{
  render() {
    const num = getNum()
    
    let msg
    if(num === 7) {
      msg = 
        <div>
          <h2>Congrats!</h2>
          <img src="https://pathtoimage.com/image.jpg"/>
        </div>
    } else {
      msg = 
        <div>
        	<p>Sorry You Lost</p>
        </div>
    }
    
    
   return (
 		<div>
    	<h1>Your Number is{num}</h1> 
       <p>{num === 7 ? 'Congrats' : 'Unlucky'}</p>
      
       {msg}
       
    </div>
   )
  }
}
```

