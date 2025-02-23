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

> 1. Insertion at the beginning
> 2. Insertion at the end
> 3. Insertion at a specific position

### 1. Insertion at the beginning

```c
# include<stdio.h>
# include<stdlib.h> // For malloc

// Define the structure
struct node{
  int data;
  struct node *link;
};

// Function to create a new node
struct node* createNode(int value) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = value; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

// Function to add a node at the beginning
struct node* addAtBeginning(struct node *head, int value) {
    struct node *ptr = (struct node*)malloc(sizeof(struct node));
    ptr->data = value;
    ptr->link = head;
    head = ptr;

    return head;
}

int main(){
  // Create a head pointer
  struct node *head = NULL;

  // Create the first node
  head = createNode(10);
  // Create a second node
  struct node *temp = createNode(20);
  // Link the first node to the second node
  head->link = temp;

  // Add a node at the beginning with value 5
  head = addAtBeginning(head, 5);

  // Print first node
  printf("%d -> ", head->data);
  // Print second node
  printf("%d -> ", head->link->data);
  // Print third node
  printf("%d", head->link->link->data);

  return 0;
}
```

### 2. Insertion at the end

```c
# include<stdio.h>
# include<stdlib.h> // For malloc

// Define the structure
struct node{
  int data;
  struct node *link;
};

// Function to create a new node
struct node* createNode(int value) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = value; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

void addAtEnd(struct node *head, int data) {
    struct node *ptr, *temp;
    ptr = head;

    // Create a new node using createNode function and assign data to it
    temp = createNode(data);

//--------------------------OR----------------------------/
    // temp = (struct node*)malloc(sizeof(struct node));
    // temp->data = data;
    // temp->link = NULL;
//------------------------------------------------------/

    while (ptr->link != NULL) {
        ptr = ptr->link;
    }
    ptr->link = temp;
}

int main(){
  // Create a head pointer
  struct node *head = NULL;

  // Create the first node
  head = createNode(10);
  // Create a second node
  struct node *temp = createNode(20);
  // Link the first node to the second node
  head->link = temp;

  // Create a third node
  temp = createNode(30);
  head->link->link = temp;


  // add a node at the end and this is the 4th node
  addAtEnd(head,999);


  // Print first node
  printf("%d -> ", head->data);
  // Print second node
  printf("%d -> ", head->link->data);
  // Print third node
  printf("%d", head->link->link->data);

  // Print fourth node
  printf(" -> %d", head->link->link->link->data);

  return 0;
}
```

### 3. Insertion at a specific position

```c
# include<stdio.h>
# include<stdlib.h>

// Define the structure
struct node{
  int data;
  struct node *link;
};

// Function to create a new node
struct node* createNode(int value) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node)); // Allocate memory

    // if part is used to check if the memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    newNode->data = value; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}


// Add a node at the Nth position
void addAtNthPosition(struct node *head, int value, int position) {

    struct node *ptr = head;
    struct node *temp = (struct node*) malloc(sizeof(struct node));
    temp->data = value;
    temp->link = NULL;

    for (int i = 1; i < position; i++) {
        ptr = ptr->link;
    }
    temp->link = ptr->link;
    ptr->link = temp;
}

int main(){

  struct node *head = NULL;
  // Create the first node
  head = createNode(10);
  // Create a second node
  struct node *temp = createNode(20);
  // Link the first node to the second node
  head->link = temp;

  // Create a third node
  temp = createNode(30);
  head->link->link = temp;


  int data = 777;
  int position = 2;
  // Add a node at the Nth position
  addAtNthPosition(head,data,position);


  //  Print all the nodes in the linked list
  printf("%d -> ", head->data); // Print first node
  printf("%d -> ", head->link->data); // Print second node
  printf("%d", head->link->link->data); // Print third node
  printf(" -> %d", head->link->link->link->data); // Print fourth node
  return 0;
}



```

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
