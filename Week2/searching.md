# Linear and binary search

## Objective
Understand the working of linear and binary search algorithms

## Task
1. How many steps would it take to perform a linear search for the number 8 in the ordered array, [2, 4, 6, 8, 10, 12, 13]? - **1 pt**

In this scenario, linear search would take 4 operations since the number 8 is the fourth element in the array. In worst case analysis, linear search would be an O(n) operation since the target element could be the very last element of the array.  

2. How many steps would binary search take for the previous example? - **1 pt**

In this scenario, binary search would take 1 operation since the number 8 located at index 3 which is the midpoint of the array: (floor((0 + 6) / 2) = 3). In general, binary serach would take O(log_n) operations since it cuts the search space in half with every iteration.

3. What is the maximum number of steps it would take to perform a binary search on an array of size 100,000? - **1 pt**

At most, it would take 17 operations to perform binary search on an array of size 100,000.  log_2(100,000) = 16.61 -> 17 (cannot have partial operation so we round up).
  
5. Write a C++ code that implements the linear and binary search algorithms. The algorithm should be able to calculate the number of steps against the given search. - **7 pts**

