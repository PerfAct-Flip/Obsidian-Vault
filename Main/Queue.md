### **🚂 Queue Implementation in C**

A **queue** works like a **line at a ticket counter** → **First In, First Out (FIFO)**.  
We can implement a queue using:

1. **Array** (fixed size, faster access).
2. **Linked List** (dynamic size, more flexible).

---

## **📌 Queue Using Array**

### **🔥 How it Works**

- **Enqueue (Add an element)** → Insert at **rear**.
- **Dequeue (Remove an element)** → Remove from **front**.
- **Peek (See front element)** → Show element at `front`.
- **IsEmpty (Check if queue is empty)** → `front == -1`.

---

### **📜 C Code for Queue Using Array**

```c
#include <stdio.h>
#define MAX 5  // Maximum queue size

int queue[MAX];  // Array to store queue elements
int front = -1, rear = -1;  // Front and rear pointers

// Enqueue operation (add element)
void enqueue(int value) {
    if (rear == MAX - 1) {  // Queue is full
        printf("Queue Overflow!\n");
        return;
    }
    if (front == -1) front = 0;  // Set front to 0 if first element is added
    queue[++rear] = value;  // Insert at rear
}

// Dequeue operation (remove element)
void dequeue() {
    if (front == -1 || front > rear) {  // Queue is empty
        printf("Queue Underflow!\n");
        return;
    }
    front++;  // Move front forward (removes element)
}

// Peek operation (get front element)
int peek() {
    if (front == -1 || front > rear) {
        printf("Queue is empty!\n");
        return -1;
    }
    return queue[front];  // Return front element
}

// Print queue elements
void display() {
    if (front == -1 || front > rear) {
        printf("Queue is empty!\n");
        return;
    }
    for (int i = front; i <= rear; i++) {
        printf("%d ", queue[i]);
    }
    printf("\n");
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();

    printf("Front element: %d\n", peek());

    dequeue();
    display();

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

1. `enqueue(value)` → Adds `value` at **rear**.
2. `dequeue()` → Removes **front** element.
3. `peek()` → Shows **front** element.
4. `display()` → Prints queue elements.
5. **Main function**
    - Enqueues `10, 20, 30`.
    - Dequeues `10`, so queue becomes `20, 30`.

---

### **📌 Expected Output**

```
10 20 30
Front element: 10
20 30
```

---

## **📌 Queue Using Linked List**

### **🔥 How it Works**

- **Enqueue** → Insert at **rear** (end).
- **Dequeue** → Remove from **front** (start).
- **Peek** → Show `front->data`.
- **IsEmpty** → Check if `front == NULL`.

---

### **📜 C Code for Queue Using Linked List**

```c
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

struct Node* front = NULL;
struct Node* rear = NULL;

// Enqueue operation (add element)
void enqueue(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;
    
    if (rear == NULL) {  // If queue is empty
        front = rear = newNode;
        return;
    }
    
    rear->next = newNode;  // Link new node to rear
    rear = newNode;  // Update rear
}

// Dequeue operation (remove element)
void dequeue() {
    if (front == NULL) {
        printf("Queue Underflow!\n");
        return;
    }
    
    struct Node* temp = front;
    front = front->next;  // Move front to next node
    
    if (front == NULL) rear = NULL;  // If queue becomes empty
    free(temp);  // Delete old front node
}

// Peek operation
int peek() {
    if (front == NULL) {
        printf("Queue is empty!\n");
        return -1;
    }
    return front->data;
}

// Print queue
void display() {
    struct Node* temp = front;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();

    printf("Front element: %d\n", peek());

    dequeue();
    display();

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

6. `enqueue(value)` → Creates a **new node** and makes it `rear`.
7. `dequeue()` → Removes `front` and updates `front = front->next`.
8. `peek()` → Shows `front->data`.
9. `display()` → Prints all queue elements.
10. **Main function**
    - Enqueues `10, 20, 30`.
    - Dequeues `10`, so queue becomes `20, 30`.

---

### **📌 Expected Output**

```
10 20 30
Front element: 10
20 30
```

---

## **🚀 Comparison: Array vs. Linked List**

|Feature|Array-Based Queue|Linked List Queue|
|---|---|---|
|Size Limit|Fixed (MAX size)|Dynamic (No limit)|
|Memory Usage|Uses extra space even if empty|Uses space only when needed|
|Speed|Faster (direct index access)|Slower (pointer operations)|
|Implementation|Simpler|More flexible|

---

### **📌 Which One to Use?**

✔ **Use Array** if size is known and speed matters.  
✔ **Use Linked List** if size is **unknown** and flexibility is needed.
