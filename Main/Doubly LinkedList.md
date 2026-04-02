### **🚂 Doubly Linked List in C**

A **Doubly Linked List (DLL)** is like a **two-way train** where each coach has:

1. **A number (`data`)**
2. **A hook to the next coach (`next`)**
3. **A hook to the previous coach (`prev`)**

This makes it easier to move **forward and backward** through the list.

---

## **📌 Operations in Doubly Linked List**

1. **Insertion at the Beginning**
2. **Insertion at the End**
3. **Deletion at the Beginning**
4. **Deletion at the End**
5. **Traversal (Forward & Backward)**

---

## **📜 C Code for Doubly Linked List**

```c
#include <stdio.h>
#include <stdlib.h>

// Define a node (coach in the train)
struct Node {
    int data;
    struct Node* next;
    struct Node* prev;
};

struct Node* head = NULL;  // Start of train

// Insert at the beginning
void insertAtBeginning(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = head;
    newNode->prev = NULL;

    if (head != NULL) head->prev = newNode;  // Update previous head
    head = newNode;  // Update head
}

// Insert at the end
void insertAtEnd(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;

    if (head == NULL) {  // If empty, new node becomes head
        newNode->prev = NULL;
        head = newNode;
        return;
    }

    struct Node* temp = head;
    while (temp->next != NULL) temp = temp->next;  // Move to last node

    temp->next = newNode;
    newNode->prev = temp;  // Set previous pointer
}

// Delete from the beginning
void deleteAtBeginning() {
    if (head == NULL) {
        printf("List is empty!\n");
        return;
    }

    struct Node* temp = head;
    head = head->next;  // Move head to next node

    if (head != NULL) head->prev = NULL;  // Update new head's prev
    free(temp);
}

// Delete from the end
void deleteAtEnd() {
    if (head == NULL) {
        printf("List is empty!\n");
        return;
    }

    struct Node* temp = head;
    if (temp->next == NULL) {  // If only one node
        free(head);
        head = NULL;
        return;
    }

    while (temp->next != NULL) temp = temp->next;  // Move to last node

    temp->prev->next = NULL;  // Unhook last node
    free(temp);
}

// Print forward
void traverseForward() {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

// Print backward
void traverseBackward() {
    struct Node* temp = head;
    if (temp == NULL) return;

    while (temp->next != NULL) temp = temp->next;  // Move to last node

    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->prev;
    }
    printf("NULL\n");
}

int main() {
    insertAtBeginning(10);
    insertAtBeginning(20);
    insertAtEnd(30);
    insertAtEnd(40);

    printf("Forward traversal:\n");
    traverseForward();

    printf("Backward traversal:\n");
    traverseBackward();

    deleteAtBeginning();
    printf("After deleting first node:\n");
    traverseForward();

    deleteAtEnd();
    printf("After deleting last node:\n");
    traverseForward();

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

1. **`insertAtBeginning(value)`**
    
    - Creates a new coach at the **front** of the train.
    - Hooks the **old head** to the new one.
2. **`insertAtEnd(value)`**
    
    - Moves to the **last coach** and adds a new one there.
3. **`deleteAtBeginning()`**
    
    - Moves the head to the **next** node and deletes the old head.
4. **`deleteAtEnd()`**
    
    - Moves to the **last coach** and removes it.
5. **`traverseForward()`**
    
    - Moves **forward** through the train, printing numbers.
6. **`traverseBackward()`**
    
    - Moves **backward** from the last coach.

---

### **📌 Expected Output**

```
Forward traversal:
20 -> 10 -> 30 -> 40 -> NULL

Backward traversal:
40 -> 30 -> 10 -> 20 -> NULL

After deleting first node:
10 -> 30 -> 40 -> NULL

After deleting last node:
10 -> 30 -> NULL
```

---

## **🚀 Why Use a Doubly Linked List?**

|Feature|Singly Linked List|Doubly Linked List|
|---|---|---|
|Memory|Less (one pointer per node)|More (two pointers per node)|
|Traversal|Forward only|Forward & backward|
|Deletion|Slower (must find previous node)|Faster (direct `prev` pointer)|

Would you like to add **insertion at a specific position**? 🚀😊