# Practical 1: Linear Search and Binary Search

## Aim
Implement linear search and binary search.

## Theory
Searching is the process of locating a specific element, key, or piece of data in a collection such as an array, list, database, or tree. If the element is found, the search returns its position or index; otherwise, the search is unsuccessful.

### 1. Linear Search
Linear search (sequential search) checks each element from the beginning until the target is found or the entire collection has been scanned.

**Steps**
1. Start at the first element (index `0`).
2. Compare the current element with the target.
3. If they match, return the current index.
4. Otherwise, move to the next element.
5. Repeat until the target is found or the end is reached.

**Time complexity**
- Best case: `O(1)` — target is the first element.
- Average case: `O(n)`.
- Worst case: `O(n)` — target is last or absent.

## Code: Linear Search (C++)
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the size of array: ";
    cin >> n;

    if (n <= 0) {
        cout << "Array size must be positive\n";
        return 1;
    }
    int* arr = new int[n];
    cout << "Enter array elements: ";
    for (int i = 0; i < n; i++)
        cin >> arr[i];

    int target;
    cout << "Enter the target element: ";
    cin >> target;

    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            cout << "Element found at index " << i << "\n";
            delete[] arr;
            return 0;
        }
    }

    cout << "Element not found\n";
    delete[] arr;
    return 0;
}
```

### 2. Binary Search
Binary search finds a target in a **sorted array** by repeatedly checking the middle element and discarding half of the remaining search range.

**Steps**
1. Set `low` to the first index and `high` to the last index.
2. Find `mid = low + (high - low) / 2`.
3. If `arr[mid]` equals the target, report the index.
4. If the target is greater, search the right half; otherwise, search the left half.
5. Continue while `low <= high`.

**Time complexity**
- Best case: `O(1)` — target is the middle element.
- Worst case: `O(log n)`.

## Code: Binary Search (C++)
```cpp
#include <iostream>

using namespace std;

int main() {
    int n, key;
    cout << "Enter the size of array: ";
    cin >> n;

    if (n <= 0) {
        cout << "Array size must be positive\n";
        return 1;
    }

    int* arr = new int[n];
    cout << "Enter the array elements in sorted order: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Enter the value of key: ";
    cin >> key;

    int low = 0, high = n - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] == key) {
            cout << "Element found at index " << mid << "\n";
            delete[] arr;
            return 0;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    cout << "Element not found\n";
    delete[] arr;
    return 0;
}
```

## Conclusion
Linear search checks elements one by one. Binary search is more efficient for large sorted arrays because it halves the search range at each step.
