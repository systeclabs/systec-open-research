## Definición

Un array es una colección ordenada de elementos. Imagina que tienes un cajón lleno de pelotas de diferentes colores. Cada pelota es un elemento y el cajón es un array. Puedes contar cuántas pelotas tienes y puedes elegir cuál de ellas quieres sacar primero, porque están ordenadas.

En el caso de los arrays en JavaScript, se pueden almacenar diferentes tipos de datos, como números, palabras y objetos. También puedes acceder a los elementos dentro del array usando su posición, llamada índice. El primer elemento en un array tiene un índice de 0, el segundo tiene un índice de 1, y así sucesivamente.

Puedes agregar nuevos elementos a un array en cualquier momento y también puedes eliminar elementos existentes. Los arrays son útiles para almacenar datos que necesitan ser organizados en un orden específico, como una lista de nombres o una serie de números.

## Ejemplo 

```js
let arr = [
	1,
	false,
	{
		name: 'Lucy',
		address: '111 Main St'
	},
	function(name){
		var greeting = 'Hello '
		console.log(greeting + name);
	}
];

console.log(arr);
arr[3](arr[2].name);
```

## Explicación

1.  En la primera línea, declaramos una variable llamada "arr" y le asignamos un array de varios elementos, incluyendo un número, un valor booleano, un objeto con dos propiedades ("name" y "address"), y una función.
    
2.  En la segunda línea, usamos la función "console.log" para imprimir el contenido de la variable "arr" en la consola del navegador.
    
3.  En la tercera línea, accedemos al cuarto elemento del array "arr" (que es una función) usando la sintaxis de corchetes "[3]".
    
4.  Después de eso, llamamos a la función accedida en el paso anterior usando la sintaxis de paréntesis "()". Además, le pasamos como argumento el valor de la propiedad "name" del tercer elemento del array "arr" (que es un objeto), accedido con la sintaxis de corchetes "[2].name".