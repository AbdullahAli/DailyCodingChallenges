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