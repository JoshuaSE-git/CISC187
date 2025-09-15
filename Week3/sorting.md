# Sorting algorithms

https://www.youtube.com/watch?v=lzGfcwxbexw

## Objective
Understand the working of sorting algorithms and evaluate the efficiency of the algorithm

## Task
1. Use Big O Notation to describe the time complexity of an algorithm that takes $4N + 16 steps.$- **1 pt**

**In Big O notation, $4N + 16$ would reduce to $O(n)$**.

- As N goes to infinity, the constants drop off, meaning they become obsolete.

2. Use Big O Notation to describe the time complexity of an algorithm that takes $2N^2$. **1 pt**

**In Big O notation, $2N^2$ would reduce to $O(n^2)$**.

- As N goes to infinity, the constants drop off, meaning they become obsolete.

3. Use Big O Notation to describe the time complexity of the following function, which returns the sum of all numbers of an array after the numbers have been doubled: - **2 pt**

**The time complexity of the algorithm is $O(n)$**.

- Although there are two loops, they are not nested. This means their relationship is additiive ($n + n = 2n$) instead of multiplicative ($n * n = n^2$).

```
def double_then_sum(array) 
	doubled_array = []

	array.each do |number| 
		doubled_array << number *= 2
	end

	sum = 0

	doubled_array.each do |number| 
		sum += number
	end
	return sum 
end

```

4. Use Big O Notation to describe the time complexity of the following function, which accepts an array of strings and prints each string in multiple cases: - **2 pts**

**The time complexity is $O(n)$**.

- Although there are three operations inside the loop body, each of them is constant.  This means the "bottleneck" of the algorithm is the input size (N).

```
def multiple_cases(array) 
	array.each do |string|
		puts string.upcase 
		puts string.downcase 
		puts string.capitalize
	end 
end
```

5. The next function iterates over an array of numbers, and for each number whose index is even, it prints the sum of that number plus every number in the array. What is this function’s efficiency in terms of Big O Notation? - **4 pts**

**The time complexity is $O(n^2)$**.

- The inner loop only executes on even indices of the outer loop, which makes the inner loop execute $n/2$ times.  In each inner loop execution, every other element of the input array gets processed, which means the inner loop body gets executed n times.  Overall, this means the algorithm takes approximately $(n^2)/2$ operations.  As N goes to infinity, the constant $1/2$ drops off, making the time complexity $O(n^2)$

```
def every_other(array) 
	array.each_with_index do |number, index|
		if index.even?
			array.each do |other_number|
            	puts number + other_number
			end 
		end
	end 
end
```
