# Practical 2: Bubble Sort and Selection Sort

## Aim
Write a C++ program to sort an array in ascending order using bubble sort and selection sort.

## Theory

### Bubble Sort
Bubble sort repeatedly compares adjacent elements and swaps them when they are in the wrong order. After each pass, the largest unsorted element moves to the end.

### Selection Sort
Selection sort repeatedly finds the smallest element in the unsorted part of the array and places it at the beginning of that part.

## Code: Bubble Sort (C++)
```cpp
#include <iostream>
using namespace std;
int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;

    if (n <= 0) {
        cout << "Number of elements must be positive\n";
        return 1;
    }

    int* arr = new int[n];
    cout << "Enter array elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // Bubble sort logic
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    cout << "Sorted array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    delete[] arr;
    return 0;
}
```

## Code: Selection Sort (C++)
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;

    if (n <= 0) {
        cout << "Number of elements must be positive\n";
        return 1;
    }
    int* arr = new int[n];
    cout << "Enter array elements: ";
    for (int i = 0; i < n; i++)
        cin >> arr[i];

    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex])
                minIndex = j;
        }

        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }

    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
    delete[] arr;
    return 0;
}
```

## Conclusion
Bubble sort and selection sort arrange the array elements in ascending order.
