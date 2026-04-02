### **🚂 Searching for an Element in a Linked List (C Code)**

To find an element, we **go through each coach (node)** and check if the number matches.

---

### **📜 C Code for Searching in a Linked List**

```c
#include <stdio.h>
#include <stdlib.h>

// Define a node (coach in the train)
struct Node {
    int data;
    struct Node* next;
};

// Function to search for an element in the linked list
int search(struct Node* head, int key) {
    struct Node* temp = head;  // Start from the engine (head)
    int position = 1;  // Position counter

    while (temp != NULL) {  // Move through the train
        if (temp->data == key) {  // If we find the number
            return position;  // Return its position
        }
        temp = temp->next;  // Move to the next coach
        position++;  // Increase position count
    }

    return -1;  // If not found, return -1
}

// Function to insert a new coach at the end
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

    traverse(head);

    int key = 30;
    int position = search(head, key);
    if (position != -1) {
        printf("Element %d found at position %d\\n", key, position);
    } else {
        printf("Element %d not found in the list\\n", key);
    }

    return 0;
}

```

---

### **🚀 Step-by-Step Explanation**

1. **search()**
    - Starts from `head`.
    - Moves through the **train** one node at a time.
    - If it finds `key`, it returns the **position**.
    - If it reaches **NULL** (end of train) without finding `key`, it returns `1`.
2. **addCoach()**
    - Adds a new coach at the **end** of the train.
3. **traverse()**
    - Prints the train structure (`10 -> 20 -> 30 -> 40 -> NULL`).
4. **main()**
    - Creates a linked list **(train)** with values `10, 20, 30, 40`.
    - Searches for **30** and prints its position.

---

### **📌 Expected Output**

```
10 -> 20 -> 30 -> 40 -> NULL
Element 30 found at position 3

```

If we search for a number not in the list (e.g., `50`):

```
Element 50 not found in the list

```

