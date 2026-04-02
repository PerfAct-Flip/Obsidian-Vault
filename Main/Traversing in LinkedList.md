### **Traversing a Linked List in C**

Traversing means **going through each node (coach) in the train** and printing its data.

---

### **🚂 Simple Code for Traversing a Linked List**

```
#include <stdio.h>
#include <stdlib.h>

// Define a node (a coach in the train)
struct Node {
    int data;
    struct Node* next;
};

// Function to traverse and print the linked list
void traverse(struct Node* head) {
    struct Node* temp = head;  // Start at the engine (head)

    while (temp != NULL) {  // Keep moving until the last coach (NULL)
        printf("%d -> ", temp->data);  // Print the number inside the coach
        temp = temp->next;  // Move to the next coach
    }

    printf("NULL\n");  // End of the train
}

// Function to create a new node (coach)
struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;  // Store the number
    newNode->next = NULL;   // No next coach yet
    return newNode;
}

int main() {
    // Creating the train (linked list manually)
    struct Node* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);

    // Traversing and printing the train
    traverse(head);

    return 0;
}

```


---

### **🚀 Step-by-Step Explanation**

1. **struct Node** → Creates a **coach** with a number (`data`) and a hook (`next`).
2. **createNode()** → Creates a new coach and returns it.
3. **traverse()**
    - Starts at the **engine (head)**.
    - Moves coach by coach using `temp = temp->next`.
    - Prints each number (`temp->data`).
    - Stops when it reaches **NULL** (end of the train).
4. **main()**
    - Manually **creates a train** → `1 -> 2 -> 3 -> 4 -> NULL`.
    - Calls `traverse(head)` to **print** the train.

---

### **📌 Expected Output**

```
1 -> 2 -> 3 -> 4 -> NULL

```

💡 This shows the **train of nodes**, moving from coach to coach.