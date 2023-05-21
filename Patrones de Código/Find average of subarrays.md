Given array, find the average of all subarrrays K contigous elements.

#### Brute Force Algorithm
Input: Array = [1, 3, 2, 6, -1, 4, 1, 8, 2], K=5
Output: [2.2, 2.8, 2.4, 3.6, 2.8]

```js
function findAverageSubArrays(array, k) {
	const result = []
	// Itera por cada elemento que llegue hasta el elemento K
	for (let i = 0; i < array.length - k + 1; i++) {
		let sum = 0.0;
		for (let j = i; j < i + k; j++) {
			sum += array[j];
		}
		result.push(sum / k)
	}
	return result;
}
//export default findAverageSubArrays;
module.exports = findAverageSubArrays;
```

#### Time complexity
Since for every element of the input array, we are calculating the sum of its next ‘K’ elements, the time complexity of the above algorithm will be 

$$O(N*K)$$
$$O(N∗K)$$
>where **‘N’** is the number of elements in the input array.
  

#### Sliding Window

```js
function slidingWindowfindAverageSubArrays(array, k) {
	const result = [];
	let windowSum = 0.0;
	let windowStart = 0;
  
	for (let windowEnd = 0; windowEnd < array.length; windowEnd++) {
		windowSum += array[windowEnd];
		// console.log(windowSum)
		if (windowEnd >= k - 1) {
			console.log(array[windowEnd])
			// calculate the average
			result.push(windowSum / k); 
			// subtract the element going out
			windowSum -= array[windowStart]; 
			// slide the window ahead
			windowStart += 1
		}
	}
	console.log(result)
	return result;
}

slidingWindowfindAverageSubArrays([1, 3, 2, 6, -1, 4, 1, 8, 2], 5)

module.exports = slidingWindowfindAverageSubArrays;
```


#### Generate parenthesis

```js
const generateParenthesis = (string) => {

	let result = [];
	let helper = (str, left, right) => {
		if (left === 0 && right === 0) {
			result.push(str);
			return;
		}

		if (left > 0) {
			helper(str + '(', left - 1, right);
		}

		if (right > left) {
			helper(str + ')', left, right - 1);
		}
	}
	helper('', string.length, string.length);
	return result;
}

console.log(generateParenthesis('><><<>><'))
```