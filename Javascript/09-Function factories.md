```js
function makeGreeting(language){

  

//passing language to outer function

//gets trapped in the closure

  

return function(firstname, lastname) {

  

if (language === 'en') {

console.log('Hello ' + firstname + ' ' + lastname);

}

  

if (language === 'es') {

console.log('Hola ' + firstname + ' ' + lastname);

}

  

}

  

}//END: makeGreeting

  

var greetEnglish = makeGreeting('en'); // closure points to language = 'en'

var greetSpanish = makeGreeting('es');

  

greetEnglish('Ivan', 'Martz');

greetSpanish('Dong', 'Zored');
```