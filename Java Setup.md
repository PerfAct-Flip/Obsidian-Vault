
---

**Method 1: Manual File Creation and Execution via Terminal**

1. Create a `.java` file (e.g., `MyProgram.java`)
    
2. Write the following code inside it:
    

```java
public class MyProgram {
    public static void main(String[] args) {
        // Your code here
    }
}
```

3. Open terminal and run:
    

```bash
javac MyProgram.java   // Compiles the code
java MyProgram         // Runs the program
```

> **Note:** The filename and public class name must match (e.g., `MyProgram.java` must have `public class MyProgram`).

---

**Method 2: Using VS Code Java Extension**

1. Press `Ctrl + Shift + P`
    
2. Search and select **"Java: Create Java Project"**
    
3. Choose **"No Build Tools"** if you're not using Maven or Gradle.
    
4. VS Code will scaffold the project.
    
5. You can click the **Run button** above the `main` method to execute it directly.
    
6. Alternatively, you can still use the **Terminal** with:
    

```bash
java <filename>.java
```

