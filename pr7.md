# Practical 7: Breadth-First Search (BFS) in a Graph

## Aim
Write a program to implement Breadth-First Search (BFS) in a graph.

## Theory
A graph is a non-linear structure made up of vertices (nodes) connected by edges (links).

Breadth-First Search traverses a graph level by level using a queue.

**How BFS works**
1. Choose a starting node, mark it visited, and add it to a queue.
2. Remove the front node from the queue and visit it.
3. Find each adjacent unvisited node, mark it visited, and add it to the queue.
4. Repeat until the queue is empty.

## Code (C++)
```cpp
#include <iostream>
#include <queue>
using namespace std;

const int MAX = 20;
int graph[MAX][MAX];
bool visited[MAX];
int n;

void bfs(int start) {
    queue<int> q;
    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";

        for (int i = 0; i < n; i++) {
            if (graph[node][i] == 1 && !visited[i]) {
                visited[i] = true;
                q.push(i);
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

    cout << "BFS Traversal: ";
    bfs(start);
    cout << "\n";
    return 0;
}
```

## Conclusion
The program traverses all nodes reachable from the starting node in breadth-first order.
