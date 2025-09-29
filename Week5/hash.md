# Hash tables

## Objective
Understand the working of hash tables

## Task
1. Assume you have a simple single-dimensional array

```array = [200, 400, 100, 50, 350]```

Linear search will take $O(N)$. Write a code in C++/Python to improve the search operation efficiency from $O(N)$ to $O(1)$. **4 pts **

```cpp
#include <iostream>
#include <map>

int main() {
  std::map<int, bool> nums = {
      {200, true}, {400, true}, {100, true}, {50, true}, {350, true},
  };

  if (nums[400]) {
    std::cout << "400 in nums" << std::endl;
  };
}
```

Here I'm using a hash map like a hash set.  The key is the integer and the value is a boolean to indicate that the integer is part of the set.  The lookup time is for any element is O(1).

2. Use C++, generate hash value of your name. **1 pts**

```cpp
#include <functional>
#include <iostream>
#include <string>

int main() {
  std::string name = "Joshua Emralino";
  std::size_t h = std::hash<std::string>{}(name);
  std::cout << "Name: " << name << "\nHash: " << h << "\n";
  return 0;
}
```

4. With the help of a figure, explain the problem that occured due to introducing a __tombstone__ to mark the deleted cell. **5 pts**

When we introduce tombstones in an open-addressed hash table, we run the risk of slowing down operations like searching and probing.  Tombstones are necessary to keep probe chains intact, but when too many of them start to accumulate, searching can end becoming inneficient.
