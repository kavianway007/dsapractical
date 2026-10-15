# Practical 6: Inorder, Preorder, and Postorder Traversal of a Binary Tree

## Aim
Write a program to find inorder, preorder, and postorder traversal of a binary tree.

## Theory
A binary tree is a hierarchical, non-linear data structure in which each node has at most two children: a left child and a right child.

**Key terminology**
- **Root:** the topmost node, which has no parent.
- **Edge:** a link connecting a parent node to a child node.
- **Leaf:** a node with no children.
- **Height:** the number of edges on the longest path from the root to a leaf.

### Traversal methods
- **Preorder:** Root → Left → Right.
- **Inorder:** Left → Root → Right.
- **Postorder:** Left → Right → Root.

## Code (C++)
```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) : data(value), left(nullptr), right(nullptr) {}
};

void inorder(Node* root) {
    if (root == nullptr) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

void preorder(Node* root) {
    if (root == nullptr) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

void postorder(Node* root) {
    if (root == nullptr) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

Node* createTree() {
    int value;
    cout << "Enter node value (-1 for no node): ";
    cin >> value;

    if (value == -1)
        return nullptr;

    Node* root = new Node(value);
    cout << "Enter left child of " << value << "\n";
    root->left = createTree();
    cout << "Enter right child of " << value << "\n";
    root->right = createTree();
    return root;
}

void deleteTree(Node* root) {
    if (root == nullptr) return;
    deleteTree(root->left);
    deleteTree(root->right);
    delete root;
}

int main() {
    Node* root = createTree();

    cout << "Inorder: ";
    inorder(root);
    cout << "\nPreorder: ";
    preorder(root);
    cout << "\nPostorder: ";
    postorder(root);
    cout << "\n";

    deleteTree(root);
    return 0;
}
```

## Conclusion
The program constructs a binary tree and displays its inorder, preorder, and postorder traversals.
