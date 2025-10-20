# Binary Search Trees

## Objective
Implement binary search trees data structures

## Task
1. Imagine you were to take an empty binary search tree and insert the following sequence of numbers in this order: [1, 5, 9, 2, 4, 10, 6, 3, 8]. Draw a diagram showing what the binary search tree would look like. Remember, the numbers are being inserted in the order presented here. **(2 points)**

![IMG_0034](https://github.com/user-attachments/assets/fd7c81aa-06fd-4be8-ad7d-af03cd652dcc)

2. If a well-balanced binary search tree contains 1,000 values, what is the maximum number of steps it would take to search for a value within it? **(1 point)**

round_up(log_2(1000)) = 10

It would take 10 steps at most to find a value within a BST of 1000 values.

3. Write an algorithm that finds the greatest value within a binary search tree. **2 points)**

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

// Function to find the greatest (maximum) value in a BST
int findMax(Node* root) {
    if (root == nullptr) {
        cout << "The tree is empty." << endl;
        return -1;  // or throw an exception
    }

    // The maximum value is found by following the right child pointers
    Node* current = root;
    while (current->right != nullptr) {
        current = current->right;
    }

    return current->data;
}

// Example usage
int main() {
    Node* root = new Node{5, nullptr, nullptr};
    root->left = new Node{2, nullptr, nullptr};
    root->right = new Node{9, nullptr, nullptr};
    root->right->left = new Node{6, nullptr, nullptr};
    root->right->right = new Node{10, nullptr, nullptr};

    cout << "Greatest value in the BST: " << findMax(root) << endl;

    return 0;
}
```

4. Write a code in C++ using the same array mentioned in #1 and implement a binary search tree. Only insertion operation is required. **(5 points)**

```cpp
#include <iostream>
using namespace std;

// Define a node structure for the BST
struct Node {
    int data;
    Node* left;
    Node* right;
};

// Function to create a new node
Node* createNode(int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->left = nullptr;
    newNode->right = nullptr;
    return newNode;
}

// Function to insert a value into the BST
Node* insert(Node* root, int value) {
    if (root == nullptr) {
        return createNode(value);
    }

    if (value < root->data)
        root->left = insert(root->left, value);
    else if (value > root->data)
        root->right = insert(root->right, value);

    return root;
}

int main() {
    int arr[] = {1, 5, 9, 2, 4, 10, 6, 3, 8};
    int n = sizeof(arr) / sizeof(arr[0]);

    Node* root = nullptr;

    // Insert each element from the array into the BST
    for (int i = 0; i < n; i++) {
        root = insert(root, arr[i]);
    }

    return 0;
}
```
