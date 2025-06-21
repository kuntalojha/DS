# Experiment 13:

## Question:

- I. Write a program to implement Quick sort technique.
- II. Write a program to implement Merge sort technique.

## I. Write a program to implement Quick sort technique.

## Program:

```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int *a, int f, int l) {
    int pivot = a[l]; // selecting last element as pivot
    int i, j = f - 1;

    for (i = f; i < l; i++) {
        if (pivot > a[i]) {
            j++;
            swap(&a[i], &a[j]);
        }
    }

    swap(&a[j + 1], &a[l]);
    return j + 1;
}

void quickSort(int *a, int f, int l) {
    if (f < l) {
        int q = partition(a, f, l);
        quickSort(a, f, q - 1);
        quickSort(a, q + 1, l);
    }
}

int main() {
    int a[100];
    int i, n;

    printf("Enter the size of the array:\n");
    scanf("%d", &n);

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }

    quickSort(a, 0, n - 1); // calling quickSort on the whole array

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
## II. Write a program to implement Merge sort technique.

## Program:

```c
#include <stdio.h>
#include <limits.h>

void merge(int *a, int f, int l) {
    int LA[100], RA[100];
    int m = (f + l) / 2;
    int n1 = m - f + 1;
    int n2 = l - m;
    int i, j, k;

    for (i = 0; i < n1; i++)
        LA[i] = a[f + i];
    for (j = 0; j < n2; j++)
        RA[j] = a[m + 1 + j];

    LA[n1] = INT_MAX;
    RA[n2] = INT_MAX;

    i = 0;
    j = 0;

    for (k = f; k <= l; k++) {
        if (LA[i] <= RA[j])
            a[k] = LA[i++];
        else
            a[k] = RA[j++];
    }
}

void mergeSort(int *a, int f, int l) {
    if (f < l) {
        int m = (f + l) / 2;
        mergeSort(a, f, m);
        mergeSort(a, m + 1, l);
        merge(a, f, l);
    }
}

int main() {
    int a[100];
    int i, n;

    printf("Enter the size of the array:\n");
    scanf("%d", &n);

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }
    // calling mergeSort on the whole array
    mergeSort(a, 0, n - 1);

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