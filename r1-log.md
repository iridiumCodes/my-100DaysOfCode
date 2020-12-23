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
