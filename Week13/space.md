# Space constraints

## Objective
How to write a space-efficient code	

## Tasks
The following exercises provide you with the opportunity to practice with space constraints.

1. Following is the 'Word Builder' algorithm. Describe its space complexity in terms of Big O.

```
function wordBuilder(array) { 
		let collection = [];
		for(let i = 0; i < array.length; i++) { 
				for(let j = 0; j < array.length; j++) {
						if (i !== j) {
								collection.push(array[i] + array[j]);
						}
				}
		}
		return collection; 
}
```

The space complexity of this algorithm will be O(n^2) since each string in the array is concatenated with every other string and then added to the collection.

2. Following is a function that reverses an array. Describe its *space* complexity in terms of Big O:

```
function reverse(array) { 
		let newArray = [];
		for (let i = array.length - 1; i >= 0; i--) { 
				newArray.push(array[i]);
		}
		return newArray;
}
```

The space complexity of this algorithm will be O(n) since the output array will always be the same length as the input array.

3. Create a new function to reverse an array that takes up just $O(1)$ extra space.

```
function reverse(array) {
    let l = 0 
		for (let r = array.length - 1; r > l; r--) { 
				temp = array[r];
        array[r] = array[l];
        array[l] = temp;
        l++;
		}
    return array;
}
```

This algorithm does in-place reversal, making the space complexity O(1).

4. Following are three different implementations of a function that accepts an array of numbers and returns an array containing those numbers multiplied by 2. For example, if the input is [5, 4, 3, 2, 1], the output will be [10, 8, 6, 4, 2].

````
function doubleArray1(array) { 
	let newArray = [];

	for(let i = 0; i < array.length; i++) { 
		newArray.push(array[i] * 2);
	}
	return newArray; 
}


function doubleArray2(array) {
	for(let i = 0; i < array.length; i++) {
  	array[i] *= 2;
  }
	return array; 
}


function doubleArray3(array, index=0) { 
	if (index >= array.length) { return; }
  array[index] *= 2;
  doubleArray3(array, index + 1);
	return array; 
}
````

Fill in the table that follows to describe the efficiency of these three versions in terms of both time and space:

| Version    | Time complexity | Space complexity |
| ---------- | --------------- | ---------------- |
| Version #1 | O(n)            | O(n)             |
| Version #2 | O(n)            | O(1)             |
| Version #3 | O(n)            | O(n)             |
