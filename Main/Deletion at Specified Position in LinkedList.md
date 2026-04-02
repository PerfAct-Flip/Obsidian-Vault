### **🚂 Deletion at a Specified Position in a Linked List (C Code)**

To delete a node at a given position, we need to:

1. Find the node **just before** the target node.
2. Adjust its `next` pointer to **skip** the target node.
3. Free the memory of the deleted node.

---

### **📜 C Code for Deleting at a Given Position**

```c
#include <stdio.h>
#include <stdlib.h>

// Define a node (coach in the train)
struct Node {
    int data;
    struct Node* next;
};

// Function to delete a node at a given position
void deleteAtPosition(struct Node** head, int position) {
    if (*head == NULL) {  // If train is empty
        printf("List is empty, nothing to delete.\\n");
        return;
    }

    struct Node* temp = *head;

    // If deleting the first node (engine)
    if (position == 1) {
        *head = temp->next;  // Move head to next coach
        free(temp);  // Remove old engine
        return;
    }

    struct Node* prev = NULL;
    int count = 1;

    // Traverse to find the node before the target
    while (temp != NULL && count < position) {
        prev = temp;
        temp = temp->next;
        count++;
    }

    // If position is invalid
    if (temp == NULL) {
        printf("Invalid position!\\n");
        return;
    }

    prev->next = temp->next;  // Unhook the target coach
    free(temp);  // Remove the target coach
}

// Function to add a new coach at the end
void addCoach(struct Node** head, int newData) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = newData;
    newNode->next = NULL;

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Function to traverse and print the train
void traverse(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\\n");
}

int main() {
    struct Node* head = NULL;

    addCoach(&head, 10);
    addCoach(&head, 20);
    addCoach(&head, 30);
    addCoach(&head, 40);

    printf("Before deletion:\\n");
    traverse(head);

    int pos = 2;
    deleteAtPosition(&head, pos);

    printf("After deleting at position %d:\\n", pos);
    traverse(head);

    return 0;
}

```

---

### **🚀 Step-by-Step Explanation**

4. **deleteAtPosition()**
    - If the train is empty, prints "List is empty".
    - If deleting the **first coach (head)**, moves head to the next coach and removes the old one.
    - Otherwise, it moves through the train to **find the coach before the target**.
    - Adjusts pointers to **skip the target coach** and removes it.
5. **addCoach()** → Adds a new coach at the **end** of the train.
6. **traverse()** → Prints the train structure.
7. **main()**
    - Creates a linked list **(train)**: `10 -> 20 -> 30 -> 40`.
    - Deletes the coach at **position 2** (`20`).

---

### **📌 Expected Output**

```
Before deletion:
10 -> 20 -> 30 -> 40 -> NULL
After deleting at position 2:
10 -> 30 -> 40 -> NULL

```

If you try to delete an **invalid position** (e.g., `5`):
```
Invalid position!

```

