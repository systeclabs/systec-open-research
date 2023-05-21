Los argumentos en JavaScript son valores que se pasan a una función cuando se la llama. Son valores o variables que se le pasan a la función para que la utilice en su cuerpo y realice alguna tarea.

Por ejemplo, si tenemos una función que suma dos números, los números que se van a sumar son los argumentos. Podemos llamar a la función y pasarle los argumentos de la siguiente manera:

```js
function sum(a, b) { 
	return a + b; 
} 

console.log(sum(2, 3)); // Devuelve 5
```

En este ejemplo, la función "sum" tiene dos argumentos, "a" y "b", y cuando llamamos a la función, le pasamos los valores 2 y 3 como argumentos. La función realiza la suma y devuelve el resultado. Los argumentos son muy útiles porque nos permiten hacer que una función sea más flexible y reutilizable para diferentes casos de uso.

```js
function greet(firstName, lastName, language) {
	language = language || 'en';
	
	if (arguments.length === 0) {
		console.log('Missing parameters');
		console.log('-----------------');
		return;
	}
	
	if (language === 'en') {
		console.log('Hello', firstName + ' ' lastName);
	}
	
	if (language === 'es') {
		console.log('Hola', firstName + ' ' lastName);
	}
	
	console.log(firstName);
	console.log(lastName);
	console.log(language);
	console.log(arguments);
	console.log('arg 0:', arguments[0]);
	console.log('========================');
}

greet();
greet('Ivan');
greet('Ivan', 'Dong');
greet('Ivan', 'Dong', 'es');
greet('John', 'Doe', 'en');
```

1. La función "greet" en JavaScript acepta tres argumentos: "firstName", "lastName" y "language".
2. El valor por defecto de "language" es "en".
3. Se revisa si no se han proporcionado argumentos usando "arguments.length".
4. La función saluda en inglés o español según el idioma proporcionado.
5. La función imprime detalles de cada llamada usando "console.log".
6. Los argumentos en JavaScript son valores o variables pasados a una función al llamarla.
7. Los argumentos se utilizan en el cuerpo de la función para realizar diferentes tareas.