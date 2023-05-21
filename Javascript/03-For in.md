## Definición

Los arrays son una estructura de datos que pueden almacenar múltiples valores en una sola variable. El bucle "for-in" es una forma de recorrer y acceder a los valores de un array utilizando una estructura de repetición.

Cuando se usa "for-in" con un array, el bucle iterará sobre cada elemento del array y devolverá el índice o la posición de cada elemento. Esto significa que en cada iteración, el valor del índice se puede utilizar para acceder al elemento correspondiente del array.

`var fruits = ['manzana', 'banana', 'naranja', 'piña'];`

```js
	for (var index in fruits) { console.log(index); }
```

> Es importante tener en cuenta que los bucles `for...in` no garantizan el orden de iteración de las propiedades de un objeto, por lo que no se recomienda utilizarlos para iterar sobre arreglos en JavaScript. En su lugar, se recomienda utilizar los bucles `for` tradicionales o los métodos de los arreglos como `forEach()`, `map()`, `filter()`, entre otros.


## Ejemplo

```js
Array.prototype.myCustomFeature = 'cool'; // Add eature to arrays

var arr = [
	'Ivan',
	'Vala',
	'Karina'
];

for (var prop in arr) {
	console.log(prop + ': ' + arr[prop]);
}

// Use this for arrays
for (var i = 0; i < arr.legth; i++) {

	//TODO
}
```

Se utiliza un bucle for-in para iterar a través de la matriz `arr`. En cada iteración, el bucle asigna el nombre de la propiedad del elemento actual a la variable `prop` y luego imprime la propiedad y su valor correspondiente en la consola del navegador. 

Este tipo de bucle es útil para iterar sobre las propiedades de un objeto, pero no se recomienda su uso para iterar sobre matrices, ya que puede incluir las propiedades personalizadas agregadas al prototipo de la clase.