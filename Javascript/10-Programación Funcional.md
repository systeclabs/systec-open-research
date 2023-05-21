```js
/* FUNCTIONAL PROGRAMMING LANGUAGES:
* pass it as parameters
* return it from functions
* THINK AND CODE IN TERMS OF FUNCTIONS
*/

  

var arr1 = [1,2,3];

console.log(arr1);

  

// create a new array out of this new array

var arr2 = [];

// loop all items of the array

for (var i=0; i < arr1.length; i++) {

  

arr2.push(arr1[i] * 2);

// double value of its equivalent item in the first array

  

}

  

console.log(arr2);

  
  

// MINIMIZE CODE AND LIMIT REPETITION

  
  

function mapForEach(arr, fn){

  

var newArr = [];

  

for (var i=0; i < arr2.length; i++) {

newArr.push(

fn(arr[i]) // pass array to this function for each item of the array

)

}

  

return newArr;

  

};

  
  

var arr2 = mapForEach(arr1, function(item) { // passing a function as a parameter

  

return item * 2

  

});

  

var arr3 = mapForEach(arr1, function(item){

return item < 2;

})

  

var arr4 = mapForEach(arr1, function(item){

return item + 1;

})

  

console.log(arr2);

console.log(arr3);

console.log(arr4);

  

var checkPastLimit = function(limiter, item) {

return item < limiter;

} // this is the same as line 51 var arr4 function

var arr5 = mapForEach(arr1, checkPastLimit.bind(this, 2)); // set 1st parameter to a 2

console.log(arr5);

  

// just pass the limiter

var checkPastLimitSimplified = function(limiter) {

return function(limiter, item) {

return item < limiter;

}.bind(this, limiter)

}

  

var arr6 = mapForEach(arr1, checkPastLimitSimplified(1));

console.log(arr6);

  

var arr7 = _.map(arr1, function(item){ // underscore library

return item * 3;

})

console.log(arr7);

  

var arr8 = _.filter([2,3,4,5,6,7], function(item){

return item % 2 === 0;

})

console.log(arr8);
```