# Experiment 10:

## Question:

- **Implementation of a Graph representation using Adjacency Matrix**

## Program:

```c
#include <stdio.h>
#define V 5  // constant

void init(int arr[][V]) {
    for (int i = 0; i < V; i++)
        for (int j = 0; j < V; j++)
            arr[i][j] = 0;
}

void addEdge(int arr[][V], int src, int dest) {
    arr[src][dest] = 1;
}

void printAdjMatrix(int arr[][V]) {
    for (int i = 0; i < V; i++) {
        for (int j = 0; j < V; j++)
            printf("%d ", arr[i][j]);
        printf("\n");
    }
}

int main() {
    int adjMatrix[V][V];
    int x, y, n;

    init(adjMatrix);

    printf("Enter number of edges: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        printf("Enter vertices of edge %d: ", i);
        scanf("%d%d", &x, &y);
        addEdge(adjMatrix, x, y);
        addEdge(adjMatrix, y, x); // for undirected graph
    }

    printf("\nAdjacency Matrix:\n");
    printAdjMatrix(adjMatrix);

    return 0;
}

```

## Output:

```

```
