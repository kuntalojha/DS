# Experiment 9:

## Question:

- **Write a C Program to implement AVL tree operations**

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *left;
    struct node *right;
    int height;
};

// Utility functions
int max(int a, int b) {
    return (a > b) ? a : b;
}

int getHeight(struct node *n) {
    if (n == NULL)
        return 0;
    return n->height;
}

int getBalanceFactor(struct node *n) {
    if (n == NULL)
        return 0;
    return getHeight(n->left) - getHeight(n->right);
}

struct node* createnode(int data) {
    struct node* node = (struct node*)malloc(sizeof(struct node));
    node->data = data;
    node->left = NULL;
    node->right = NULL;
    node->height = 1;
    return node;
}

// Rotations
struct node* rightRotate(struct node *y) {
    struct node *x = y->left;
    struct node *T2 = x->right;
    x->right = y;
    y->left = T2;
    y->height = max(getHeight(y->left), getHeight(y->right)) + 1;
    x->height = max(getHeight(x->left), getHeight(x->right)) + 1;
    return x;
}

struct node* leftRotate(struct node *y) {
    struct node *x = y->right;
    struct node *T2 = x->left;
    x->left = y;
    y->right = T2;
    y->height = max(getHeight(y->left), getHeight(y->right)) + 1;
    x->height = max(getHeight(x->left), getHeight(x->right)) + 1;
    return x;
}

// Insert into AVL Tree
struct node* insert(struct node* node, int data) {
    if (node == NULL)
        return createnode(data);

    if (data < node->data)
        node->left = insert(node->left, data);
    else if (data > node->data)
        node->right = insert(node->right, data);
    else
        return node; // Duplicate keys not allowed

    node->height = 1 + max(getHeight(node->left), getHeight(node->right));

    int bf = getBalanceFactor(node);

    // Rotation cases
    if (bf > 1 && data < node->left->data)
        return rightRotate(node);
    if (bf < -1 && data > node->right->data)
        return leftRotate(node);
    if (bf > 1 && data > node->left->data) {
        node->left = leftRotate(node->left);
        return rightRotate(node);
    }
    if (bf < -1 && data < node->right->data) {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }

    return node;
}

// Find max in left subtree (in-order predecessor)
struct node* findIOP(struct node* node) {
    struct node* current = node;
    while (current->right != NULL)
        current = current->right;
    return current;
}

// Delete from AVL Tree
struct node* deletenode(struct node* root, int data) {
    if (root == NULL)
        return root;

    if (data < root->data)
        root->left = deletenode(root->left, data);
    else if (data > root->data)
        root->right = deletenode(root->right, data);
    else {
        if (root->left == NULL || root->right == NULL) {
            struct node *temp = root->left ? root->left : root->right;
            if (temp == NULL) {
                temp = root;
                root = NULL;
            } else
                *root = *temp;
            free(temp);
        } else {
            struct node* temp = findIOP(root->left);
            root->data = temp->data;
            root->left = deletenode(root->left, temp->data);
        }
    }

    if (root == NULL)
        return root;

    root->height = 1 + max(getHeight(root->left), getHeight(root->right));
    int bf = getBalanceFactor(root);

    // Rotation cases after deletion
    if (bf > 1 && getBalanceFactor(root->left) >= 0)
        return rightRotate(root);
    if (bf > 1 && getBalanceFactor(root->left) < 0) {
        root->left = leftRotate(root->left);
        return rightRotate(root);
    }
    if (bf < -1 && getBalanceFactor(root->right) <= 0)
        return leftRotate(root);
    if (bf < -1 && getBalanceFactor(root->right) > 0) {
        root->right = rightRotate(root->right);
        return leftRotate(root);
    }

    return root;
}

// Traversals
void preOrder(struct node *root) {
    if (root != NULL) {
        printf("%d ", root->data);
        preOrder(root->left);
        preOrder(root->right);
    }
}

void inOrder(struct node *root) {
    if (root != NULL) {
        inOrder(root->left);
        printf("%d ", root->data);
        inOrder(root->right);
    }
}

// Main function with switch-case menu
int main() {
    struct node *root = NULL;
    int choice, val;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Insert\n");
        printf("2. Delete\n");
        printf("3. Display Preorder\n");
        printf("4. Display Inorder\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &val);
                root = insert(root, val);
                break;
            case 2:
                printf("Enter value to delete: ");
                scanf("%d", &val);
                root = deletenode(root, val);
                break;
            case 3:
                printf("Preorder traversal: ");
                preOrder(root);
                printf("\n");
                break;
            case 4:
                printf("Inorder traversal: ");
                inOrder(root);
                printf("\n");
                break;
            case 5:
                printf("Exiting...\n");
                exit(0);
            default:
                printf("Invalid choice. Try again.\n");
        }
    }

    return 0;
}
```

## Output:

```

```
