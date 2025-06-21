# Experiment 12:

## Question:

- I. Write a program to implement Bubble sort technique.
- II. Write a program to implement Insertion sort technique.


## I. Write a program to implement Bubble sort technique.

## Program:

```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void BubbleSort(int *a, int n) {
    int swapped = 0;
    int i, j;

    for (i = 0; i < n; i++) {
        for (j = 0; j < n - 1; j++) {
            if (a[j] > a[j + 1]) {
                swap(&a[j], &a[j + 1]);
                swapped = 1;
            }
        }

        if (swapped == 0) {
            break;
        }
    }
}

int main() {
    int a[100];
    int n, i;

    printf("Enter the size of the array:\n");
    scanf("%d", &n);

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }

    BubbleSort(a, n);  // Calling BubbleSort function

    printf("Sorted array:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", a[i]);
    }
    printf("\n");
    return 0;
}
```

## Output:

```

```
## II. Write a program to implement Insertion sort technique.

## Program:

```c
#include <stdio.h>

int main(void) {
    int arr[100];
    int n, i, j, temp;

    printf("Enter the size of the array:\n");
    scanf("%d", &n);

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    // Insertion Sort
    for (i = 1; i < n; i++) {
        j = i;
        while (j > 0 && arr[j - 1] > arr[j]) {
            temp = arr[j];
            arr[j] = arr[j - 1];
            arr[j - 1] = temp;
            j--;
        }
    }

    printf("Sorted array:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

## Output:
```

```