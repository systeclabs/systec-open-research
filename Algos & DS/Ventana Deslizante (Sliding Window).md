202207120039
Estado: #idea
Tags: #patrones #algoritmos 

# Ventana Deslizante (Sliding Window)

## Descripción
Es [[Ventana Deslizante (Sliding Window) |patrón de código|]]. Imagina una ventana con una anchura en especifico. Al mover la ventana manteniendo su anchura en un [[Arrays |array|]] debemos notar que un elemento sale y otro entra. Restando y sumando al total respectivamente.

## Elementos claves
- [[Representación visual Ventana Deslizante - ]]: Smallest contigous subarray.

## Pasos

1. Sumar los elementos desde el principio del array hasta que la suma sea igual lo mayor a 'S'
2. Estos elementos constituyen nuestra ventana deslizante y mantendremos registro de el lehgth de la ventana como si fuera la ventana mas pequeña (por el momento).
3. Deslizar la ventana agregando un elemento. `(+=)`
4. Ecogemos la ventana hasta que la suma de la ventana sea menor a 'S' de nuevo.
	1. Verifica si el length actual de la ventana es la menor hasta el momento, si es asi: **recuerda el length**
	2. Restar el primer elemento de la ventana

## Ejemplos

> Given an array of positive integers and a number ‘S,’  find the length of the **smallest contiguous subarray** *whose sum is* **greater than or equal to ‘S’**. Return 0 if no such subarray exists.

**Input:** [2, 1, 5, 2, 8], S=7  
**Output:** 1  
**Explanation:** The smallest subarray with a sum greater than or equal to ‘7’ is [8].


## Implementación

```js
const smallestSubArraySum = (s, arr) => {
	let windowSum = 0.0, // 2
		window
	for (let i = 0; i >= arr.length; i++) {
		windowSum += arr[i];
		if (windowSum >= s) {
			return i;
		}
	}

	return -1
}

console.log(smallestSubArraySum(7, [2, 1, 5, 2, 3, 2]));

```

---
## Referencias
- [Smallest Subarray With a Greater Sum (easy) - Grokking the Coding Interview: Patterns for Coding Questions (educative.io)](https://www.educative.io/courses/grokking-the-coding-interview/7XMlMEQPnnQ)