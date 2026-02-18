- Usestate
- Useeffect
- red

# Introduction to React

We will now start by creating an application using a tool called __Vite__, Namely the create-vite tool.

```
npm create vite@latest
```
Then answer the questions like this:
![alt text](image.png)

This whole process means we have created an application called part1. If we had answered "Yes" to the question "Install with npm and start now?" the tool would have installed all required dependencies and started the application automatically. But we will work through the steps manually

1. Create the files using npm create vit@latest
2. Change Directory into the folder
3. `npm install` the required library 
4. `npm run dev` to start the process

Vite starts the application by default on port 5172 if its not free it will move to the next port number.

### Component

The file app.jsx now defines a React component with the name App. The command on the final line of main.jsx 

```jsx
ReactDOM.createRoot(document.getElementById('root')).render(<App />)
```

renders its contents into the div-element, defined in the file index.html, having the id value 'root'.

By default, the file index.html doesn't contain any HTML markup that is visible to use in the browser:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>part1</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

In React all content that needs to be rendered is normally done by using React components...

```jsx
const App = () => (
  <div>
    <p>Hello world</p>
  </div>
)
```
This component will be rendered as a div-tag, which wraps a p-tag containing the text Hello World.

Technically the component is defined as a JS function. The following is a function (which also does not receive any parameters):

```jsx
() => (
  <div>
    <p>Hello world</p>
  </div>
)
```

But the component is then assigned to the constant variable App

```jsx
const App = ...
```

There are a few ways to define an function in JSX the most popular way now is using the arrow function. The function defining the component can be anything such as:

```jsx
const App = () => {
  console.log('Hello from component')
  return (
    <div>
      <p>Hello world</p>
    </div>
  )
}

export default App
```

Which returns Hello from component inside of the console. 

It is also possible to render dynamic content inside of a component.

```jsx
const App = () => {
  const now = new Date()
  const a = 10
  const b = 20
  console.log(now, a+b)

  return (
    <div>
      <p>Hello world, it is {now.toString()}</p>
      <p>
        {a} plus {b} is {a + b}
      </p>
    </div>
  )
}
```

Any JavaScript code within the curly braces is evaluated and the result of this evaluation is embedded into the defined place in HTML produced by the component.

Note that you should not remove the line at the bottom of the component.

NEVER remove:

```jsx 
export default App
```

from the bottom of the component.

# JSX

It seems the React components are retuning HTML markup, however it's not actually the case. The layout of React components is mostly written using JSX (JavaScript XML). Although JSX looks like HTML, we are dealing with a way to write JavaScript, JSX returned by React components is compiled JavaScript.

After compiling (In the context of compiling JSX is essentially the middle man, basically it will take the JSX style and then swap your JSX to normal JavaScript) your code should look like this:

```jsx
const App = () => {
  const now = new Date()
  const a = 10
  const b = 20
  return React.createElement(
    'div',
    null,
    React.createElement(
      'p', null, 'Hello world, it is ', now.toString()
    ),
    React.createElement(
      'p', null, a, ' plus ', b, ' is ', a + b
    )
  )
}
```

The compilation is handled by Babel. Projects created by Vite is are configured to compile automatically. 

In practice JSX is much like an HTML with the distinction that with JSX you can easily embed dynamic content by writing appropriate JS within curly braces. In the end JSX is a templating language.

JSX is "XML-like" In the sense that every tag also needs to be closed e.g. <br> <br />