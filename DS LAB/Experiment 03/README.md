# Experiment 3:

## Question:

- **Write a C program that implement stack operations using I.Arrays II. Linked Lists**

## I. Arrays:

## Program:

#include <stdio.h>
#include <stdlib.h>

int push(int stack[], int top, int data, int size) {
if (top == size - 1) {
printf("Stack is full / overflow. Cannot push.\n");
return top;
}
stack[++top] = data;
return top;
}

int pop(int top) {
if (top == -1) {
printf("Stack is empty / underflow. Cannot pop.\n");
return top;
}
top--;
return top;
}

void pick(int stack[], int top) {
if (top == -1) {
printf("Stack is empty. Cannot pick.\n");
return;
}
printf("Top element: %d\n", stack[top]);
}

void display(int stack[], int top) {
if (top == -1) {
printf("Stack is empty.\n");
return;
}

    printf("Stack: ");
    for (int i = 0; i <= top; i++) {
        printf("%d ", stack[i]);
    }
    printf("\n");

}

int main() {
int size;
printf("Enter the size of the stack: ");
scanf("%d", &size);
int stack[size]; // Declare stack after size is known

    int top = -1;
    int choice, data;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Pick\n");
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
                pick(stack, top);
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

## Output:

```




```

## II. Linked Lists:

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

int push(int stack[], int top, int data, int size) {
    if (top == size - 1) {
        printf("Stack is full / overflow. Cannot push.\n");
        return top;
    }
    stack[++top] = data;
    return top;
}

int pop(int top) {
    if (top == -1) {
        printf("Stack is empty / underflow. Cannot pop.\n");
        return top;
    }
    top--;
    return top;
}

void pick(int stack[], int top) {
    if (top == -1) {
        printf("Stack is empty. Cannot pick.\n");
        return;
    }
    printf("Top element: %d\n", stack[top]);
}

void display(int stack[], int top) {
    if (top == -1) {
        printf("Stack is empty.\n");
        return;
    }

    printf("Stack: ");
    for (int i = 0; i <= top; i++) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}

int main() {
    int size;
    printf("Enter the size of the stack: ");
    scanf("%d", &size);
    int stack[size];  // Declare stack after size is known

    int top = -1;
    int choice, data;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Pick\n");
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
                pick(stack, top);
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
