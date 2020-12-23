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
