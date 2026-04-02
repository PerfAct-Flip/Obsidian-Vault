
**Operations**
 1. [[Traversing in LinkedList]]
 2. [[Insertion at Beginning in LinkedList]]
 3. [[Searching in LinkedList]]
 4. [[Deletion at Specified Position in LinkedList]]
 5. [[Deletion at End in LinkedList]]
 
TYPES:-

1. [[Doubly LinkedList]]




```
#include <stdio.h>
#include <stdlib.h>

// Each coach (node) has a number and a pointer to the next coach
struct Node {
    int data;
    struct Node* next;
};

// Function to add a new coach (node) at the end
void addCoach(struct Node** head, int newData) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = newData;
    newNode->next = NULL;

    if (*head == NULL) {  // If train has no coaches
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL) {  // Move to the last coach
        temp = temp->next;
    }
    temp->next = newNode;  // Attach new coach at the end
}

// Function to print the train
void printTrain(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\\n");
}

// Main function
int main() {
    struct Node* head = NULL;  // Train starts empty

    addCoach(&head, 1);  // Add coach 1
    addCoach(&head, 2);  // Add coach 2
    addCoach(&head, 3);  // Add coach 3

    printTrain(head);  // Print train

    return 0;
}

```

---

---

### **Code Explanation:**

```c
#include <stdio.h>
#include <stdlib.h>

```

- `#include <stdio.h>` → This helps us use `printf()` to show things on the screen.
- `#include <stdlib.h>` → This helps us use `malloc()` to create new nodes (coaches).

---

```c
struct Node {
    int data;
    struct Node* next;
};

```

- **struct Node** → Think of it as a **blueprint** for making a coach.
- `int data;` → This is the **number** inside the coach.
- `struct Node* next;` → This is a **hook** that points to the next coach.

💡 If there’s no next coach, this hook is **NULL** (empty).

---

```c
void addCoach(struct Node** head, int newData) {

```

- This function **adds a new coach** to the train.
- `struct Node** head` → This is the **engine** (start of the train).
- `int newData` → This is the number for the new coach.

---

```c
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

```

- `malloc(sizeof(struct Node))` → **Makes space for a new coach.**
- `newNode->data = newData;` → Puts a number inside the coach.
- `newNode->next = NULL;` → Sets the hook to NULL (for now, it's alone).

---

```c
    if (*head == NULL) {  // If train has no coaches
        *head = newNode;
        return;
    }

```

- If the train has **no coaches**, the new coach **becomes the first** one.
- `head = newNode;` → The engine now points to this new coach.
- `return;` → Stops here because we added the first coach.

---

```c
    struct Node* temp = *head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

```

- This finds the **last coach** in the train.
- `temp = temp->next;` moves **one coach ahead** until we reach the last one.

---

```c
    temp->next = newNode;

```

- The last coach **hooks onto** the new coach.

---

```c
void printTrain(struct Node* head) {
    struct Node* temp = head;

```

- This function **prints the train** from start to end.
- `temp = head;` → Start from the engine.

---

```c
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }

```

- **Moves from coach to coach**, printing each number.
- Stops when `temp = NULL` (end of the train).

---

```c
    printf("NULL\\n");

```

- Prints **"NULL"** to show the end of the train.

---

```c
int main() {
    struct Node* head = NULL;

```

- The train starts **empty** (`head = NULL`).

---

```c
    addCoach(&head, 1);  // Add coach 1
    addCoach(&head, 2);  // Add coach 2
    addCoach(&head, 3);  // Add coach 3

```

- Adds **three coaches** to the train (1 → 2 → 3).

---

```c
    printTrain(head);  // Print train
    return 0;
}

```

- Calls `printTrain()` to show the train.
- `return 0;` → Ends the program.

---

### **Final Train Output:**

```
1 -> 2 -> 3 -> NULL

```

- `1 -> 2 -> 3` → Coaches linked together.
- `NULL` → End of the train.

Let me know if any part is still confusing! 🚂😊



