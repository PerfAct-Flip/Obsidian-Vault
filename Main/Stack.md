### **📚 Stack Implementation in C**

A **stack** is like a pile of plates—**last in, first out (LIFO)**. We can implement a stack using:

1. **Array** (fixed size, fast access).
2. **Linked List** (dynamic size, more flexible).

---

## **📌 Stack Using Array**

### **🔥 How it Works**

- **Push (Add an element)** → Insert at `top` index.
- **Pop (Remove an element)** → Remove from `top` index.
- **Peek (See top element)** → Show element at `top`.
- **IsEmpty (Check if stack is empty)** → Check if `top == -1`.

---

### **📜 C Code for Stack Using Array**

```c
#include <stdio.h>
#define MAX 5  // Maximum stack size

int stack[MAX];  // Array to store stack elements
int top = -1;    // Top of stack (-1 means empty)

// Push operation
void push(int value) {
    if (top == MAX - 1) {  // Stack is full
        printf("Stack Overflow!\n");
        return;
    }
    stack[++top] = value;  // Increase top and insert value
}

// Pop operation
void pop() {
    if (top == -1) {  // Stack is empty
        printf("Stack Underflow!\n");
        return;
    }
    top--;  // Decrease top (removes element)
}

// Peek operation (get top element)
int peek() {
    if (top == -1) {
        printf("Stack is empty!\n");
        return -1;
    }
    return stack[top];  // Return top element
}

// Check if stack is empty
int isEmpty() {
    return top == -1;
}

// Print stack elements
void display() {
    if (top == -1) {
        printf("Stack is empty!\n");
        return;
    }
    for (int i = top; i >= 0; i--) {
        printf("%d\n", stack[i]);
    }
}

int main() {
    push(10);
    push(20);
    push(30);
    display();

    printf("Top element: %d\n", peek());

    pop();
    display();

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

1. `push(value)` → Adds `value` at `top`.
2. `pop()` → Removes `top` element.
3. `peek()` → Shows top element.
4. `display()` → Prints stack elements.
5. **Main function**
    - Pushes `10, 20, 30`
    - Pops `30`, so stack becomes `10, 20`.

---

### **📌 Expected Output**

```
30
20
10
Top element: 30
20
10
```

---

## **📌 Stack Using Linked List**

### **🔥 How it Works**

- **Push** → Insert at **head** (top of stack).
- **Pop** → Remove from **head** (top of stack).
- **Peek** → Show `head->data`.
- **IsEmpty** → Check if `head == NULL`.

---

### **📜 C Code for Stack Using Linked List**

```c
#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

struct Node* top = NULL;  // Top of stack

// Push operation
void push(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = top;  // Link new node to previous top
    top = newNode;  // Update top
}

// Pop operation
void pop() {
    if (top == NULL) {
        printf("Stack Underflow!\n");
        return;
    }
    struct Node* temp = top;
    top = top->next;  // Move top to next node
    free(temp);  // Delete old top
}

// Peek operation
int peek() {
    if (top == NULL) {
        printf("Stack is empty!\n");
        return -1;
    }
    return top->data;
}

// Check if stack is empty
int isEmpty() {
    return top == NULL;
}

// Display stack
void display() {
    struct Node* temp = top;
    while (temp != NULL) {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
}

int main() {
    push(10);
    push(20);
    push(30);
    display();

    printf("Top element: %d\n", peek());

    pop();
    display();

    return 0;
}
```

---

### **🚀 Step-by-Step Explanation**

6. `push(value)` → Creates a **new node** and makes it `top`.
7. `pop()` → Removes `top` and updates `top = top->next`.
8. `peek()` → Shows `top->data`.
9. `display()` → Prints all stack elements.
10. **Main function**
    - Pushes `10, 20, 30`
    - Pops `30`, so stack becomes `10, 20`.

---

### **📌 Expected Output**

```
30
20
10
Top element: 30
20
10
```

---

## **🚀 Comparison: Array vs. Linked List**

|Feature|Array-Based Stack|Linked List Stack|
|---|---|---|
|Size Limit|Fixed (MAX size)|Dynamic (No limit)|
|Memory Usage|Uses extra space even if empty|Uses space only when needed|
|Speed|Faster (direct index access)|Slower (pointer operations)|
|Implementation|Simpler|More flexible|

---

### **📌 Which One to Use?**

✔ **Use Array** if size is known and speed matters.  
✔ **Use Linked List** if size is **unknown** and flexibility is needed.

