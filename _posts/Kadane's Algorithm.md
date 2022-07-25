---
category: algorithms
---

# Kadane's Algorithm
This algorithm is used for finding the min/max sum of subarrays given an array in O(N) where N is the size of the given array.
With some additional variables it can also find the subarray itself.

###### Implementation
- Max sum
```
tempSum = 0, maxSum = INT_MIN
for (element : array) {
	tempSum += element
	maxSum = max(maxSum, tempSum)
	tempSum = max(tempSum, 0)
}
```

- Min sum
```
tempSum = 0, minSum = INT_MAX
for (element : array) {
	tempSum += element
	minSum = min(minSum, tempSum)
	tempSum = min(tempSum, 0)
}
```

- Find subarray
```
tempSum = 0, maxSum = INT_MIN, maxSumIndx, tempIndx, len, tempLen
for (i = 0; i < array.size; i++) {
	tempSum += array[i]
	len++
	if (maxSum < tempSum)
		maxSum = tempSum, maxSumIndx = tempIndx, len = tempLen
	if (tempSum < 0)
		tempSum = 0, tempIndex = i + 1, len = 0
}

```

###### Explanation
- Whether searching for min/max sum, one variable keeps the answer and the other variable is a temporary sum of the potential subarray. For each step, answer is updated by comparing with temporary sum.
- When searching for max sum in an all-negative array, this algorithm will find the biggest negative element.
- To find the actual subarray, additional variables to keep in track of the best subarray and the temporary subarray can be used.