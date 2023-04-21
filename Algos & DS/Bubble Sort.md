Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.

```js
function bubbleSort(array) {
	for (var i = array.length; i > 0; i--) {
		for (var j = 0; j < i; j++) {
			if (array[j] > array[j + 1]) {
				var temp = array[j];				
				array[j] = array[j + 1];
				array[j + 1] = temp;
			}
		}
	}
	return array;
}

bubbleSort([6000, 34, 203, 3, 746, 200, 984, 198, 764, 9, 1]); // [1, 3, 9, 34, 198, 200, 203, 746, 764, 984, 6000]
```