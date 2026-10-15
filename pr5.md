# Practical 5: Implement Queue Using a Linked List

## Aim
Implement a queue using a linked list.

## Theory
A queue is a linear data structure that follows **FIFO (First In, First Out)**. Elements are inserted at the rear and removed from the front.

**Basic operations**
- `enqueue`: add an element to the rear.
- `dequeue`: remove an element from the front.
- `display`: show the queue elements.

## Code (C++)
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int value) : data(value), next(nullptr) {}
};

Node* frontNode = nullptr;
Node* rearNode = nullptr;

void enqueue(int value) {
    Node* node = new Node(value);

    if (rearNode == nullptr) {
        frontNode = rearNode = node;
    } else {
        rearNode->next = node;
        rearNode = node;
    }
}

void dequeue() {
    if (frontNode == nullptr) {
        cout << "Queue is empty\n";
        return;
    }

    Node* temp = frontNode;
    cout << "Deleted value: " << temp->data << "\n";
    frontNode = frontNode->next;

    if (frontNode == nullptr)
        rearNode = nullptr;

    delete temp;
}

void display() {
    if (frontNode == nullptr) {
        cout << "Queue is empty\n";
        return;
    }

    Node* temp = frontNode;
    while (temp != nullptr) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL\n";
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);

    cout << "Queue: ";
    display();

    dequeue();
    cout << "Queue after dequeue: ";
    display();

    // Clean up remaining nodes
    while (frontNode != nullptr) {
        Node* temp = frontNode;
        frontNode = frontNode->next;
        delete temp;
    }
    rearNode = nullptr;

    return 0;
}
```

## Conclusion
The program implements queue insertion and deletion using a linked list.
