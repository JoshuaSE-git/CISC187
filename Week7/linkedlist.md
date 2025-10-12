# Linked lists

## Objective
Implement linked lists data structures in C++

## Pre-requisite
Review [Linked lists](https://htmlpreview.github.io/?https://github.com/d-khan/dslabs/blob/main/linked-lists/Linked%20lists.html) contents.

## Task
Create a linked list in C++, add nodes and delete nodes at the start of the list.

```cpp
#include <iostream>
using namespace std;

// Node structure
struct Node {
  int data;
  Node *next;
};

// Linked list class
class LinkedList {
private:
  Node *head;

public:
  LinkedList() : head(nullptr) {}

  void addAtStart(int value) {
    Node *newNode = new Node();
    newNode->data = value;
    newNode->next = head;
    head = newNode;
    cout << "Added " << value << " at the start.\n";
  }

  void deleteAtStart() {
    if (head == nullptr) {
      cout << "List is empty. Nothing to delete.\n";
      return;
    }
    Node *temp = head;
    head = head->next;
    cout << "Deleted " << temp->data << " from the start.\n";
    delete temp;
  }

  void display() const {
    if (head == nullptr) {
      cout << "List is empty.\n";
      return;
    }
    Node *current = head;
    cout << "List: ";
    while (current != nullptr) {
      cout << current->data << " ";
      current = current->next;
    }
    cout << endl;
  }

  ~LinkedList() {
    Node *current = head;
    while (current != nullptr) {
      Node *next = current->next;
      delete current;
      current = next;
    }
  }
};

int main() {
  LinkedList list;

  list.addAtStart(10);
  list.addAtStart(20);
  list.addAtStart(30);
  list.display();

  list.deleteAtStart();
  list.display();

  list.deleteAtStart();
  list.deleteAtStart();
  list.deleteAtStart(); // Deleting from empty list

  return 0;
}
```
