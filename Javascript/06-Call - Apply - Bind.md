```js
/* Control 'this' value for each Execution Context
* Functions can have properties and methods
* Access to a: call(), apply() and bind() method
* This have to be with the 'this' variable
* and arguments you pass to the function
*/

var person = {
	firstname: 'Ivan',
	lastname: 'Dong',
	getFullName: function(){
		var fullname = this.firstname + ' ' + this.lastname;
		return fullname;
	}
}

var logName = function(lang1, lang2) {
	console.log('Logged:' + this.getFullName() );
	console.log('Arguments: ' + lang1 + ' ' + lang2);
	console.log('==================')
}

// REMEMBER!: 'this' is a function object (it has properties and methods)

var logPersonName = logName.bind(person) // bind 'this' to the passed object

logPersonName('en'); // logName is expecting arguments for languages

  

// CALL method: bind the object for 'this'
// and pass your parameters
logName.call(person, 'en', 'es');


// APPLY == CALL != Wants array of parameters
logName.apply(person, ['es', 'en']);

  
// CREATE FUNCTION ON THE FLY an invoke it!
(function(lang1, lang2) {
	console.log('Logged:' + this.getFullName() );
	console.log('Arguments: ' + lang1 + ' ' + lang2);
	console.log('==================')
}).apply(person, ['en', 'es']);


// FUNCTIONS BORROWING
var person2 = {
	firstname: 'Jane',
	lastname: 'Doe'
}
console.log(person.getFullName.apply(person2));

/* FUNCTION CURRYING

* With bind you create a new copy of the function

*/

function multiply(a, b){
	return a * b
}
 
// CURRYING: Creating copy of a function with preset parameters
var multiplyByTwo = multiply.bind(this, 2); // 2 is the first paremeter (a)
console.log(multiplyByTwo(4)); // 4 is the second parameter (b)

var multiplyByTwo = multiply.bind(this, 2, 3); // 2 is the first paremeter (a) and 3 is the second one (b)
console.log(multiplyByTwo()); // 6 (2 * 3)

var multiplyByThree = multiply.bind(this, 3); // 3 is the first paremeter (a)
console.log(multiplyByThree(2));
```
