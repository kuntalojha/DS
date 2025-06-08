# Experiment 6:

## Question:

- **Write a C program to implement linear queue using I.Arrays II. Linked Lists**

## I. Arrays:

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

int *queue;
int front = -1, rear = -1, size = 0;

// Enqueue function
void enqueue(int data) {
    if (rear == size - 1) {
        printf("Queue is full (Overflow).\n");
        return;
    }
    if (front == -1) front = 0;
    queue[++rear] = data;
    printf("Enqueued element: %d\n", data);
}

// Dequeue function
void dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue is empty (Underflow).\n");
        return;
    }
    printf("Dequeued element: %d\n", queue[front++]);
    if (front > rear) front = rear = -1; // Reset
}

// Display front element
void showFront() {
    if (front == -1 || front > rear) {
        printf("Queue is empty.\n");
    } else {
        printf("Front element: %d\n", queue[front]);
    }
}

// Display rear element
void showRear() {
    if (rear == -1 || front > rear) {
        printf("Queue is empty.\n");
    } else {
        printf("Rear element: %d\n", queue[rear]);
    }
}

// Display entire queue
void displayQueue() {
    if (front == -1 || front > rear) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    for (int i = front; i <= rear; i++) {
        printf("%d ", queue[i]);
    }
    printf("\n");
}

int main() {
    int choice, data;

    printf("Enter the size of the queue: ");
    scanf("%d", &size);

    // Dynamically allocate memory for queue
    queue = (int *)malloc(size * sizeof(int));
    if (queue == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }

    while (1) {
        printf("\nMenu:\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Front\n");
        printf("4. Rear\n");
        printf("5. Display Queue\n");
        printf("6. Exit\n");
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
                showFront();
                break;
            case 4:
                showRear();
                break;
            case 5:
                displayQueue();
                break;
            case 6:
                printf("Exiting program.\n");
                free(queue); // Free allocated memory
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
## I. Linked Lists

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *link;
};

// Global front and rear pointers
struct node *front = NULL, *rear = NULL;

// Create a new node
struct node* createNode(int data) {
    struct node* newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->link = NULL;
    return newNode;
}

// Enqueue: Insert at rear
void enqueue(int data) {
    struct node* newNode = createNode(data);
    if (rear == NULL) {
        front = rear = newNode;
    } else {
        rear->link = newNode;
        rear = newNode;
    }
    printf("Enqueued element: %d\n", data);
}

// Dequeue: Remove from front
void dequeue() {
    if (front == NULL) {
        printf("Queue is empty.\n");
        return;
    }

    struct node* temp = front;
    front = front->link;

    if (front == NULL)
        rear = NULL;

    printf("Dequeued element: %d\n", temp->data);
    free(temp);
}

// Display front element
void showFront() {
    if (front == NULL) {
        printf("Queue is empty.\n");
    } else {
        printf("Front element: %d\n", front->data);
    }
}

// Display rear element
void showRear() {
    if (rear == NULL) {
        printf("Queue is empty.\n");
    } else {
        printf("Rear element: %d\n", rear->data);
    }
}

// Display all elements in the queue
void displayQueue() {
    if (front == NULL) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Queue elements: ");
    struct node* temp = front;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->link;
    }
    printf("\n");
}

int main() {
    int choice, data;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Front\n");
        printf("4. Rear\n");
        printf("5. Display Queue\n");
        printf("6. Exit\n");
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
                showFront();
                break;
            case 4:
                showRear();
                break;
            case 5:
                displayQueue();
                break;
            case 6:
                printf("Exiting program.\n");
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

















```

## II. Linked Lists:

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *link;
};

// Push: Insert at top
struct node* push(struct node *top, int data) {
    struct node *newNode = (struct node *)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->link = NULL;
    newNode->link = top; 
    return newNode; 
}

// Pop: Remove from top
struct node* pop(struct node *top) {
    struct node *temp = top;
    if (top == NULL) {
        printf("Can't pop. Stack is empty / underflow.\n");
        return NULL;
    }
    top = top->link; // Move top to next node
    printf("Popped element: %d\n", temp->data);
    free(temp); // Free memory
    return top;
}

// Peek: Show top element
void peek(struct node *top) {
    if (top == NULL) {
        printf("Stack is empty.\n");
        return;
    }
    printf("Top / Peek element: %d\n", top->data);
}

int main() {
    struct node *top = NULL; // Empty stack
    int choice, data;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Peek\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                top = push(top, data);
                break;

            case 2:
                top = pop(top);
                break;

            case 3:
                peek(top);
                break;
            case 4:
                printf("Exiting program.\n");
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
