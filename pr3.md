# Practical 3: Insert and Delete at Any Position in a Singly Linked List

## Aim
Write a program to insert and delete an element at any position in a singly linked list.

## Theory
In a singly linked list, each node contains data and a pointer to the next node. Insertion creates a node and adjusts links to place it at the required position. Deletion removes a node by changing the previous node's `next` pointer to skip it. Reaching a position requires traversal, so these operations generally take `O(n)` time.

## Code (C++)
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
    Node(int value) : data(value), next(nullptr) {}
};

void display(Node* head) {
    while (head != nullptr) {
        cout << head->data << " -> ";
        head = head->next;
    }
    cout << "NULL\n";
}

void insertAtPosition(Node*& head, int value, int position) {
    if (position < 1) {
        cout << "Invalid position\n";
        return;
    }

    Node* node = new Node(value);
    if (position == 1) {
        node->next = head;
        head = node;
        return;
    }

    Node* current = head;
    for (int i = 1; current != nullptr && i < position - 1; i++)
        current = current->next;

    if (current == nullptr) {
        cout << "Invalid position\n";
        delete node;
        return;
    }

    node->next = current->next;
    current->next = node;
}

void deleteAtPosition(Node*& head, int position) {
    if (head == nullptr || position < 1) {
        cout << "Invalid position or empty list\n";
        return;
    }

    if (position == 1) {
        Node* old = head;
        head = head->next;
        delete old;
        return;
    }

    Node* current = head;
    for (int i = 1; current != nullptr && i < position - 1; i++)
        current = current->next;

    if (current == nullptr || current->next == nullptr) {
        cout << "Invalid position\n";
        return;
    }

    Node* old = current->next;
    current->next = old->next;
    delete old;
}

int main() {
    Node* head = nullptr;
    int n, value, position;

    cout << "Enter number of nodes: ";
    cin >> n;

    if (n < 0) {
        cout << "Number of nodes cannot be negative\n";
        return 1;
    }

    Node* tail = nullptr;
    for (int i = 0; i < n; i++) {
        cout << "Enter value: ";
        cin >> value;
        Node* node = new Node(value);
        if (head == nullptr)
            head = tail = node;
        else {
            tail->next = node;
            tail = node;
        }
    }

    cout << "Original list: ";
    display(head);

    cout << "Enter value and position to insert: ";
    cin >> value >> position;
    insertAtPosition(head, value, position);
    cout << "After insertion: ";
    display(head);

    cout << "Enter position to delete: ";
    cin >> position;
    deleteAtPosition(head, position);
    cout << "After deletion: ";
    display(head);

    while (head != nullptr) {
        Node* old = head;
        head = head->next;
        delete old;
    }
    return 0;
}
```

## Conclusion
The program inserts and deletes nodes at a specified position in a singly linked list.
