 Overview
This project demonstrates how to **delete a node by value** in a **Singly Linked List** using C programming.

In a singly linked list:
- Each node contains data and a pointer to the next node.
- Deletion requires updating the links and freeing the memory of the removed node.

This program:
1. Creates a sample linked list: `10 → 20 → 30`
2. Deletes a node with a given value.
3. Displays the updated linked list.

---

 Source Code

```c
#include <stdio.h>
#include <stdlib.h>

// Define structure
struct Node {
    int data;
    struct Node* next;
};

// Function to delete a node by value
struct Node* deleteNode(struct Node* head, int key) {
    struct Node *temp = head, *prev = NULL;

    // If head node itself holds the key
    if (temp != NULL && temp->data == key) {
        head = temp->next;
        free(temp);
        return head;
    }

    // Search for the key
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    // If key not present
    if (temp == NULL) {
        printf("Value not found in list.\n");
        return head;
    }

    // Unlink the node
    prev->next = temp->next;
    free(temp);

    return head;
}

// Function to display linked list
void traverse(struct Node* head) {
    while (head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }
}

int main() {
    struct Node* head = NULL;

    // Creating sample list: 10 -> 20 -> 30
    struct Node* n1 = (struct Node*)malloc(sizeof(struct Node));
    struct Node* n2 = (struct Node*)malloc(sizeof(struct Node));
    struct Node* n3 = (struct Node*)malloc(sizeof(struct Node));

    n1->data = 10; n1->next = n2;
    n2->data = 20; n2->next = n3;
    n3->data = 30; n3->next = NULL;

    head = n1;

    printf("Original List:\n");
    traverse(head);

    // Delete node with value 20
    head = deleteNode(head, 20);

    printf("\nList after deletion:\n");
    traverse(head);

    return 0;
}
```

---

 Explanation

 deleteNode()
- Checks if the head node contains the value.
- Searches for the node containing the key.
- Updates the previous node's pointer.
- Frees the memory of the deleted node.
- Returns the updated head.

 traverse()
- Iterates through the list.
- Prints each element until `NULL`.

---

 Sample Output

```
Original List:
10 20 30
List after deletion:
10 30
```

---

 Time Complexity
- Deletion (Worst Case): **O(n)**
- Traversal: **O(n)**

---

 Compile:
```
gcc delete_node.c -o delete
```

 Run:
```
./delete
```

---

Concepts Used
- Structures in C
- Pointers
- Dynamic Memory Allocation (`malloc`, `free`)
- Linked List Traversal
