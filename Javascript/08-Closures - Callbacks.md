```js
function sayHiLater(time) {

  

var greeting = 'Hi';

  

setTimeout(function(){

  

console.log(greeting);

  

}, time)

} //END: sayHiLater()

  

sayHiLater(5000); // seconds later still have access to greeting variale

  

/* CLOSURES !

* Callback function: Function you give to another

* function to be run when the other function is finished

* It callsback with the function you gave

*/

  

function tellMeWhenDone(callback) {

  

var a = 1000; // some work

var b = 2000; // some work

  

callback(); // the 'callback', it runs the function t give it!

  

}

  
  

// give this functions to your other function:

tellMeWhenDone(function(){

console.log('I am done');

});

  

tellMeWhenDone(function(){

console.log('I am done again');

});
```