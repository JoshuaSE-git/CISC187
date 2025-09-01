# Week 1 Assignment - Arrays

https://www.youtube.com/watch?v=31AwMbR9KZc

## Task
1. Explain how to create an array of 100 elements. You can choose any data type of your choice. (requires C++ code) - **1 pts**

To declare a fixed-size array in C++, you write the data type of the array's elements followed by an identifer and the size of the array in brackets.

```cpp
int main(void) {
  int arr[100]; // array of 100 integers

  return 0;
}
```

3. What will be the size of each element of an array. (requires C++ code) - **1 pts**

The size of each element in an array depends on the elements' data type.  In my example, I am using an integer array so each element will have a size of 4 bytes.

```cpp
#include <iostream>

int main(void) {
  int arr[100];

  std::cout << "Size of one element: " << sizeof(arr[0]) << " bytes"
            << std::endl;

  return 0;
}
```

5. For an array containing 100 elements, provide the number of steps the following operations would take: (theoretical) - **6 pts**

- Reading

Reading from an array is a constant time operation O(1).  Indices of an array map to a memory address via pointer arithmetic, allowing us to check the stored value directly.

- Searching for a value not contained within the array

Searching for a value in an array is a linear time operation O(n).  Each element in the array needs to be checked; in the worst case, the value will be at the end of the array.

- Insertion at the beginning of the array

Inserting at the beginning of an array is a linear time operation O(n).  Every subsequent element will have to shift to the right by one to make space for the new element.

- Insertion at the end of the array

Inserting at the end of an array is a constant time operation on average O(1).  Since we are inserting at the end, no elements will have to shift over.  Therefore in the best case, this operation is O(1).  However, if the array is at max capacity, the array will need to undergo a resizing operation to accomodate the new element.  The resizing operation is O(n) since a new array will be created in memory, and all elements will be copied over to the new array.  Since the resizing operation happens far fewer times compared to insertion, the amortized cost of insertion is O(1).
  
- Deletion at the beginning of the array

Deleting an element at the beginning of an array is a linear time operation O(n).  Each subsequent element will have to shift to the left by one position in order to fill the deleted element's slot.

- Deletion at the end of the array

Deleting an element at the end of an array is a constant time operation O(1).

4. Normally the search operation in an array looks for the first instance of a given value. But sometimes we may want to look for every instance of a given value. For example, say we want to count how many times the value “apple” is found inside an array. How many steps would it take to find all the “apples”? Give your answer in terms of N. (theoretical) - **1 pts**

In order to find all the "apple" values, we will need to look at every element in the array.  This is because an "apple" may be the last element of the array, and therefore, we will need to check every element to account for all possibilities.  This is a linear time operation O(n).

6. Research how to find the memory address of an array. You can use any programming language of your choice. (requires code) **1 pts**

In C++ you can use the address-of operator, '&', to find the memory address of any object in memory.

```cpp
#include <iostream>

int main(void) {
  int arr[100];

  // '&' Address-of operator
  std::cout << "Address of the array: " << &arr << std::endl;

  return 0;
}
```
