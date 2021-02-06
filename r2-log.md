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
