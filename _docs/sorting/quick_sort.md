---
layout: default
title: Quick Sort
nav_order: 4
description: 'Quick Sort'
parent: Sorting Algorithms
---

Quick Sort
{: .fs-9}

Quick Sort is like that perfect little black dress: super versatile, elegant, and suitable for many occasions! But, just like any wardrobe piece, it shines brighter in some situations than others.

## When to Use Quick Sort 💅

The Quick Sort is particularly useful in certain scenarios, and here are the moments when it’s the perfect choice:

- Large and Unordered Lists 📝: Quick Sort is ideal for large, completely unordered lists because it has an average complexity of O(nlogn), making it very efficient for handling large amounts of data. If you need to sort a large, unordered list quickly and don’t mind the potential for a worst-case scenario (which is rare), Quick Sort is a great choice!
- When Memory is a Concern 💻 Quick Sort is in-place, meaning it doesn’t require significant extra memory beyond the space used by the list itself. This makes it great when you have memory constraints and need to sort the list without creating many copies or additional structures, unlike other algorithms like Merge Sort, which use extra space.
- When Consistent Average Performance is Needed 🚀 While Quick Sort can have a worst-case time complexity of O(n^2), it is well optimized in most implementations and generally faster than other sorting algorithms, like Merge Sort, due to lower constant overhead and optimizations made during execution. Modern implementations of Quick Sort use techniques like random pivot selection or median-of-three pivoting to reduce the chance of hitting the worst-case scenario.
- When Sorting Arrays 🧩 Quick Sort is more efficient with arrays than with linked lists because it accesses elements directly via indices, which is more complex with linked lists. This makes it excellent for situations where your data is stored in contiguous memory arrays, as is common in many programming languages (e.g., C, C++, Python).

## Quick Sort Code in C 💻
Here’s how the Quick Sort code would look in C:

```c
#include <stdio.h>

// Function to swap two elements
void swap(int *a, int *b) {
    int temp = *a;  // O(1) - Constant time to assign a variable
    *a = *b;        // O(1) - Constant time to assign a variable
    *b = temp;      // O(1) - Constant time to assign a variable
}
// Total complexity for swap: O(1)

// Partition function for Quick Sort
int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // O(1) - Constant time to set the pivot
    int i = (low - 1);      // O(1) - Constant time to initialize index

    for (int j = low; j < high; j++) {  // O(n) - Iterates n times
        // If current element is less than or equal to pivot
        if (arr[j] <= pivot) {  // O(1) - Comparison
            i++;                // O(1) - Increment
            swap(&arr[i], &arr[j]);  // O(1) - Swap operation
        }
    }
    swap(&arr[i + 1], &arr[high]);  // O(1) - Final swap to position pivot
    return (i + 1);  // O(1) - Return index of pivot
}
// Total complexity for partition: O(n)

// Quick Sort function
void quickSort(int arr[], int low, int high) {
    if (low < high) {  // O(1) - Constant time comparison
        int pi = partition(arr, low, high);  // O(n) - Partition call

        // Recursively sort the subarrays
        quickSort(arr, low, pi - 1);   // T(n/2) - Recursive call for left subarray
        quickSort(arr, pi + 1, high);  // T(n/2) - Recursive call for right subarray
    }
}
// Total complexity for quickSort: T(n) = 2 * T(n/2) + O(n)

// Function to print an array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)  // O(n) - Iterates n times
```

## The recursive calls make the complexity: 

T(n)=2⋅T(n/2)+O(n).

Using the Master Theorem, we get the average complexity of O(nlogn).
- In the worst case, when the pivot is always the smallest or largest element, the complexity becomes O(n^2), but this is rare with optimizations like random pivot selection.

## Summary with Glamour! 🌟

Use Quick Sort when you need to sort large, unordered lists efficiently, especially when memory is a concern. It has an average complexity of O(nlogn), making it versatile and quick, like the perfect outfit for most occasions! 👗✨
