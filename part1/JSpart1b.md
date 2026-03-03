# JavaScript

In order to fully understand react it's important to back track and understand what React is built upon JavaScript...

JS has advanced rapidly and due to this browsers do not yet support many of JavaScript's newest features. Due to this fact, a lot of code run in browsers has been transpiled into older more compatible versions, the most popular way of doing this is using __Babel__. Transpilation is automatically configured in React applications created with Vite.

Node.js is a JavaScript runtime environment based on Google's Chrome V8 JavaScript engine and works practically anywhere from servers to phones. The latest versions of Node already understand the latest of JS so the code does not need to be transpiled.

We can create a node file by using the cmd:

```cmd
node name_of_file.js
```

It's also possible to write JS into the node.js console, which is opened by typing node in the command line, as well as the browser's own developer tool console. One thing to note about JavaScript is that it is sort of reminiscent both in name and syntax, to Java. But it's core mechanism of the language could not be more different.

### Variables

In JS defining variables can be done in multiple ways:

```js
const x = 1
let y = 5

console.log(x, y) // 1 5 printed
y += 10
console.log(x, y) // 1 15 printed
y = 'sometext'
console.log(x, y) // 1 sometext are printed
x = 4 // causes an error

```

-**const** does not define a variable but a constant for which the value cannot be changed once set. 
-**let** On the other hand defines a normal variable

In the example above we can see that a variable's data type can change during execution. At the start `y` stores and integer but at the end it stores a string.

You also have the option to define variables in JS using **var** however const and let are much newer and made to combat certain features of var that are more or less annoying. Use `const` by default, use `let` only when you need to reassign.

The main reason however is that **var** is function-scoped and not block scoped meaning that if you use var it can leak out and be used outside the block while if you use let it won't and will spit an error. You are also able to redeclare using var which let does not allow. so just don't use var in most cases.

### Arrays

An array with some examples of use:

```js
const t = [1, -1, 3]

t.push(5)

console.log(t.length) // 4 is printed
console.log(t[1])     // -1 is printed

t.forEach(value => {
  console.log(value)  // numbers 1, -1, 3, 5 are printed, each on its own line
})                    
```

The most noticeable thing about this example is the fact that although a variable declared with const cannot be reassigned to a different value, the contents of the object it references can still be modified. This is because const declaration ensures the immutability of the reference itself, not the data points to. Similar to the furniture in a house being able to move but the address is the same.

One way of iteration through an array is using `forEach` it receives a function defined using the arrow syntax as a parameter:

```js
value => {
  console.log(value)
}
```

forEach calls the function for every item in the array, always passing the individual item as an argument (The actual value which replaces the defined parameter in a function). The function as the argument of forEach may also receive other arguments.

In the previous code we used `push` to add to the list. However this modifies the list itself, in React it is common to use `concat` instead as it creates a completely new list with the new values meaning the original array will always remain unchanged.


```js
const t = [1, -1, 3]

const t2 = t.concat(5)  // creates new array

console.log(t)  // [1, -1, 3] is printed
console.log(t2) // [1, -1, 3, 5] is printed
```

There are plenty of useful methods defined for arrays such as the `map` method:

```js
const t = [1, 2, 3]

const m1 = t.map(value => value * 2)
console.log(m1)   // [2, 4, 6] is printed
```

Based off a old array, map creates a new array, for which each function given as a parameter is used to create the item. In the example the original value is multiplied by two.

Map is also able to transform the array into something completely different:

```js
const m2 = t.map(value => '<li>' + value + '</li>')
console.log(m2)  
// [ '<li>1</li>', '<li>2</li>', '<li>3</li>' ] is printed
```

Here an array filled with integer values  is transformed into an array containing strings of HTML using the map method.

Individual items of array are easy to assign to variables with the help destructuring assignment.

```js
const t = [1, 2, 3, 4, 5]

const [first, second, ...rest] = t

console.log(first, second)  // 1 2 is printed
console.log(rest)          // [3, 4, 5] is printed
```

Above, the first and second values are made to be 1 and 2 respectively. Well by using `...rest` the last remaining integers are collected and put into its own separate array.


### Object

There are a few different ways of defining objects in JS. One very common method is using object literals, which happens by listing its properties within braces.

```jsx
const object1 = {
  name: 'Arto Hellas',
  age: 35,
  education: 'PhD',
}

const object2 = {
  name: 'Full Stack web application development',
  level: 'intermediate studies',
  size: 5,
}

const object3 = {
  name: {
    first: 'Dan',
    last: 'Abramov',
  },
  grades: [2, 3, 5, 3],
  department: 'Stanford University',
}
```

The values of the properties can be of any type (Inclusive of objects themselves).

The properties of an object are referenced using the `dot` notation, or by using brackets:

```jsx
console.log(object1.name) // Arto Hellas printed
const fieldName = 'age'
console.log(object1[fieldName]) // 35 is printed
```

You are also able to add properties to an object on the fly by either using dot notation or brackets:

```jsx
object1.address = "Helsinki"
object1['secret number'] = 12345
```

The latter has to be done with brackets because you can't include a space using dot notation. Objects also have methods too (But self study this)

Objects can be defined using constructor functions, which results in similarities e.g. Java's classes. However JS does not have classes in the same senses as OOP languages. There has been in newest version class syntax which helps structure oop classes

### Functions

The complete process of an arrow function looks like this:

```jsx
const sum = (p1, p2) => {
  console.log(p1)
  console.log(p2)
  return p1 + p2
  }
```

Function calling

```jsx
const result = sum(1,5)
console.log(result)
```

If there is only one parameter we can exclude () from the function

```jsx
const square = p => {
  console.log(p)
  return p * p
}
```

If the function only contains a single expression then the braces are not needed. In this case, the function only returns the result of its only expression. Now, if we remove console printing, we can further shorten the function definition:

```jsx
const square = p => p * p
```

This form is handy when manipulating arrays - e.g. map method

```jsx
const t = [1, 2, 3]
const tSquared = t.map(p => p * p)
// tSquared is now [1, 4, 9]
```

The original way before arrow functions is much more similar to python there are two ways to reference the function one is giving a name in func declaration:

```jsx
function product(a,b) {
  return a * b

  const result = product(2, 6)
  // result is now 12
}
```

The other way is by using a function expression. In this case there is no need to give the func a name and the definition may reside among the rest of the code:

```jsx
const average = function(a,b) {
  return (a + b)/2
}

const result = average(2, 5)
// result is now 3.5
```

Task 1.3: Course info step 3

 We want to create objects for our application:

```jsx
const App = () => {
  const course = 'Half Stack application development'
  const part1 = {
    name: 'Fundamentals of React',
    exercises: 10
  }
  const part2 = {
    name: 'Using props to pass data',
    exercises: 7
  }
  const part3 = {
    name: 'State of a component',
    exercises: 14
  }

  return (
    <div>
      ...
    </div>
  )
}
```
Creates an object for each part, however there is an easier way of doing this by setting up an array:

```jsx
const App = () => {
  const course = 'Half Stack application development'
  const parts = [
    {
      name: 'Fundamentals of React',
      exercises: 10
    },
    {
      name: 'Using props to pass data',
      exercises: 7
    },
    {
      name: 'State of a component',
      exercises: 14
    }
  ]

  return (
    <div>
      ...
    </div>
  )
}
```

In order to access the objects in the array we use the dot product and it's corresponding index such as parts[0].name for "Fundamentals of React" as an example

### Objects methods and "this"

Arrow functions and functions defined using the `function` keyword vary substantially when it comes to how they behave and respect to the keyword `this`, which refers to the object itself.

We can assign methods to an object by defining properties that are functions:

```jsx
const arto = {
  name: 'Arto Hellas',
  age: 35,
  education: 'PhD',

  greet: function() {
    console.log('hello, my name is ' + this.name)
  },
}

arto.greet()  // "hello, my name is Arto Hellas" gets printed
```

Methods can be assigned to objects even after the creation of the object:


```jsx
const arto = {
  name: 'Arto Hellas',
  age: 35,
  education: 'PhD',
  greet: function() {
    console.log('hello, my name is ' + this.name)
  },
}


arto.growOlder = function() {
  this.age += 1
}

console.log(arto.age)   // 35 is printed
arto.growOlder()
console.log(arto.age)   // 36 is printed
```
