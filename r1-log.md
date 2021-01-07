# #100DaysOfCode Log - Round 1 - [Iris Diakoumi]

The log of my #100DaysOfCode challenge. Started on [November 14, Saturday, 2020].

## Log

### R1D1

I'm digging into Javascript after some days as a refresher to HTML and CSS. DOM Selector & Events for today and moving into more advanced js, starting with scope.

### R1D2

Practised DOM manipulation using several methods, read up on "this", made the gradient styler as a quick exercise

[You Might Not Need jQuery](http://youmightnotneedjquery.com/)

You should imagine bindings(variables) as tentacles, rather than boxes. They do not _contain_ values; they _grasp_ them.

[Open Sauced](https://opensauced.pizza/)

[Understanding the "this" keyword, call, apply, and bind in JavaScript - ui.dev](https://ui.dev/this-keyword-call-apply-bind-javascript/)

### R1D3

```jsx
const whereAmI = (username, location) =>
  username && location ? 'I am not lost' : 'I am totally lost'; // one line operation does not need closure, else needs return statement
```

Symbols: values created with the `Symbol` function → p.106 El.JS

My first pull request that fixes an issue!

[How To Create a Pull Request on GitHub | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-create-a-pull-request-on-github)

- Alternate for loop

```jsx
for (let entry of JOURNAL) {
console.log(${entry.events.length} events.);
```

When a for loop looks like this, with the word _of_ after a variable definition, it will loop over the elements of the value given after _of_. This works not only for arrays but also for strings and some other data structures. - a case of polymorphism

- Closures, currying, compose

### R1D4

- Things to do as a developer : Minimize side-effects → Functional Purity

  Input → Function →Return Value

  Inside a function should be like its own little world. Don't affect outside scope.

  Return a value so that you avoid `undefined` . —> Determinism

- Map, filter, reduce for arrays

```jsx
const doubleArray = array.map(num ⇒ num * 2); //directly maps each array element
//and replaces it with its manipulated counterpart

```

```
const filterArray = array.filter(num => num < 6);
//it will create a new array that contains only the original values that
//fullfill the condition
```

```
const reduceArray = array.reduce((accumulator,num) => {
	return accumulator + num;
}, 0);
//0 is the starting value for the accumulator, acc shorthand for accumulator
//the end result is NOT an array -- not even for strings
```

- primitive vs reference types
- context (≠ scope)
- instantiation —> when you make a copy of an object and reuse the code

### R1D5 & D6

- Pass by value vs. pass by reference ? primitive types are immutable - we copy the value to another memory spce
- objects pass by reference, so to only copy an object's value we do:

  ```jsx
  let clone = Object.assign({}, objToCopy);
  OR;
  let clone = {...objToCopy}; //Spread operator - > newer feature
  ```

  and any further changes we make to the original object will not affect the clone's contents. —> _Shallow cloning_ - clones only the first layer of parameters.

  IF the original object has an object as a value to a property, THEN that will be passed by reference still.. and will follow all future changes to original and clones.

  _Deep Cloning - performance implications for very deep objects_

  ```jsx
  let superClone = JSON.parse(JSON.stringify(objToCopy);
  ```

  - type coercion `==`
  - Object.is(param1, param2) —> handles some edge cases

  [JavaScript Object Explorer](https://sdras.github.io/object-explorer/)

  Object method explorer

  - **ES7** : .includes() works for arrays but searches for the complete value, not substrings OH wait it works with `filter()`

    ```jsx
    const dragons = ['Tim', 'Johnathan', 'Sandy', 'Sarah'];
    dragons.filter((name) => name.includes('John'));
    //returns Array [ "Johnathan" ]
    ```

    exponential operator ** → eg `const cube = (x)⇒ x**3`

  - **ES8:**

    Object.values

    Object.entries

    _Object.keys_

    ```jsx
    *Object.keys(obj).forEach((key,index) ⇒ {
    	console.log(key, obj[key]);
    })

    Object.values(obj).forEach(value => {
        console.log(value);
    })

    Object.entries(obj).forEach(entry => {
        console.log(entry);
    })

    //example section 158 ZTM
    Object.entries(obj).map(entry => {
        return entry[1] + entry[0].replace('username', '');
    })*
    ```

    - **ES10**

      .flat() - removes a layer of arrays contained inside an array

      .flat(num) - removes _num_ number of layers of contained arrays

      .flat(Infinity) - for when I don't want to count the layers

      .flatMap() - functions as the normal map() function and THEN as flat() on the new array

      .trimStart()

      .trimEnd() —remove blank spaces at the beginning or end of the string

      _\*\*Can chain call methods string.trimStart().trimEnd()_

      **Object.fromEntries(stringName) is run on a string of usually pairs of [key,value] and returns an object == the reverse of Object.entries()**

      ```jsx
      try {
      } catch {} //stopped requiring passing an error argument to catch (error)
      ```

### R1D7

**Object.fromEntries(stringName) is run on a string of usually pairs of [key,value] and returns an object == the reverse of Object.entries()**

Object.values

Object.entries

_Object.keys - old one_

**from object —> array —> manipulate values —> back to object again —? is that a pattern?**

ADVANCED LOOPING:

- for of - **iterables—> arrays and strings**

```jsx
const basket = ['apples', 'grapes', 'oranges'];

//Iterating available for iterable data structures - **arrays**, **strings**
for (item of basket) {
  console.log(item);
}
```

- for in - **enumerable—>** properties of objects

```jsx
const detailedBasket = {
  apples: 5,
  oranges: 3,
  grapes: 100,
};

for (item in detailedBasket) {
  console.log(item);
}

//works for iterables as well, because they are considered objects.
```

- ES2020

Optional Chaining Operator

```jsx
let weight = andrei.pokemon?.pikachu?.weight; //checks is there such objects and
//such properties
```

Nullish Coalescing Operator

```jsx
let power = andrei.pokemon?.pikachu?.power || 'no power'
//this OR checks if the left side is truthy, if not returns the right side

let power = andrei.pokemon?.pikachu?.power **??** 'no power'
//NCO: checks if the left side is null or undefined
```

- Debugging

Instead of inserting console.log('label', value) statements to demonstrate the variables we can use the keyword `debugger;`

Step through - Context - Scope

**JS engine**

- Memory heap — Memory leaks from leftover unused variables, fill up the memory heap, global variables are bad for that
- Call Stack

JavaScript is a single-threaded language that can be non-blocking

Has one call stack - LIFO - only one statement is executed at a time

Multi-threaded environvments face the issue of deadlocks -

---

Async is what can make it be non-blocking. We can run processes in the background and when the result is result is ready it will be called back by the event loop.

Async is needed to avoid delays when waiting for a task to finish executing, or a website freezing etc.

Stack-overflow :

```jsx
//recursion --> infinite loop
function foo() {
  foo();
}

foo();
```

### R1D8 & D9

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a05283a-de24-4b4f-a97b-8f2f39b44e65/Screen_Shot_2020-11-23_at_00.16.05.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a05283a-de24-4b4f-a97b-8f2f39b44e65/Screen_Shot_2020-11-23_at_00.16.05.png)

—Call Stack

—Web Api

—Callback Queue

—Event Log: Event log checks to see if call stack is empty, and if it is it calls the callback that is waiting

**JavaScript is a single-threaded language that can be non-blocking**

MODULES:

_Climbing the mountain of modules_

- Inline script: lack of code reusability, pollution of global namespace
- Script tags: re-copy script tags for every new html page, lack of dependency resolution(the order in which the js script files are included and called is important), still pollutes the global namespace
- IIFEs: solves the global pollution problem, because everything inside an IIFE is local, still no dependency resolution
- Browserify + CommonJS syntax ⇒ Module bundler that creates one file (bundle) with the necessary interdependencies to each other
- ES6 + Webpack2

### R1D10

Toyed around with CSS Flexbox common patterns & CSS Grid common layouts

### R1D11

- Node and Npm intro / update to latest version
- npm init in project directory → package.json
- npm allows for local or global installation (-g)
- node modules installed and listed as dependencies in the package.json file, don't need to be included in the code, eg in Github. Whenever someone runs npm install, the package.json file will download the necessary dependencies.
- dev dependencies are required only for the development phase and are never shipped with the final product code
- "scripts" in package.json are commands that we can batch run with `npm run scriptName`

  ```jsx
  "scripts": {
  	"build": "browserify script.js > bundle.js && live-server"
  }
  ```

  [npm semantic version calculator](https://semver.npmjs.com/)

  Intro to React:

  - Think in Components
  - One way data-flow
  - Virtual DOM

  npx — package runner tool that comes with npm 5.2+

  npx create-react-app myApp

  cd myApp

  npm start

### R1D12

**React Component : Essential Elements**

- import React, { Component } from 'react'
- render()
- return
- export default ComponentName

Tachyons (Styling library) - npm install tachyons —go to index.js `import 'tachyons';`

JSX - React needs to be in scope, that's why we import at the top of each component JS file

Function must return only one element, wrapped in an enclosing tag - can't return a div and an h1

key prop for VirtualDOM to keep track of changes

crazy cattery interface, object returns cards

### R1D13

State : One way data flow — Components that are neighbords and need to communicate, do so by sending state to a common parent and the parent in turn will pass on the state to the neighbor component

Pure components — pure functions, deterministic, receive an input(props) and return the output

State is an **object** that describes the application, mutable and is owned by the parent Component that has the right to change it and pass it on

class ← constuctor( )←super() and then this.state

when we try to return or console.log an event we use `event.target.value`

In React, inside a class anytime we make our own methods, we use arrow functions, and anytime we want to change state we call method `this.setState({key:value })`

For styling, create App.css and/or index.css files to target specific elements

@font-face for more stylized fonts, look for woff font webkits

[Cufon Fonts: Download High Quality Free Fonts for Desktop and WebFonts](https://www.cufonfonts.com/)

### R1D14

Smart vs dumb components — Smart components have state and are usually in a class syntax. Dumb components are pure functions.

[Mock API at Scale | Mocki](https://mocki.io/)

Created mock api to grab the data from

**Lifecycle methods:**

- Mounting
- Updating
- Unmounting

```jsx
componentDidMount() {
    fetch('https://api.mocki.io/v1/8905b8d6')
      .then(response=>response.json())
      .then(users => this.setState({cats: users}));
  }
```

props , state , children

JSX : `style = {{put css styles here but in the form of: **selector: 'value', ...**}}`

folder structure is important

Inside src > components and src > containers

Containers house smart components, that contain state, eg App.js

Components are pure functions

Don't forget to update the paths and imports

npm run build (script inside package.json)

npm install -g serve serve -s build

Find out more about deployment here:

[https://cra.link/deployment](https://cra.link/deployment)

### R1D15

`npm audit`, —> `npm audit fix —force` or `npm update`

```jsx
componentDidCatch () {
	this.setState....
}
```

```jsx
if (true) {
  throw new Error('Nooooooo!');
}
// put it in places where we need to throw an error to check
//if boundaries work
```

[Deployment | Create React App](https://create-react-app.dev/docs/deployment/#github-pages)

### R1D16 & D17

**Client-Server Protocol**

Request →HTTP methods:

- GET
- POST
- PUT
- DELETE

Response →HTTP Status Messages and/or Data (HTML, CSS, JS)

Ways to send data (eg form) : a) query strings[GET] b)body[POST]

HTTPS layer encrypted with TLS or SSL, always use it for sensitive data sent to server

JSON : easier to mount because it is an object, smaller size due to less tags (compared to XML)

json.stringify(user) <-> json.parse(user) encode-decode to json so that machine understands the contents of the object sent

AJAX - update a webpage without reloading the page, and does it on the background while the user interacts with the page

fetch (promises) .then returns the response

PROMISES(ES6 Feature) : replaces CALLBACKS —(the pyramid of doom)

### R1D18

Async/Await and inside try-catch blocks for exceptions

### R1D19

Reviewed JS from EloquentJS books and made a plan for future projects

### R1D20

**ES9**

- Object spread operator ... ( we used to be able to this with arrays already in ES6 but now we can do it with objects )
- .finally a final block of functionality in a promise declaration, after .then and .catch that runs no matter what!
- **for await of** - //In this case, for-await takes each item from the array and waits for it to resolve. You'll get the first response even if the second response isn't ready yet, but you'll always get the responses in the correct order.

```jsx
const getData2 = async function () {
  const arrayOfPromises = urls.map((url) => fetch(url));
  for (const request of arrayOfPromises) {
    console.log(request);
  }

  for await (const request of arrayOfPromises) {
    const data = await request.json();
    console.log(data);
  }
};
```

- ES2020 allSettled()
- Backend basics

  LAMP stack vs. Application Server (scaling for big applications with load balancer)

  ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/91447a9e-de1d-4d53-afcb-b3a55fb67aa3/Screen_Shot_2020-12-29_at_22.24.20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/91447a9e-de1d-4d53-afcb-b3a55fb67aa3/Screen_Shot_2020-12-29_at_22.24.20.png)

- APIs - API keys to track the charges for API usage, from commercial services, Documentation, JSON standard

### R1D21

Relational databases need to have a defined schema before we start filling in data

NoSQL-Non Relational Databases, we can define it as we go, more flexible

MongoDB is document oriented, uses MongoDB query language

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8527f7b6-50b7-4e82-b9ec-99d376b3135a/Screen_Shot_2020-12-30_at_22.13.13.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8527f7b6-50b7-4e82-b9ec-99d376b3135a/Screen_Shot_2020-12-30_at_22.13.13.png)

### R1D22

New React Project - Color Detection App

1. Create react app CRA
2. List out components in App.js
    1. Navigation
    2. Logo
    3. ImageLinkField
    4. ColorDetection
3. Create components folder
4. npm install tachyons & import 'tachyons' in index.js
5. Start building each component

**Navigation component:**

1. arrow function, returns "HTML" in JSX form
2. don't forget to export default componentName

**Logo Component:**

1. import logo from its source in the project folder
2. use it in the source of the <img>
3. Align Logo and Nav with flexbox

**ImageLink Component(→ for day 23):**

1. Title that prompts user to input image link
2. image field input and button to submit
3. Style them (CSS3 patterns [http://projects.verou.me/css3patterns/](http://projects.verou.me/css3patterns/) )
4. Make button cursor pointer in index.css
5. Change font in index.css
6. particles.js and react-particles.js for background (position fixed, and z-index)
