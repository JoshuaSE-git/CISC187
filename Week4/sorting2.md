# Sorting algorithms

## Objective
Understand the working of insertion sort algorithm algorithms and evaluate the algorithm's efficiency.

## Task
1. Proof that, under the average-case scenario, the insertion sort has a time complexity of $O(N^2)$. Draw a clear figure and show all the operations clearly.  **2 pts **

Insertion sort works by maintaining a sorted array at every iteration through the array.  For example, at the first iteration, insertion sort ensures the first two elements are sorted.  At the next iteration, it makes sure that the first 3 elements are sorted.  In the best case scenario, the array is already sorted, so each resorting operation is constant O(1).  In the worst case scenario, the array is in reverse order, making every resort take k operations where k is the current index. In the average-case scneario, the cost of resorting the array is k/2 where k is the current index.  This is because the resorting operation works by iterating backwards through the array in order to correctly place the current element.

Average-case scenario
$(1/2)(1 + 2 + 3 ... + (N-1)) = (N^2 - N)/4 -> O(N^2)$

2. At the start of the insertion sort, the index of the inspected value is set to 1. Change the index of the inspected value and verify that the total number of operations equals 20. Consider the worst-case scenario. Use N=5, where N is the number of elements.  **4 pts**

In the worst-case scenario the array is in reverse order.  If we were to start the index at 0, that would mean the first iteration would have 0 operations since there are no previous elements to compare with.

Step-by-step:

Case 1: Inspect index 0

- Nothing to compare (only one element).

- Operations: 0

Case 2: Inspect index 1

- Compare with index 0 → 1 comparison.

- Shift 1 element → 1 shift.

- Operations: 2

Case 3: Inspect index 2

- Compare with indices 1 and 0 → 2 comparisons.

- Shift 2 elements → 2 shifts.

- Operations: 4

Case 4: Inspect index 3

- Compare with indices 2, 1, 0 → 3 comparisons.

- Shift 3 elements → 3 shifts.

- Operations: 6

Case 5: Inspect index 4

- Compare with indices 3, 2, 1, 0 → 4 comparisons.

- Shift 4 elements → 4 shifts.

- Operations: 8

Total Operations: 20

3. The following function returns whether or not a capital “X” is present within a string.  **4 pt**

```
function containsX(string) {
	foundX = false;
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			foundX = true; 
		}
	}
	return foundX; 
}
```

(a) What is this function’s time complexity regarding Big O Notation?

O(n) where n is the number of characters in the string.

(b) Then, modify the code to improve the algorithm’s efficiency for best- and average-case scenarios.

In the best case scenario, the string has an 'X' in the first position.  Instead of using a flag to mark if 'X' is found, we can implement an early return if 'X' is detected.  The early return would also help the average-case scenario since the function would return half-way through the loop as opposed to after all iterations.

```
function containsX(string) {
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			return true; 
		}
	}
	return false;
}
```
