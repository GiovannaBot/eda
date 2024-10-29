---
layout: default
title: Quick Select
nav_order: 1
description: 'Quick Select'
parent: Search Algorithms
---

Quick Select
{: .fs-9}

The Quick Select is used to find the k-th smallest element in an unordered list without fully sorting it. It’s like going straight to the dress you want without rearranging the whole closet! 👗✨

## Quick Select Code in C with Complexity Analysis 💻
Here’s the C code with complexity explained for each line:

```c
#include <stdio.h>

// Function to swap two elements
void swap(int *a, int *b) {
    int temp = *a;  // O(1) - Constant time to assign a variable
    *a = *b;        // O(1) - Constant time to assign a variable
    *b = temp;      // O(1) - Constant time to assign a variable
}
// Total complexity for swap: O(1)

// Partition function for Quick Select
int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // O(1) - Constant time to set the pivot
    int i = (low - 1);      // O(1) - Constant time to initialize index

    for (int j = low; j < high; j++) {  // O(n) - Iterates n times
        if (arr[j] <= pivot) {  // O(1) - Comparison
            i++;                // O(1) - Increment
            swap(&arr[i], &arr[j]);  // O(1) - Swap operation
        }
    }
    swap(&arr[i + 1], &arr[high]);  // O(1) - Final swap to position pivot
    return (i + 1);  // O(1) - Return index of pivot
}
// Total complexity for partition: O(n)

// Quick Select function
int quickSelect(int arr[], int low, int high, int k) {
    if (low <= high) {  // O(1) - Constant time comparison
        int pi = partition(arr, low, high);  // O(n) - Partition call

        // If the pivot is in the k-th position
        if (pi == k)  // O(1) - Constant time comparison
            return arr[pi];  // O(1) - Return the k-th element

        // If k-th element is in the left subarray
        else if (pi > k)  // O(1) - Constant time comparison
            return quickSelect(arr, low, pi - 1, k);  // T(n/2) - Recursion on left subarray

        // If k-th element is in the right subarray
        else  // O(1) - Constant time comparison
            return quickSelect(arr, pi + 1, high, k);  // T(n/2) - Recursion on right subarray
    }
    return -1;  // O(1) - Return statement
}
// Total complexity for quickSelect: T(n) = T(n/2) + O(n)

// Function to print an array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)  // O(n) - Iterates n times
        printf("%d ", arr[i]);      // O(1) - Print operation
    printf("\n");                   // O(1) - Newline print
}
// Total complexity for printArray: O(n)

int main() {
    // Example array of dress colors (represented by numbers)
    int arr[] = {8, 2, 4, 7, 1, 9, 5, 3, 6};  // O(1) - Initialization
    int n = sizeof(arr) / sizeof(arr[0]);     // O(1) - Calculate size

    int k = 2;  // O(1) - k-th smallest element, 0-based index

    // Find the k-th smallest element using Quick Select
    int kthSmallest = quickSelect(arr, 0, n - 1, k);  // O(n) - Average complexity of quickSelect

    // Print the k-th smallest element
    printf("The %d-th smallest element is: %d\n", k + 1, kthSmallest);  // O(1)
    return 0;  // O(1) - Return statement
}
// Total complexity for main: O(n) due to quickSelect

```

## Quick Select Function:

The recursive call is made only on one side of the array (left or right), reducing the size by about half each time. The recurrence relation for Quick Select is: T(n)=T(n/2)+O(n)

Applying the Master Theorem, the overall average complexity is: (n)

In the worst case (if the pivot is consistently the smallest or largest), the complexity becomes O(n^2), but with techniques like random pivot selection, this is rare.

## Summary with Glamour 🌟✨

- Average Complexity of Quick Select: O(n).
- Worst-Case Complexity: O(n^2) (rare with good pivot selection).
- Best-Case Complexity: O(n), when the pivot consistently splits the array well.
  
Quick Select is all about finding the desired element quickly and efficiently, just like picking the perfect dress from your closet without rearranging everything! 👗✨
