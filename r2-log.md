# #100DaysOfCode Log - Round 2 - [Iris Diakoumi]

## Log

The log of my #100DaysOfCode challenge. Started on [January 8, Friday, 2020]. This is a fresh start. Last round I couldn't complete the daily streak due to unforeseen circumstance, so I'm starting a new iteration!

## R2D0

**Project ColorDetection steps:**

1. Create react app
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

**ImageLink Component(→ for day 1):**

1. Title that prompts user to input image link
2. image field input and button to submit
3. Style them (CSS3 patterns [http://projects.verou.me/css3patterns/](http://projects.verou.me/css3patterns/) )
4. Make button cursor pointer in index.css
5. Change font in index.css
6. particles.js and react-particles.js for background (position fixed, and z-index)

### R2D1

I'm currently building a React app that will detect dominant colors in an image the user uploads. Plan is to have proper authentication, user profile and possibly an archive of the user's saved color palettes. Progress so far:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a057c2b-50e7-4a67-8719-8dc5d6b21af7/Screen_Shot_2021-01-08_at_23.35.40.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a057c2b-50e7-4a67-8719-8dc5d6b21af7/Screen_Shot_2021-01-08_at_23.35.40.png)

Things done today:

- [x] Title that prompts user to input image link
- [x] image field input and button to submit
- [x] Style them (https://www.svgbackgrounds.com/)

(#CC5577 —> #9A96EE gradient)

- [x] Make button cursor pointer in index.css
- [x] Change font in index.css
- [x] particles.js and react-particles.js for background (position fixed, and z-index)

(did an alternative with little bubbles). I'll be playing with the Clarifai API tomorrow

## R2D2

Good news.. The Clarifai API has deprecated their javascript API. In the past 3 days... Awesome! (Cries in code). For the moment I'll continue as planned and in the next iteration I will switch to the new grpc client. Fingers crossed! Things done today:

- [x] Check responsive (submit is out of margin)
- [x] Detect Input change on textfield
- [x] Detect button click
- [x] Sign up for Clarifai API Key
- [x] Setup inside App.js
- [x] Send sample url and receive object response OK

## R2D3

- [x] Worked with API on uploading my own image URL
- [x] Showing images uploaded below the search field
- [x] Planned almost all of my projects for the future weeks
- [x] Done with Week 2 of Agile with Jira Coursera Course

## R2D4

- [x] Add Image URL to State
- [x] update state with input from field
- [x] pass the image URL to the ColorDetection component
- [x] pass image URL as props in the ColorDetection Component
- [x] Use the props as src for image to be displayed in ColorDetection Component
- [x] go through APi response and find hex value for each entry in the array
- [x] use for-each loop in case I want to add a break to set maximum number of values returned
- [x] added labels for name and hex value using template literals
- [x] restrict the size of the image displayed for consistency
- [x] git remote set-url origin new_url (renamed repository, updated the remote url in local repo)

**NOTE about setState():**

Calling `setState()` in React is asynchronous, for various reasons (mainly performance).

Under the covers React will batch multiple calls to `setState()` into a single call, and then re-render the component a single time, rather than re-rendering for every state change.

Therefore the imageUrl parameter would have never worked in our example, because when we called Clarifai with our the predict function, React wasn't finished updating the state.

One way to go around this issue is to use a callback function:`setState(updater, callback)`

[Read about it more here](https://reactjs.org/docs/react-component.html#setstate)

## R2D5 & 6

- [x] Sign in form
- [x] Route switch
  - [x] route state paramenter keeps track of where the user is
  - [x] conditional statement will render components accordingly
  - [x] prop onRouteChange to each component that changes onClick of the components
  - [x] onRouteChange changes the route dynamically depending on which component calls it
  - [x] each component runs an arrowfunction that in turn runs the onRouteChange with a different string(route) as the parameter
- [x] Register form
- [x] Route switch

## R2D7

- [x] Top line of render method, destructure state object for convenience and clarity
- [x] for —> htmlFor
- [x] form —> div for JSON submission
- [x] Node - versions, globalThis, \_\_dirname, ES6 modules (.mjs or package.json with "type": "module")
- [x] nodemon setup inside node server project
- [x] Work with basic node server, expressJS, middleware, Postman, RESTful APIs,
- [x] Node File System Module (readFile, readFileSync, appendFile, writeFile, unlink) - I/O covered

## R2D8

- [x] Add .gitignore for node_modules etc.

  _node_modules_

  _build_

  _npm-debug.log_

  _.env_

  _.DS_Store_

- [x] added type:module in package.json
- [x] tested signin endpoint on Postman (remember to post body raw → JSON) with check of static user object

  ```jsx
  *app*.use(*express*.urlencoded({extended: *false*}));  *//replaces bodyParser package, native functionality
  app*.use(*express*.json());
  ```

## R2D9

- [x] _/profile/:userId --> GET = user OK_
- [x] _/palettes --> PUT = updated user palettes array with an array of colors_
- [x] CORS, BCRYPTJS
- [ ] Connect Front-End with Server → Signin and Register for tomorrow

## R2D10
```jsx
users.sort((a, b) => a.followers < b.followers ? 1 : -1)
```

DRY principle

Unit Testing → Arrange Act Asser Pattern

```jsx
// Unit Test

function reverse(str) {
    // write code here
    let splitString = str.split("")
    let reverseArray = splitString.reverse()
    let joinArray = reverseArray.join("")
    return joinArray
}

/**
* Test Suite 
*/
describe('reverse()', () => {
    it('reverses a word', () => {
        // arrange
        const input = 'burgers'
        
        // act
        const result = reverse(input)
        
        // log
        console.log('result:', result)
        
        // assert
        expect(result).toBe('sregrub')
    })
})
```

ColorDetect Project - smart component for Sign-in and Set State with Email and Password events

## R2D11
- [x]  onChange form event handler, fetch (does a GET by default, make it post)
- [x]  connect signin component with server
- [x]  connect register component with server
- [x]  Do the appropriate route changes
- [x]  Palettes component basic structure ( I need to design the functionality.. for the moment it displays the name and a title for the palettes )
- [x]  PostgreSQL and PSequel installed and setup, SQL refresher

## R2D12
Trying to fix a PostgreSQL error --> createdb: error: could not connect to database template1: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
        
Uninstalling PostgreSQL and reinstalling because apparently this happens when no version is specified during installation.

## R2D13
- [x]  ERROR fixed!
- [x]  tables: users, login, palettes

```sql
CREATE TABLE users (
id serial PRIMARY key,
name VARCHAR(100),
email text UNIQUE NOT NULL,
joined TIMESTAMP NOT NULL
);
```

[8.15. Arrays](https://www.postgresql.org/docs/current/arrays.html)

PSequel decided to stop working — recent open issue in Github, does not render data, like column names and even entries, even though it shows the number of rows in each table

Moving to pgAdmin... NOPE — I will work with psql in the terminal for now

**Install KNEX.js** 

npm install knex

npm install pg

- Do not return error message from json response (eg user with that email already exists). It's a security concern. Instead console.log a custom, less descriptive message

## R2D14
- [x]  Fix undefined name in palettes component after register
- [x]  Palettes Endpoint (inserts array of colors into palettes table
- [x]  Register with corresponding hash for password in the login table
- [x]  Lookup transactions in databases and knex

*"Transactions are an important feature of relational databases, as they allow correct recovery from failures and keep a database consistent even in cases of system failure. All queries within a transaction are executed on the same database connection, and run the entire set of queries as a single unit of work. Any failure will mean the database will rollback any queries executed on that connection to the pre-transaction state."*

- [x]  Sign-in endpoint - check against login table, compare password to hash in order to sign in the user

## R2D15
Work on backend, organize endpoints in controllers

Fix bug - when a user logins after other user that detected an image, clear state to not display that previously used image

Workout a strange thing that happens with modules and import - different syntax for ES6

Dependency injection in imported modules

## R2D16

Endpoints organized in controllers, handling functions with callbacks

## R2D17

- [x]  Validation for register and signin, don't allow empty user to signin or register
- [x]  Allow to return to signin component after register
- [x]  Hide API key — move from client to server, handle API function and endpoint
- [x]  Fetch from client
- [x]  Environment variables

```jsx
console.log(process.env)
```

Set environment in fish:

env PORT='3000' node server.js

- [x]  Be careful to open using `heroku open` for the correct link
- [x]  Connect Database to Heroku

## R2D18
Webflow bootcamp with Dubstech

## R2D19
Webflow site with e-commerce component -- submitted for certificate https://iris-webflow-bootcamp.webflow.io/

## R2D20
Front End Deploy to Heroku

Environment Variable for Clarifai API Key

- [ ]  start script replace with serve -s build (after everything is done)

Log response array to find probability parameter

## R2D21
Rendered swatches by mapping an array of returned values

Heroku push — eslint prettier error is solved by substituting the react start script with 

"start": "serve -s build",

Some styling of the components, but will finish tomorrow

Branching off to incorporate hooks

## R2D22
Learned how to convert a React class component to Functional component

Converted all class components (App, Register, Signin) in my Color Detector app

## R2D23 & R2D24
Fixed Responsive for various device sizes, and fluid resolutions in between - Redesigned components

Added Footer Component

Tweaked some colors for better contrast and UX

## R2D25
CSS Reset by Chris Coyier

```css
html {
  box-sizing: border-box;
  font-size: 100%;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

[Box Sizing | CSS-Tricks](https://css-tricks.com/box-sizing/)

Expenses tracker app - basic setup and Expenses component setup

❗️Always use a **key** property (unique) when using **map** over an array

- [ ]  Add
- [ ]  Edit
- [ ]  Delete
- [ ]  Local Storage

## R2D26
- [x]  Add
- [x]  Edit
- [x]  Delete
- [ ]  Local Storage

**event.preventDefault(); —> Prevents default form submission**

[Using the Effect Hook - React](https://reactjs.org/docs/hooks-effect.html)

If you start editing one user, then try to switch to another user, nothing will happen. Why? Well, the component is already open, and although the state on the parent has changed, it's not registered down to the props.

We want to let the EditUserForm component know the props have changed, which we would have done before with componentDidUpdate.

```jsx
useEffect(() => {
  setUser(props.currentUser)
}, [props])
```

## R2D27
Barebones React App - no CRA, setup from scratch

npm init (to create package.json)

npm install —save packagename

npm install —save-dev packagename for dev dependency

## R2D28
Firebase Setup

Data is stored as documents, which are gathered in collections

Collections: photos, users

Firestore rules

```jsx
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read;
      allow write: if request.auth.uid != null;
    }
  }
}
```

Firebase Authentication: email/password out of the box, email link(passwordless), various social platforms

Import firebase into the application

Firebase Context (rerendering, memoization techniques)

## R2D29
Redux — **Flux** Design Pattern

  + **Middleware between Action and Dispatcher (Redux-logger) to show which actions have been called**

Redux async functions ⇒ Thunk Middleware: Listens for actions that instead of returning an object it returns a function.. Simple Redux doesn't understand a returned function from a reducer.

**Project structure:**

Use folder for each smart component, containing all its logic, styles, and Redux things(constants, actions, reducers)

React ⇒ Component-driven user interfaces

**TOOLS:**

React Router

Lodash (functional library)

Styled-Components

Redux-saga >> Redux-thunk

Immutable.js

Do I really need it? — Added weight, added dependencies that can break in the future

## R2D30
**INITIAL SETUP**

Setup Project Folder Structure

Setup Firebase - Firestore and Authentication (development rules) —> switch to production rules 

```jsx
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read;
      allow write: if request.auth.uid != null;
    }
  }
}
```

Create seed file to populate the data store the first time

Create Firebase Context

Import Firebase Context in index.js

Import relevant Firebase libraries in lib/firebase.js

Add config details from our Firebase Project settings (apiKey, authDomain, etc...)

initializeApp(config) as firebase

Pull FieldValue from Firebase.firestore

Export firebase and FieldValue to use them centrally (in index.js)

Create the Context Provider in index.js with the two imported values mentioned before.

---

**LOGIN PAGE**

We will be redirecting users to pages so we use react-router-dom

Pull from react-router-dom Router, Route, Switch

In order to split up a big bundle into lighter loads, we load the component when it is requested, using lazy from react and Suspense

Create a login.js in pages, and export a dummy Login() function

Suspense provides us with a fallback as we wait for the component to load

---

**ROUTES - CONSTANTS
**

Create constants for routes that will be used in the app

import * as ROUTES to use each route [helpful because VS Code shows the available routes]


## R2D31
SETUP LOGIN PAGE

useHistory hook  from react-router-dom ⇒

useContext hook from react ⇒

useState hook from react ⇒

Basic Validation

useEffect hook from react ⇒ 

SETUP TAILWIND:

dev dependency packages: npm-run-all, postcss, postcss-cli, prop-types, tailwindcss, autoprefixer

tweak the scripts to be:

```jsx
"build:css": "postcss src/styles/tailwind.css -o src/styles/app.css",
"watch:css": "postcss src/styles/tailwind.css -o src/styles/app.css --watch",
"react-scripts:start": "sleep 5 && react-scripts start",
"start": "run-p watch:css react-scripts:start",
"build": "run-s build:css react-scripts:build",
```

**tailwind.css gets compiled to app.css**

Import styles folder into index.js

Config files for tailwind and postcss

Input fields for email and password

## R2D32
Sign In and Sign up Buttons

Tailwind Colors Configuration

HandleLogin function

Sign Up page

TODO: handleSignup function

## R2D33

- [x]  TODO: handleSignup function
- [x]  Pages: Not-found, Dashboard
- [ ]  Components in Dashboard: ~~Header~~, Timeline, Sideboard

Header — use-auth-listener custom hook to listen for when a user logs-in or out

Header layout, check if user is Signed in and show equivalent view

## R2D34
Use gravatar for profile images—!

Sidebar: User - Suggestions

Custom hook (***use-user*** - returns the current user based on uid)

## R2D35
Figma to HTML/CSS Landing Page

- Project setup (repo, sass, live sass compiler, figma file, project folder structure
- Header done
- Responsive header done

## R2D36

- Hamburger icon animation to X, fade in overlay
- Mobile Menu - create markup, css, fade in

## R2D37
Responsive hero (mobile and desktop styles)

Mobile styles: use the two images as background-image in the css, and the phone mockups image as a pseudoelement (::before)

For ::before, rememember to define

- content: ' '
- width, height
- position
- background-size( cover, or you may use percentages)

Create helper classes to manipulate the padding for different axis and sides:

& — pt, &—pb, &—pr, &—pl, &—pall, &—pX, &—pY (X and Y axis)

## R2D38
- EasyBank Landing Page Feature section - typography, responsive styles, padding, layout

## R2D39
-Articles Section
-Fixed overlay to be on top and menu items visible

## R2D40
-Expenses Tracker add Date field and Type select field, clear form after submit
-Easybank Footer - Make logo for dark version by tweaking the path fill property to white - Grid Template Areas - Remove min-height - Replace button opacity effect with overlay by using a pseudoelement ::before
-Merged PR that fixes bottom whitespace
