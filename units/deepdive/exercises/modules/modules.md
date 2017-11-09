# NodeJS Modules: Imports and Exports - Exercises

## Setup

- Create a new folder.
- Add a `main.js` file to the folder.

### Math Module

- Add a `math-module.js` file to your folder
- In the `math-module.js` file add a function called `sum`. The `sum` function should take two arguments and return their sum.

Example:

```js
sum(3, 6); //returns 9
```

- Add a `module.exports` statement at the bottom of the `math-module.js` file.
- Add the `sum` function to `module.exports`.
- In the `main.js` file, use the `require` keyword to import the `math-module.js` file.
- Call the `sum` function from the `main.js` file and save the result to a new variable.
- Add a `console.log` statement that logs the saved variable.
- Open the terminal and run the `main.js` file. You should see the output from the `sum` function
- Add three more functions to the `math.module.js` file:
1. A `multiply` function (takes two arguments and returns their product).
2. A `divide` function (takes two arguments and returns the first argument divided by the second).
3. A `square` function (takes one argument and returns its square).

Examples:

```js
multiply(2, 5); //returns 10
divide(20, 10); //returns 2
square(5); //returns 25
```

- Add the `multiply`, `divide`, and `square` functions to `module.exports` in the `math-module.js` file.
- In the `main.js` file, use the use the imported `math-module.js` file to call the three new functions, and save the results as new variables
- Log the saved variable.
- Open the terminal and run the `main.js` file. You should see the output from all the functions.

### String Module

- Create a new file called `strings-module` that contains at least three string functions (for example: return the first letter of a string, reverse a string, etc.) of the choosing.
- Import the `string-module` into the `main.js` file and try calling and logging the functions from `string-module`.
- Can you also import the `string-module` into the `math-module` and use it in there? Or vice versa?

### Modular: Files By Extension

The following is a code for an program that takes a user's input of a folder and an extension, and lists all the files in that folder that have the given extension.

```js
const fs = require('fs')
const path = require('path')

const folder = process.argv[2]
const ext = '.' + process.argv[3]

fs.readdir(folder, function (err, files) {
  if (err) return console.error(err)
  files.forEach(function (file) {
    if (path.extname(file) === ext) {
      console.log(file)
    }
  })
})
```

In a new folder, create the files `filterFiles.js` and `main.js`. 

1. Paste the above code into `filterFiles.js` and rewrite it as follows:

- Do not take any input from the user (i.e. remove lines that make use of the `process` object).
- Wrap the code in a function that takes as arguments a folder name, an extension, and a callback function.
- If there is an error while reading the folder, invoke the callback with the error.
- Otherwise, invoke the callback at the bottom of the function with two arguments: `null` and the list of files.
- Export the function using `module.exports`.

2. In `main.js` do the following:

- Import the function from `filterFiles.js` as `filterFilesFn`.
- Read the input for folder and extension from the user (using the `process` object).
- invoke the function with the following arguments:
  - the folder
  - the extension
  - a callback function that takes as arguments an error object and a list. If the error object is not `null`, it logs the string: `'there was an error'` followed by the erro. Otherwise, it loges the list, with each element in a separate line. 

### Challenge: Create a Module

Create a module with functions that you think would be useful to have when building various different apps. Try to think of functions that you find yourself using in different exercises, projects, code wars problems, etc. For example, would a `createRandomNumber` function be useful to have in multiple different apps?What about an `sumAll` function that returns the sum of all the numbers in an array.

#### Example

Here's an example of the beggining of a 'useful array methods' module. The goal would be to continue adding a bunch of other useful array methods (that don't already exist in JavaScript) to this module, so we could easily import them all into any of our projects.

'Useful array methods' is an example of a theme for a module, but you could choose any theme that you think would be personally useful.

```js
module.exports = {
  // returns the first element of the array
  head: function(arr){
    return arr[0];
  }
  // returns the array minus the first item
  tail: function(arr) {
    return arr.slice(1);
  },
  // returns the sum of a all the numbers in an array
  sumAll: function(arr) {
    return arr.filter(elem => typeof elem === "number")
              .reduce((sum, curr) => sum + curr, 0)
  }
  // returns a random value from the array
  randomElem: function(arr) {
    return arr[Math.floor(Math.random() * arr.length)];
  }
}
```

#### Test it

Try importing your module into some of your other projects. Can you successfully use your module functions with your pre-existing code?