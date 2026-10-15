# Code Validation Report

All C++ code blocks from `pr1.md` through `pr8.md` were compiled using `g++ -std=c++17 -Wall -Wextra -Wpedantic` (0 errors, 0 warnings) and verified with edge-case and representative inputs.

## Summary of Results

| Practical | Topic | Code Blocks | Status | Notes / Fixes Applied |
|---|---|---|---|---|
| **[pr1.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr1.md)** | Linear Search & Binary Search | 2 | **PASS** | Added missing `Enter array elements: ` prompt in Linear Search; normalized prompt formatting. |
| **[pr2.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr2.md)** | Bubble Sort & Selection Sort | 2 | **PASS** | Cleaned leftover inline comments (`// Fixed allocation and pointer syntax`). Tested with ascending, descending, and arbitrary inputs. |
| **[pr3.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr3.md)** | Singly Linked List (Insert/Delete) | 1 | **PASS** | Added negative node-count validation check (`n < 0`). Verified head, middle, and tail insertions and deletions. |
| **[pr4.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr4.md)** | Stack using Array | 1 | **PASS** | Tested `push`, `pop`, `peek`, and `display` operations. Stack overflow and underflow conditions are correctly guarded. |
| **[pr5.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr5.md)** | Queue using Linked List | 1 | **PASS** | Added proper memory deallocation before program exit in `main()`. FIFO semantics and empty queue checks verified. |
| **[pr6.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr6.md)** | Binary Tree Traversals | 1 | **PASS** | Inorder, Preorder, and Postorder recursive traversals verified. Complete tree memory deallocation with `deleteTree()` verified. |
| **[pr7.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr7.md)** | Breadth-First Search (BFS) | 1 | **PASS** | Added clear `BFS Traversal: ` output label for clean console display. Level-order graph traversal verified. |
| **[pr8.md](file:///home/vaibhav/Documents/study/p/dsa_practicals_md/pr8.md)** | Depth-First Search (DFS) | 1 | **PASS** | Added clear `DFS Traversal: ` output label. Iterative stack-based graph traversal verified. |

---

## Detailed Test Cases & Sample Outputs

### Practical 1: Linear Search and Binary Search
- **Linear Search**:
  - Input: size `5`, elements `10 20 30 40 50`, target `30` → Output: `Element found at index 2`
  - Input: size `5`, elements `10 20 30 40 50`, target `99` → Output: `Element not found`
- **Binary Search**:
  - Input: size `5`, elements `10 20 30 40 50`, key `30` → Output: `Element found at index 2`
  - Input: size `5`, elements `10 20 30 40 50`, key `99` → Output: `Element not found`

### Practical 2: Bubble Sort and Selection Sort
- **Bubble Sort**:
  - Input: `5` elements (`64 34 25 12 22`) → Output: `Sorted array: 12 22 25 34 64`
- **Selection Sort**:
  - Input: `5` elements (`64 34 25 12 22`) → Output: `Sorted array: 12 22 25 34 64`

### Practical 3: Singly Linked List Insert & Delete at Any Position
- **Initial list creation**: 3 nodes (`10 -> 20 -> 30 -> NULL`)
- **Insert `15` at position `2`**: `10 -> 15 -> 20 -> 30 -> NULL`
- **Delete at position `3`**: `10 -> 15 -> 30 -> NULL`

### Practical 4: Stack using Array
- Push `3`, `5`, `4`
- Display: prints `4`, `5`, `3` (top-to-bottom)
- Pop: removes `4`
- Peek: `Top element: 5`

### Practical 5: Queue using Linked List
- Enqueue `10`, `20`, `30`
- Initial queue: `10 -> 20 -> 30 -> NULL`
- Dequeue: deletes `10`
- Queue after dequeue: `20 -> 30 -> NULL`
- Proper heap cleanup upon termination

### Practical 6: Binary Tree Traversals
- Sample tree: Root `1`, Left Child `2`, Right Child `3`
- **Inorder**: `2 1 3`
- **Preorder**: `1 2 3`
- **Postorder**: `2 3 1`

### Practical 7: Graph Breadth-First Search (BFS)
- Adjacency matrix for 4 vertices, starting vertex `0`
- Output: `BFS Traversal: 0 1 2 3`

### Practical 8: Graph Depth-First Search (DFS)
- Adjacency matrix for 4 vertices, starting vertex `0`
- Output: `DFS Traversal: 0 1 3 2`
