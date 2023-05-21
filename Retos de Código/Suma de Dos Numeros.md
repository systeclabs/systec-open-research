### Two Number Sum

Escribe una función que reciba una lista de números enteros diferentes y no vacía, y un número entero que representa la suma objetivo. Si cualquier par de números en la lista suman la suma objetivo, la función debe devolverlos en una lista, en cualquier orden. Si no hay ningún par de números que sumen la suma objetivo, la función debe devolver una lista vacía.

```js
function twoNumberSum(array, targetSum) {
  const seenNumbers = new Set();
  for (let num of array) {
    const complement = targetSum - num;
    if (seenNumbers.has(complement)) {
      return [num, complement];
    }
    seenNumbers.add(num);
  }
  return [];
}
// Do not edit the line below.
exports.twoNumberSum = twoNumberSum;
```