# Experiment 1:

> Write a C program that uses functions to perform the following operations on singly linked list:

- I. Creation
- II. Insertion
- III. Deletion
- IV. Traversal
- V. Merge two single linked lists

## I. Creation of a single linked list

```c
# include<stdio.h>
// For malloc
# include<stdlib.h> 

// Define the structure
struct node{
  int data;
  struct node *link;
};

// Function to create a new node
struct node* createNode(int value) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node)); // Allocate memory
    // if part is optional
    // if part is used to check if the memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    newNode->data = value; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

int main(){
  // Create a head pointer
  struct node *head = NULL;
  // Create the first node
  printf("Create the first node\n");
  printf("Enter the data: ");
  int data;
  scanf("%d", &data);
  head = createNode(10);

  printf("Print the data from the first node:\n");
  printf("%d\n", head->data);
  return 0;
}

```

## II. Insertion in a single linked list

> - Insertion at the beginning
> - Insertion at the end
> - Insertion at a specific position

### Insertion at the beginning

### Insertion at the end

### Insertion at a specific position
 
## III. Deletion in a single linked list

> - Deletion at the beginning
> - Deletion at the end
> - Deletion at a specific position

### Deletion at the beginning

### Deletion at the end

### Deletion at a specific position

## IV. Traversal of a single linked list
> - Traversal in forward direction only

## V. Merge two single linked lists
