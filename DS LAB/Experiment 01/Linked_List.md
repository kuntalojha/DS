## Linked List Operations

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
