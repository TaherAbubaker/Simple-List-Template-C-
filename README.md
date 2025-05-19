# SimpleListTemplate

A simple generic list class template implemented in C++ with fixed-size array storage.

---

## Description

This project implements a basic `list` class template in C++ that supports essential list operations such as:

- Insert an element at any position.
- Insert multiple random elements.
- Remove an element by position.
- Find an element's index.
- Check if the list contains a value.
- Retrieve an element by index.
- Clear the list.
- Print the list contents.

The list uses a fixed-size array (`maxsize = 100`) to store elements and keeps track of the current count of items. This example also demonstrates how to use the list to manage a simple to-do list with string tasks.

---

## Usage Example

```cpp
list<string> todoList;

// Add tasks
todoList.insert(todoList.size(), "Buy groceries");
todoList.insert(todoList.size(), "Finish homework");
todoList.insert(todoList.size(), "Call mom");

// Insert at top priority
todoList.insert(0, "Pay bills");

// Remove a completed task
int pos = todoList.find("Finish homework");
if (pos != -1) {
    todoList.remove(pos);
}

// Print all remaining tasks
todoList.print();
