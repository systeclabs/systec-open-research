```js
/* FIRST CLASS FUNCTIONS

* Javascript is not the only lang with first class functions

* Everything that you can do with other types:

* Objects.

* Strings,

* Numbers,

* Booleans

*

* You can do with FUNCTIONS:

* Assign variables that have a value that is a function

* Pass functions around as params to other functions

* Can create functions on the fly

*

* 'Function' is a special type of object

*

* CHANGE THE WAY YOU CAN PROGRAM!

*/

console.log(Function);

console.log(Function.name);

console.log(Function.code);

  

function greet() {

console.log('hi');

}

greet.language = 'english'; // custom property created

console.log(greet);

console.log(greet.language);

console.log(greet.name) // get name property

  

greet(); // executes code
```