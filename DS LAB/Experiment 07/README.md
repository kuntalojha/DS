# Experiment 7:

## Question:

- **Write a C program to perform following operations on a circular Queue `I. Insertion II. deletion III. search and count`**

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

int *queue;
int front = -1, rear = -1, size = 0;

// Enqueue (Insertion)
void enqueue(int data) {
    if ((front == 0 && rear == size - 1) || (rear + 1) % size == front) {
        printf("Queue is full (Overflow).\n");
        return;
    }
    if (front == -1 && rear == -1) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % size;
    }
    queue[rear] = data;
    printf("Enqueued element: %d\n", data);
}

// Dequeue (Deletion)
void dequeue() {
    if (front == -1) {
        printf("Queue is empty (Underflow).\n");
        return;
    }
    printf("Dequeued element: %d\n", queue[front]);
    if (front == rear) {
        front = rear = -1;
    } else {
        front = (front + 1) % size;
    }
}

// Search and Count
void searchAndCount(int key) {
    if (front == -1) {
        printf("Queue is empty.\n");
        return;
    }
    int i = front, count = 0, found = 0;
    printf("Searching for %d...\n", key);
    while (1) {
        if (queue[i] == key) {
            printf("Found at position %d\n", i);
            count++;
            found = 1;
        }
        if (i == rear) break;
        i = (i + 1) % size;
    }
    if (!found)
        printf("Element not found.\n");
    else
        printf("Total occurrences: %d\n", count);
}

// Display Queue
void displayQueue() {
    if (front == -1) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear) break;
        i = (i + 1) % size;
    }
    printf("\n");
}

int main() {
    int choice, data;

    printf("Enter the size of the Circular Queue: ");
    scanf("%d", &size);

    queue = (int *)malloc(size * sizeof(int));
    if (queue == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }

    while (1) {
        printf("\nMenu:\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Search and Count\n");
        printf("4. Display Queue\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                enqueue(data);
                break;
            case 2:
                dequeue();
                break;
            case 3:
                printf("Enter element to search: ");
                scanf("%d", &data);
                searchAndCount(data);
                break;
            case 4:
                displayQueue();
                break;
            case 5:
                printf("Exiting program.\n");
                free(queue);
                return 0;
            default:
                printf("Invalid choice! Try again.\n");
        }
    }
    return 0;
}

```

## Output:

```

```
