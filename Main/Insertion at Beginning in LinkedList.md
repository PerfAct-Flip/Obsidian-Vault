### **🚂 Insertion at the Beginning of a Linked List in C**

To insert at the beginning, we **create a new coach (node)** and make it the new **engine (head)**.

---

### **📜 Code for Inserting at the Beginning**

```c
#include <stdio.h>
#include <stdlib.h>

// Define a node (a coach in the train)
struct Node {
    int data;
    struct Node* next;
};

// Function to insert a new coach at the beginning
void insertAtBeginning(struct Node** head, int newData) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node)); // Create new coach
    newNode->data = newData;  // Put number inside the coach
    newNode->next = *head;    // Hook new coach to the old engine
    *head = newNode;          // Update engine (head) to this new coach
}

// Function to traverse and print the linked list (train)
void traverse(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\\n");
}

int main() {
    struct Node* head = NULL;  // Train starts empty

    insertAtBeginning(&head, 3); // New engine (3)
    insertAtBeginning(&head, 2); // New engine (2)
    insertAtBeginning(&head, 1); // New engine (1)

    traverse(head);  // Print train

    return 0;
}

```

---

### **🚀 Step-by-Step Explanation**

1. **struct Node** → Creates a coach with a number (`data`) and a hook (`next`).
2. **insertAtBeginning()**
    - Creates a new coach (`newNode`).
    - Hooks it **to the old engine** (`newNode->next = *head`).
    - Updates the engine (`head = newNode`).
3. **traverse()** → Moves coach by coach and prints numbers.
4. **main()**
    - Starts with an **empty train**.
    - Inserts **3** → Train: `3 -> NULL`
    - Inserts **2** → Train: `2 -> 3 -> NULL`
    - Inserts **1** → Train: `1 -> 2 -> 3 -> NULL`

---

### **📌 Expected Output**

```
1 -> 2 -> 3 -> NULL

```

💡 **New numbers always become the new engine!**