# Practical 4: Implement Stack Using an Array

## Aim
Write a program to implement a stack using an array.

## Theory
A stack is a linear data structure that follows **LIFO (Last In, First Out)**. Insertion and deletion occur at one end called the `top`.

**Core operations**
- `push`: insert an element at the top.
- `pop`: remove the top element.
- `peek`: view the top element.
- `display`: show the stack elements.

## Code (C++)
```cpp
#include <iostream>
using namespace std;

const int MAX = 5;
int stk[MAX];
int top = -1;

void push(int value) {
    if (top == MAX - 1) {
        cout << "Stack overflow\n";
    } else {
        stk[++top] = value;
        cout << value << " has been pushed\n";
    }
}

void display() {
    if (top == -1) {
        cout << "Stack is empty\n";
        return;
    }

    for (int i = top; i >= 0; i--)
        cout << stk[i] << "\n";
}

void pop() {
    if (top == -1) {
        cout << "Stack is empty\n";
    } else {
        cout << stk[top--] << " has been popped\n";
    }
}

void peek() {
    if (top == -1)
        cout << "Stack is empty\n";
    else
        cout << "Top element: " << stk[top] << "\n";
}

int main() {
    push(3);
    push(5);
    push(4);

    cout << "\nStack:\n";
    display();

    pop();
    cout << "\nStack after pop:\n";
    display();

    peek();
    return 0;
}
```

## Conclusion
The program implements stack insertion, deletion, viewing the top element, and displaying the stack using an array.
