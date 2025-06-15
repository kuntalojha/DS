# Experiment 8:

## Question:

- **Write a C Program to implement binary tree traversals**

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

// Define the structure for a tree node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* newNode(int data) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    return node;
}

// Inorder traversal (Left-Root-Right)
void inOrder(struct Node* node) {
    if (node == NULL) return;
    inOrder(node->left);
    printf("%d ", node->data);
    inOrder(node->right);
}

// Preorder traversal (Root-Left-Right)
void preOrder(struct Node* node) {
    if (node == NULL) return;
    printf("%d ", node->data);
    preOrder(node->left);
    preOrder(node->right);
}

// Postorder traversal (Left-Right-Root)
void postOrder(struct Node* node) {
    if (node == NULL) return;
    postOrder(node->left);
    postOrder(node->right);
    printf("%d ", node->data);
}

// Main function
int main() {
    // Create a sample binary tree
    struct Node* root = newNode(1);
    root->left = newNode(2);
    root->right = newNode(3);
    root->left->left = newNode(4);
    root->left->right = newNode(5);
    
    printf("Binary Tree Traversals:\n");
    printf("Inorder traversal: ");
    inOrder(root);
    printf("\n");

    printf("Preorder traversal: ");
    preOrder(root);
    printf("\n");

    printf("Postorder traversal: ");
    postOrder(root);
    printf("\n");

    return 0;
}
```

## Output:

```

```
