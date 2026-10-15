# Practical 8: Depth-First Search (DFS) in a Graph

## Aim
Write a program to implement Depth-First Search (DFS) in a graph.

## Theory
A graph is a non-linear network consisting of vertices (nodes) connected by edges (links).

Depth-First Search explores as deeply as possible along one branch before backtracking. It can be implemented using a stack.

**How DFS works**
1. Push the starting node onto a stack.
2. Pop a node. If it has not been visited, mark and print it.
3. Push its unvisited adjacent nodes onto the stack.
4. Continue until the stack is empty.

## Code (C++)
```cpp
#include <iostream>
using namespace std;

const int MAX = 20;
int graph[MAX][MAX];
bool visited[MAX];
int n;
int stackArr[MAX * MAX];
int top = -1;

void dfs(int start) {
    stackArr[++top] = start;

    while (top != -1) {
        int node = stackArr[top--];

        if (!visited[node]) {
            visited[node] = true;
            cout << node << " ";

            // Reverse order keeps traversal similar to ascending-neighbor DFS.
            for (int i = n - 1; i >= 0; i--) {
                if (graph[node][i] == 1 && !visited[i])
                    stackArr[++top] = i;
            }
        }
    }
}

int main() {
    cout << "Enter number of nodes (maximum 20): ";
    cin >> n;

    if (n < 1 || n > MAX) {
        cout << "Invalid number of nodes\n";
        return 1;
    }

    cout << "Enter the adjacency matrix:\n";
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            cin >> graph[i][j];

    int start;
    cout << "Enter starting node (0 to " << n - 1 << "): ";
    cin >> start;

    if (start < 0 || start >= n) {
        cout << "Invalid starting node\n";
        return 1;
    }

    cout << "DFS Traversal: ";
    dfs(start);
    cout << "\n";
    return 0;
}
```

## Conclusion
The program traverses nodes reachable from the starting node using depth-first search and backtracking.
