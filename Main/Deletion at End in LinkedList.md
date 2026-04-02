### **🚂 Deletion at the End of a Linked List (C Code)**

To delete the **last node**, we need to:

1. Find the **second last node**.
2. Set its `next` pointer to **NULL** (unlink last node).
3. Free memory of the last node.

---

### **📜 C Code for Deleting the Last Node**

```c
#include <stdio.h>
#include <stdlib.h>

// Define a node (a coach in the train)
struct Node {
    int data;
    struct Node* next;
};

// Function to delete the last node
void deleteAtEnd(struct Node** head) {
    if (*head == NULL) {  // If train is empty
        printf("List is empty, nothing to delete.\n");
        return;
    }

    struct Node* temp = *head;

    // If only one node exists (engine only)
    if (temp->next == NULL) {
        free(temp);
        *head = NULL;
        return;
    }

    struct Node* prev = NULL;

    // Move to the second last node
    while (temp->next != NULL) {
        prev = temp;
        temp = temp->next;
    }

    prev->next = NULL;  // Unhook the last node
    free(temp);  // Remove last node
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
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;

    addCoach(&head, 10);
    addCoach(&head, 20);
    addCoach(&head, 30);
    addCoach(&head, 40);

    printf("Before deletion:\n");
    traverse(head);

    deleteAtEnd(&head);

    printf("After deleting the last node:\n");
    traverse(head);

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

4. **deleteAtEnd()**
    
    - If train is **empty**, print `"List is empty"`.
    - If train has **only one coach**, delete it and set `head = NULL`.
    - Otherwise, move to the **second last coach**.
    - **Unhook** the last coach and remove it.
5. **addCoach()** → Adds a new coach at the **end**.
    
6. **traverse()** → Prints the train.
    
7. **main()**
    
    - Creates a train: `10 -> 20 -> 30 -> 40 -> NULL`.
    - Deletes **last node (40)**.

---

### **📌 Expected Output**

```
Before deletion:
10 -> 20 -> 30 -> 40 -> NULL
After deleting the last node:
10 -> 20 -> 30 -> NULL
```

If the train has **only one coach (10)** before deletion:

```
Before deletion:
10 -> NULL
After deleting the last node:
List is empty
```
