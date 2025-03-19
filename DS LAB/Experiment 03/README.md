# Experiment 3:

## Question:

- **Write a C program that implement stack operations using I.Arrays II. Linked Lists**

## I. Arrays:

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

// Push : Insert at top
int push(int stack[], int top, int data, int size) {
    if (top == size - 1) {
        printf("Stack is full / overflow. Cannot push.\n");
        return top;
    }
    stack[++top] = data;
    return top;
}

// Pop : Remove from top
int pop(int top) {
    if (top == -1) {
        printf("Stack is empty / underflow. Cannot pop.\n");
        return top;
    }
    top--;
    return top;
}

// Peek: Show top element
void peek(int stack[], int top) {
    if (top == -1) {
        printf("Stack is empty. Cannot peek.\n");
        return;
    }
    printf("Top element: %d\n", stack[top]);
}

void display(int stack[], int top) {
    int i;
    if (top == -1) {
        printf("Stack is empty.\n");
        return;
    }

    printf("Stack:\n");
    printf("-----\n");
    for (i = top; i >= 0; i--) {
        printf("| %d |\n", stack[i]);
    }
    printf("-----\n");
}

int main() {
    int size;
    printf("Enter the size of the stack: ");
    scanf("%d", &size);
    int stack[size];  // Declaring the stack using array.

    int top = -1;
    int choice, data;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Peek\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                top = push(stack, top, data, size);
                break;

            case 2:
                top = pop(top);
                break;

            case 3:
                peek(stack, top);
                break;

            case 4:
                display(stack, top);
                break;

            case 5:
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
