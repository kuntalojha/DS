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
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node)); // Allocate memory
    // if part is optional
    // if part is used to check if the memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    newNode->data = data; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

int main(){
  // Create a head pointer
  struct node *head = NULL;
  int data;
  // Create the first node
  printf("Create the first node\n");
  printf("Enter the data: ");
  scanf("%d", &data);
  head = createNode(data);

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
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

// Function to add a node at the beginning
struct node* addAtBeginning(struct node *head, int data) {
    struct node *ptr = (struct node*)malloc(sizeof(struct node));
    ptr->data = data;
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

  // Add a node at the beginning with data 5
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
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data; // Assign data to the data part
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
# include<stdlib.h> // For malloc

// Define the structure
struct node{
  int data;
  struct node *link;
};

// Function to create a new node
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node)); // Allocate memory

    // if part is used to check if the memory allocation is successful
    if (newNode == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    newNode->data = data; // Assign data to the data part
    newNode->link = NULL; // Assign NULL to the link part
    return newNode;
}

// Function to display the linked list
void display(struct node *head){

   if(head == NULL){
     printf("Linked list is empty");
   }
   else{
    // Take a temporary pointer ptr
     struct node *ptr = NULL;
     ptr = head;

     while(ptr != NULL){
       printf("%d -> ",ptr->data);
       ptr = ptr->link;
     }
     printf("NULL\n");
   }
}

// Add a node at the Nth position
struct node* addAtNthPosition(struct node *head, int data, int position) {
    struct node *ptr = head;

    // Create a new node
    struct node *temp = (struct node*) malloc(sizeof(struct node));
    temp->data = data;
    temp->link = NULL;

    if(position == 1){
        temp->link = head;
        head = temp;

     return head;
    }

    for (int i = 1; i < position-1 && ptr != NULL; i++) {
        ptr = ptr->link;
    }

    temp->link = ptr->link;
    ptr->link = temp;

    return head;
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

  display(head);
  int data = 777;
  int position = 4;
  head = addAtNthPosition(head,data,position);


  //  Print all the nodes in the linked list
  display(head); // Function call and passing the head pointer as an argument

  return 0;
}
```

## III. Deletion in a single linked list

> 1. Deletion at the beginning
> 2. Deletion at the end
> 3. Deletion at a specific position

### 1. Deletion at the beginning

```c
#include <stdio.h>
#include <stdlib.h>

// Define the structure
struct node {
    int data;
    struct node *link;
};

// Function to create a new node
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->link = NULL;
    return newNode;
}

// Function to display the linked list
void display(struct node *head) {
    if (head == NULL) {
        printf("Linked list is empty\n");
    } else {
        struct node *ptr = head;
        while (ptr != NULL) {
            printf("%d -> ", ptr->data);
            ptr = ptr->link;
        }
        printf("NULL\n");
    }
}

// Function to delete a node at the beginning
struct node* deleteAtBeginning(struct node *head) {
    if (head == NULL) {
        printf("List is already empty!\n");
        return NULL;
    }

    struct node *ptr = head;
    head = head->link;
    free(ptr);

    return head;
}

int main() {
    struct node *head = NULL;

    // Create the first node
    head = createNode(10);

    // Create a second node
    struct node *temp = createNode(20);
    head->link = temp;

    // Create a third node
    temp = createNode(30);
    head->link->link = temp;

    // Delete the first node
    head = deleteAtBeginning(head);

    // Print all the nodes in the linked list
    display(head);

    return 0;
}

```

### 2. Deletion at the end

```c
#include <stdio.h>
#include <stdlib.h>

// Define the structure
struct node {
    int data;
    struct node *link;
};

// Function to create a new node
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return NULL;
    }
    newNode->data = data;
    newNode->link = NULL;
    return newNode;
}

// Function to display the linked list
void display(struct node *head) {
    if (head == NULL) {
        printf("Linked list is empty\n");
        return;
    }
    struct node *ptr = head;
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->link;
    }
    printf("NULL\n");
}

// Function to delete a node from the end
struct node* deleteAtEnd(struct node *head) {
    if (head == NULL) {
        printf("List is already empty.\n");
        return NULL;
    }

    if (head->link == NULL) { // Only one node in the list
        free(head);
        return NULL;
    }

    struct node *ptr = head;
    struct node *prev = NULL;

    while (ptr->link != NULL) {
        prev = ptr;
        ptr = ptr->link;
    }

    if (prev != NULL) {
        prev->link = NULL;
    }

    free(ptr);
    return head;
}

int main() {
    struct node *head = NULL;

    // Create nodes and link them
    head = createNode(10);
    head->link = createNode(20);
    head->link->link = createNode(30);

    printf("Original Linked List:\n");
    display(head);

    // Delete nodes from the end
    head = deleteAtEnd(head);
    printf("After deleting one node:\n");
    display(head);

    head = deleteAtEnd(head);
    printf("After deleting another node:\n");
    display(head);

    head = deleteAtEnd(head);
    printf("After deleting all nodes:\n");
    display(head);

    return 0;
}

```

### 3. Deletion at a specific position

```c
#include <stdio.h>
#include <stdlib.h>

// Define the structure
struct node {
    int data;
    struct node *link;
};

// Function to create a new node
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    if (!newNode) {
        printf("Memory allocation failed\n");
        return NULL;
    }
    newNode->data = data;
    newNode->link = NULL;
    return newNode;
}

// Function to display the linked list
void display(struct node *head) {
    if (head == NULL) {
        printf("Linked list is empty\n");
        return;
    }
    struct node *ptr = head;
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->link;
    }
    printf("NULL\n");
}

// Function to delete a node at a specific position
struct node* deleteAtPosition(struct node *head, int position) {
    if (head == NULL) {
        printf("List is empty, nothing to delete.\n");
        return NULL;
    }

    struct node *temp = head;

    // If deleting the first node
    if (position == 1) {
        head = head->link;
        free(temp);
        return head;
    }

    struct node *prev = NULL;
    int count = 1;

    // Traverse to the node at the given position
    while (temp != NULL && count < position) {
        prev = temp;
        temp = temp->link;
        count++;
    }

    // If position is greater than the number of nodes
    if (temp == NULL) {
        printf("Invalid position! No node deleted.\n");
        return head;
    }

    // Unlink the node and free memory
    prev->link = temp->link;
    free(temp);

    return head;
}

int main() {
    struct node *head = NULL;

    // Create nodes and link them
    head = createNode(10);
    head->link = createNode(20);
    head->link->link = createNode(30);
    head->link->link->link = createNode(40);

    printf("Original Linked List:\n");
    display(head);

    // Delete node at position 2
    head = deleteAtPosition(head, 2);
    printf("After deleting node at position 2:\n");
    display(head);

    // Delete node at position 1 (head)
    head = deleteAtPosition(head, 1);
    printf("After deleting node at position 1 (head):\n");
    display(head);

    // Delete last node
    head = deleteAtPosition(head, 2);
    printf("After deleting the last node:\n");
    display(head);

    return 0;
}
```

## IV. Traversal of a single linked list

> - Traversal in forward direction only

### Display the linked list

```c
// Function to display the linked list
void display(struct node *head) {
    if (head == NULL) {
        printf("Linked list is empty\n");
        return;
    }
    struct node *ptr = head;
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->link;
    }
    printf("NULL\n");
}
```

### Count the number of nodes

```c
// Function to count the number of nodes
int countNodes(struct node *head) {
    int count = 0;
    struct node *ptr = head;
    while (ptr != NULL) {
        count++;
        ptr = ptr->link;
    }
    return count;
}
```

## Experiment 1:

### Quuestion

- **Write a C program that uses functions to perform the following operations on singly linked list: I. Creation II. Insertion III. Deletion IV. Traversal V. merge two single linked lists**

### Program

```c
#include <stdio.h>
#include <stdlib.h>
// Define the structure
struct node {
    int data;
    struct node *link;
};
// Function to create a new node
struct node* createNode(int data) {
    struct node *newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->link = NULL;
    return newNode;
}

// Function to display the linked list
void display(struct node *head) {
    if (head == NULL) {
        printf("Linked list is empty\n");
        return;
    }
    struct node *ptr = head;
    while (ptr != NULL) {
        printf("%d -> ", ptr->data);
        ptr = ptr->link;
    }
    printf("NULL\n");
}

// Function to count the number of nodes in the linked list
void count (struct node *head){

  int count = 0;
  if(head == NULL){
     printf("Linked list is empty");
   }
  else{
    // Take a temporary pointer ptr
    struct node *ptr = NULL;
    ptr = head;

    while(ptr != NULL){
       count++;
       ptr = ptr->link;
    }
    printf("\nNumber of nodes: %d\n",count);
 }
 }

// Function to insert at the beginning
struct node* insertAtBeginning(struct node *head, int data) {
    struct node *newNode = createNode(data);
    newNode->link = head;
    return newNode;
}

// Function to insert at the end
struct node* insertAtEnd(struct node *head, int data) {
    struct node *newNode = createNode(data);
    if (head == NULL) return newNode;

    struct node *temp = head;
    while (temp->link != NULL){
        temp = temp->link;
    }
    temp->link = newNode;
    return head;
}

// Function to insert at a specific position
struct node* insertAtPosition(struct node *head, int data, int position) {
    if (position == 1){
        return insertAtBeginning(head, data);
    }

    struct node *newNode = createNode(data);
    struct node *temp = head;
    for (int i = 1; temp != NULL && i < position - 1; i++){
        temp = temp->link;
    }
    if (temp == NULL) {
        printf("Position out of range.\n");
        return head;
    }

    newNode->link = temp->link;
    temp->link = newNode;
    return head;
}

// Function to delete from the beginning
struct node* deleteFromBeginning(struct node *head) {
    if (head == NULL) {
        printf("List is empty.\n");
        return NULL;
    }
    struct node *temp = head;
    head = head->link;
    free(temp);
    return head;
}

// Function to delete from the end
struct node* deleteFromEnd(struct node *head) {
    if (head == NULL) {
        printf("List is empty.\n");
        return NULL;
    }
    if (head->link == NULL) {
        free(head);
        return NULL;
    }

    struct node *temp = head, *prev = NULL;
    while (temp->link != NULL) {
        prev = temp;
        temp = temp->link;
    }
    prev->link = NULL;
    free(temp);
    return head;
}

// Function to delete from a specific position
struct node* deleteFromPosition(struct node *head, int position) {
    if (head == NULL) {
        printf("List is empty.\n");
        return NULL;
    }

    struct node *temp = head;

    if (position == 1) {
        head = temp->link;
        free(temp);
        return head;
    }

    struct node *prev = NULL;
    for (int i = 1; temp != NULL && i < position; i++) {
        prev = temp;
        temp = temp->link;
    }

    if (temp == NULL) {
        printf("Position out of range.\n");
        return head;
    }

    prev->link = temp->link;
    free(temp);
    return head;
}

int main() {
    struct node *head = NULL;
    int choice, data, position;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Insert at Beginning\n");
        printf("2. Insert at End\n");
        printf("3. Insert at Position\n");
        printf("4. Delete from Beginning\n");
        printf("5. Delete from End\n");
        printf("6. Delete from Position\n");
        printf("7. Display List\n");
        printf("8. Count Nodes\n");
        printf("9. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                head = insertAtBeginning(head, data);
                break;

            case 2:
                printf("Enter data: ");
                scanf("%d", &data);
                head = insertAtEnd(head, data);
                break;

            case 3:
                printf("Enter data: ");
                scanf("%d", &data);
                printf("Enter position: ");
                scanf("%d", &position);
                head = insertAtPosition(head, data, position);
                break;

            case 4:
                head = deleteFromBeginning(head);
                printf("First node deleted.\n");
                break;

            case 5:
                head = deleteFromEnd(head);
                printf("Last node deleted.\n");
                break;

            case 6:
                printf("Enter position to delete: ");
                scanf("%d", &position);
                head = deleteFromPosition(head, position);
                printf("Node deleted from position %d.\n", position);
                break;

            case 7:
                printf("Linked List: ");
                display(head);
                break;

            case 8:
                printf("Count Nodes ");
                count(head);
                break;

            case 9:
                printf("Exiting program.\n");
                return 0;

            default:
                printf("Invalid choice! Try again.\n");
        }
    }
    return 0;
}
```

### Output:

```
Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 1
Enter data: 55

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 1
Enter data: 66

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 2
Enter data: 99

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 7
Linked List: 66 -> 55 -> 99 -> NULL

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 3
Enter data: 69
Enter position: 2

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 7
Linked List: 66 -> 69 -> 55 -> 99 -> NULL

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 8
Count Nodes
Number of nodes: 4

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 4
First node deleted.

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 7
Linked List: 69 -> 55 -> 99 -> NULL

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 5
Last node deleted.

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 7
Linked List: 69 -> 55 -> NULL

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 6
Enter position to delete: 3
Position out of range.
Node deleted from position 3.

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 6
Enter position to delete: 1
Node deleted from position 1.

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 7
Linked List: 55 -> NULL

Menu:
1. Insert at Beginning
2. Insert at End
3. Insert at Position
4. Delete from Beginning
5. Delete from End
6. Delete from Position
7. Display List
8. Count Nodes
9. Exit
Enter your choice: 9
Exiting program.
```

## V. Merge two single linked lists

```c
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct node {
    int data;
    struct node* next;
};

// Function to create a new node
struct node* createNode(int data) {
    struct node* newNode = (struct node*)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// Function to insert at the end of a list
struct node* insertAtEnd(struct node* head, int data) {
    struct node* newNode = createNode(data);
    if (head == NULL) {
        return newNode;
    }

    struct node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;

    return head;
}

// Function to merge two singly linked lists
struct node* mergeLists(struct node* head1, struct node* head2) {
    if (head1 == NULL) return head2;
    if (head2 == NULL) return head1;

    struct node* temp = head1;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = head2;  // Link last node of first list to head of second list

    return head1;
}

// Function to display the linked list
void displayList(struct node* head) {
    struct node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

// Main function with switch-case menu
int main() {
    struct node* head1 = NULL;
    struct node* head2 = NULL;
    int choice, value;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Insert into First Linked List\n");
        printf("2. Insert into Second Linked List\n");
        printf("3. Merge Linked Lists\n");
        printf("4. Display First Linked List\n");
        printf("5. Display Second Linked List\n");
        printf("6. Display Merged Linked List\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to insert into First Linked List: ");
                scanf("%d", &value);
                head1 = insertAtEnd(head1, value);
                break;

            case 2:
                printf("Enter value to insert into Second Linked List: ");
                scanf("%d", &value);
                head2 = insertAtEnd(head2, value);
                break;

            case 3:
                head1 = mergeLists(head1, head2);
                head2 = NULL; // Clear head2 since it's merged
                printf("Lists merged successfully!\n");
                break;

            case 4:
                printf("First Linked List: ");
                displayList(head1);
                break;

            case 5:
                printf("Second Linked List: ");
                displayList(head2);
                break;

            case 6:
                printf("Merged Linked List: ");
                displayList(head1);
                break;

            case 7:
                printf("Exiting program...\n");
                return 0;

            default:
                printf("Invalid choice! Please enter a valid option.\n");
        }
    }

    return 0;
}
```

### Output:

```
Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 1
Enter value to insert into First Linked List: 555

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 2
Enter value to insert into Second Linked List: 666

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 1
Enter value to insert into First Linked List: 999

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 2
Enter value to insert into Second Linked List: 888

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 4
First Linked List: 555 -> 999 -> NULL

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 5
Second Linked List: 666 -> 888 -> NULL

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 3
Lists merged successfully!

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 6
Merged Linked List: 555 -> 999 -> 666 -> 888 -> NULL

Menu:
1. Insert into First Linked List
2. Insert into Second Linked List
3. Merge Linked Lists
4. Display First Linked List
5. Display Second Linked List
6. Display Merged Linked List
7. Exit
Enter your choice: 7
Exiting program...
```
