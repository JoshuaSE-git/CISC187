# Recursions

## Objective
Implement recursions in C++

## Tasks
1. The following function prints every other number from a low number to a high number. For example, if low is 0 and high is 10, it would print:
```
0
2
4
6
8
10
```

Identify the base case in the function:
```
def print_every_other(low, high) 
    return if low > high
    puts low
    print_every_other(low + 2, high)
end
```

The base case is (if low > high).  Once the bottom bound increases past the top bound, the function returns without printing or calling itself.

2. My kid was playing with my computer and changed my factorial function so that it computes factorial based on (n - 2) instead of (n - 1). Predict what will happen when we run factorial(10) using this function:

```
def factorial(n)
    return 1 if n == 1
    return n * factorial(n - 2)
end
```

This factorial function will cause an infinite recursion loop since the base case (n == 1) will never occur.  This happens because each recursive call decrements n by 2, and since we start at 10, we skip over 1.

3. Following is a function in which we pass in two numbers called low and high. The function returns the sum of all the numbers from low to high. For example, if low is 1, and high is 10, the function will return the sum of all numbers from 1 to 10, which is 55. However, our code is missing the base case, and will run indefinitely! Fix the code by adding the correct base case:
```
def sum(low, high)
    return high + sum(low, high - 1)
end
```

Solution:

```cpp
#include <iostream>

using namespace std;

int sum(int low, int high) {
    if (low > high) {
        return 0;
    }
    return high + sum(low, high - 1);
}

int main() {
    cout << sum(1, 5) << endl;
    return 0;
}
```

4. Here is an array containing both numbers as well as other arrays, which in turn contain numbers and arrays:
```
array=[ 1, 
        2, 
        3,
        [4, 5, 6],
        7,
        [8,
          [9, 10, 11,
            [12, 13, 14]
          ] 
        ],
        [15, 16, 17, 18, 19,
          [20, 21, 22,
            [23, 24, 25,
              [26, 27, 29]
            ], 30, 31 
          ], 32
        ], 33 
      ]
```
Write a recursive function that prints all the numbers (and just numbers).

```cpp
#include <iostream>
#include <vector>
#include <variant>

using namespace std;

struct Node;

// A Node can hold either an int or a vector of Nodes
using Element = variant<int, vector<Node>>;

struct Node {
    Element value;
};

// Recursive function to print all numbers
void print_numbers(const vector<Node>& arr) {
    for (const auto& elem : arr) {
        if (holds_alternative<int>(elem.value)) {
            // Base case: it's a number
            cout << get<int>(elem.value) << endl;
        } else {
            // Recursive case: it's another array
            print_numbers(get<vector<Node>>(elem.value));
        }
    }
}

int main() {
    vector<Node> array = {
        {1},
        {2},
        {3},
        {{ vector<Node>{{4}, {5}, {6}} }},
        {7},
        {{ vector<Node>{
            {8},
            {{ vector<Node>{
                {9}, {10}, {11},
                {{ vector<Node>{{12}, {13}, {14}} }}
            }}}
        }}},
        {{ vector<Node>{
            {15}, {16}, {17}, {18}, {19},
            {{ vector<Node>{
                {20}, {21}, {22},
                {{ vector<Node>{
                    {23}, {24}, {25},
                    {{ vector<Node>{{26}, {27}, {29}} }}
                }}},
                {30}, {31}
            }}},
            {32}
        }}},
        {33}
    };

    print_numbers(array);
    return 0;
}
```
