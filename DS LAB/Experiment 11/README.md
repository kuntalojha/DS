# Experiment 11:

## Question:

- I. Write a program to implement Linear Search technique.
- II. Write a program to implement Binary Search technique.

## I. Write a program to implement Linear Search technique.

## Program:

```c
#include <stdio.h>

int linearSearch(int arr[], int size, int key) {
    int i;
    for (i = 0; i < size; i++) {
        if (key == arr[i]){
            return i; // Element found
        }
    }
    return -1; // Element not found
}
int  main() {
    // Unsorted array for linear search
    // Note: Linear search does not require the array to be sorted
    int arr[]={50, 90, 30, 40, 10, 60, 77, 8, 90, 100};
    int key,size,result;
    size = sizeof(arr)/sizeof(arr[0]);
    
    printf("Enter the element to search: ");
    scanf("%d", &key);
    result = linearSearch(arr, size, key);
    if (result == -1) {
        printf("Element %d is not found in the array.\n", key);
    }else {
        printf("Element %d is found at index %d.\n", key, result);
    }
    return 0;
}

```

## Output:

```

```
## II. Write a program to implement Binary Search technique.

## Program:

```c
#include <stdio.h>

int binarySearch(int arr[], int size, int key) {
    int mid;
    int i=0;
    while (i < size) {
        mid = (i + size) / 2;
        if (key == arr[mid])
            return mid; // Element found
        else if (key > arr[mid])
            i = mid + 1;
        else
            size = mid - 1;
    }
    return -1; // Element not found
}

int  main() {
    // Sorted array for binary search
    // Note: Binary search requires the array to be sorted
    int arr[]={10, 30, 40, 50, 69, 77, 80, 90, 100, 110};
    int key,size,result;
    size = sizeof(arr)/sizeof(arr[0]);
    
    printf("Enter the element to search: ");
    scanf("%d", &key);
    result = binarySearch(arr, size, key);
    if (result == -1) {
        printf("Element %d is not found in the array.\n", key);
    }else {
        printf("Element %d is found at index %d.\n", key, result);
    }
    return 0;
}
```

## Output:
```

```