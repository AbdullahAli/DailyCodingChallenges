Daily Coding Problem: Problem #1

Good morning! Here's your coding interview problem for today.

This problem was recently asked by Google.

Given a list of `numbers` and a number `k`, return whether any two `numbers` from the list add up to `k`.

For example, given `[10, 15, 3, 7]` and `k` of `17`, return true since `10 + 7` is `17`.

Bonus: Can you do this in one pass?

Solution:

Time complexity o(n): since we are passing through the array once and are doing an additional constant look up in the hash o(1)

Space complexity o(n): since we can store the whole array in the hash 'seen'

```javascript
function containsPairWithSum(numbers, k) {
	const seen = {};

	for(currentNumber of numbers) {
		const numberNeeded = k - currentNumber;

		if(seen[numberNeeded]) {
			console.log(`Found! ${currentNumber}+${numberNeeded}=${k}`);
			return true;
		} else {
			seen[currentNumber] = true;
		}
	}

	return false;
}

console.log(containsPairWithSum([10, 15, 3, 7], 17));
```

---
Daily Coding Problem: Problem #2

Good morning! Here's your coding interview problem for today.

This problem was asked by Uber.

Given an `array` of integers, return a new `array` such that each element at index `i` of the new array is the product of all the numbers in the original array except the one at `i`.

For example, if our input was `[1, 2, 3, 4, 5]`, the expected output would be `[120, 60, 40, 30, 24]`. If our input was `[3, 2, 1]`, the expected output would be `[2, 3, 6]`.

Follow-up: what if you can't use division?

Solution:

Time complexity o(n): since we are passing through the array once to calculate the total product.  Then a secondary pass of the array to divide by the current number, so o(2n), which is o(n)

Space complexity o(n): since the question required us to return a new array

```javascript
const numbers = [1, 2, 3, 4, 5];
const totalProduct = numbers.reduce((currentTotal, num) => currentTotal * num);
const products = [];

numbers.forEach(number => products.push(totalProduct/number));

console.log(products);
```

If we were not required to return a new array, we can modify the input array to achieve a o(1) space complexity

```javascript
const numbers = [1, 2, 3, 4, 5];
const totalProduct = numbers.reduce((currentTotal, num) => currentTotal * num);

for (let i = 0; i < numbers.length; i++) {
	numbers[i] = totalProduct / numbers[i];
}

console.log(numbers);
```

>Follow-up: what if you can't use division?

Time complexity o(n): since we are passing through the array twice

Space complexity o(n): since we are storing an array of the products which are the same length as that of the input array

```javascript
const numbers = [1, 2, 3, 4, 5];
const products = [];

let p = 1;
for(let i = 0; i < numbers.length; i++) {
	products[i] = p;
	p *= numbers[i];
}

let q = 1;
for (let i = numbers.length -1; i >= 0; i--) {
	products[i] *= q;
	q *= numbers[i];
}

console.log(products);
```
---