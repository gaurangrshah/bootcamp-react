# Compiling JSX with Babel



## Babel Compiler

Fundamentally JSX is just syntactic sugar for the `createElement` method provided by react. This is where we are extending our class components from as well. 

```react
React.createElement(component, props, ...children)
```

> As we can see the method takes 3 arguments, the first being the component that is being crreated and the rest are it's props and/or any of it's children if provided. 
>
> -  Children are any elements rendered inside the rendered component. 

To better understand how babel compiles our `jsx` syntactic sugar into a lower level react method we can use the babel online compiler, by compiling the following syntax with the bable online compiler:

[Babel Compiler]:https://babeljs.io/repl

```react
<div>
  <h1>My Image</h1>
  <img src="https://pathtoimage.com/image.jpg"/>
</div>
```

![image-20191019215841025](https://tva1.sinaimg.cn/large/006y8mN6gy1g84fn9li4fj317t06rta7.jpg)

> Not how the compiler nests several `React.createElement()` calls to render our `h1` and `img` tags inside our `div` wrapper element



## Transpiling JSX in Browser

**Babel standalone library**

Currently we're using the CDN link for `Babel` in our project to process and compile our JSX:

- Easy to get started — nothing to install!

  ```html
  <script
    src="https://unpkg.com/babel-standalone"></script>
  ```

- Mark JSX files with `type="text/jsx"`:

  ```html
  <script src="index.js" type="text/jsx"></script>
  <!-- NOTE: (type) must = "text/jsx" -->
  ```



**Use Babel on Command Line**

While it’s convenient to transpile JSX into JavaScript directly in the browser like this, it’s not suitable for real-world deployment: it takes a second to do the conversion, leading to a poor experience for users.

Better for deployment is to convert JSX to JavaScript once, via the command line, and then save and use the converted JS directly.

To do this:

1. You need to install [npm](http://npmjs.com)

2. Then use npm to install Babel and settings for React:

   ```shell
      $ npm install @babel/core @babel/cli @babel/preset-react
   ```

3. To convert a file:

   ```shell
   $ node_modules/@babel/cli/bin/babel.js --presets @babel/react
        file.jsx > file.js
   ```



------

