
# A First Simple Program

---

## 🚀 Objective

This week introduces your **first working Java program**, breaking it down piece by piece, explaining its structure, syntax, and how to compile and run it using the **Java Development Kit (JDK)**.

---

## 🧾 First Java Program Example

```java
/*
This is a simple Java program.
Call this file "Example.java".
*/
public class Example {
    // Your program begins with a call to main().
    public static void main(String[] args) {
        System.out.println("This is a simple Java program.");
    }
}
```

### ✅ Expected Output:

```
This is a simple Java program.
```

> 📌 This is the most basic skeleton of a Java program: **one class** and **one main() method**.

---

## 📄 File Naming Rules

- Java source files **must end in `.java`**.
    
- The **filename must match the public class name** exactly — including **capitalization**.
    
    - Example: Class name = `Example`, filename = `Example.java`
        
- Java is **case-sensitive**. `Example.java` ✔️, `example.java` ❌
    

> 🧠 Why? Because the compiled `.class` file needs to match the class name to be executable.

---

## 🔄 Compilation & Execution Steps (Terminal-Based)

|Step|Command|Result|
|---|---|---|
|1️⃣ Compile|`javac Example.java`|Creates `Example.class` (bytecode)|
|2️⃣ Execute|`java Example`|Runs the program|

> ⚠️ Do NOT use the `.class` extension in `java Example`.

> 🆕 Since JDK 11, you can also directly run simple programs:

```bash
java Example.java
```

---

## 🧱 Anatomy of the Program

### 1. 📌 Multiline Comment

```java
/*
This is a simple Java program.
Call this file "Example.java".
*/
```

- Begins with `/*`, ends with `*/`.
    
- Used for long explanations or documentation.
    
- Ignored by the compiler.
    

### 2. 📦 Class Declaration

```java
public class Example {
    // ...
}
```

- Declares a **new class** named `Example`.
    
- All Java code must live **inside a class** — no exceptions.
    
- Everything inside `{}` belongs to the class.
    

---
### 3. 🧵 Single-Line Comment

```java
// Your program begins with a call to main().
```

- Begins with `//`, ends at the line's end.
    
- Great for **inline explanations**.
    

### 4. 🧩 Main Method Declaration

```java
public static void main(String[] args) {
    // body
}
```

#### 🔍 Breakdown:

|Keyword|Meaning|
|---|---|
|`public`|Accessible from outside the class (required by JVM)|
|`static`|No object needed to call this method|
|`void`|Returns no value|
|`main`|Special name: JVM starts here|
|`String[] args`|Receives command-line arguments|

> 🚨 `Main` ≠ `main`. Java is **case-sensitive**!

---

## 🖨️ The println() Statement

```java
System.out.println("This is a simple Java program.");
```

- `System`: Predefined class.
    
- `out`: Standard output stream (console).
    
- `println()`: Method that prints followed by a new line.
    

### More Examples

```java
System.out.println("Hello, world!");
System.out.println(42);
System.out.println(3.14);
System.out.println(true);
```

#### ✅ Expected Output:

```
Hello, world!
42
3.14
true
```

> 🧠 println() can print: **Strings, integers, floats, booleans, objects**...

---

## 🗃️ Summary of Java Comment Types

|Type|Syntax|Purpose|
|---|---|---|
|Multiline|`/* ... */`|Long documentation blocks|
|Single-line|`//`|Quick line comments|
|Documentation|`/** ... */`|Used with `javadoc` tool for API docs|

> ✨ Use comments wisely to keep code **clear**, **maintainable**, and **team-friendly**.

---

## 🌐 Real-World Uses of Basic Console Java

- ✅ Learning and teaching
    
- ✅ Writing utility tools/scripts
    
- ✅ Server-side debugging logs
    
- ❌ GUI-based apps (use JavaFX/Swing instead)
    
---
## 📚 Further Reading

| Topic             | Link                                                                            |
| ----------------- | ------------------------------------------------------------------------------- |
| Java API Docs     | [Oracle Java SE Docs](https://docs.oracle.com/en/java/javase/17/docs/api/)      |
| JDK Download      | [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html)    |
| Java Tutorials    | [Learn Java (Official)](https://dev.java/learn)                                 |
| Try Java Online   | [Replit Java](https://replit.com/languages/java10)                              |
| Command Line Java | [Baeldung Java CLI Guide](https://www.baeldung.com/java-command-line-arguments) |

---

## 📄 Writing Java Source Code

Java source code is saved in plain text files with the `.java` extension.

> ✅ **Important**: The file name **must match** the public class name it contains (case-sensitive).

### 🔤 Rules:

- Extension must be `.java` only (not `.txt`, `.doc`, etc.)
    
- Only one public class per file
    

### 📌 Example:

```java
// Welcome.java
public class Welcome {
    public static void main(String[] args) {
        System.out.println("Welcome to Java 17!");
    }
}
```

**✅ Valid filename**: `Welcome.java`

---

## 📁  Java Project Directory Structure

For the `javafun` project (from the book):

```bash
javafun/
├── src/      # Java source code (.java files)
├── mod/      # Compiled module files (.class files)
└── lib/      # Packaged libraries (JARs)
```

> 🔍 Helps organize source, compiled, and external code

### 🧭 Module `jdojo.intro` Example Structure:

```
src/
└── jdojo.intro/
    ├── module-info.java
    └── com/
        └── jdojo/
            └── intro/
                └── Welcome.java
```

---

## 📦 Module Declaration (JDK 9+)

### 🧱 What is a Module?

A **module** is a group of related packages with a controlled access mechanism.

### 📜 Syntax:

```java
module module.name {
    // requires, exports, etc.
}
```

### 📘 Example:

```java
// module-info.java
module jdojo.intro {
    // Empty body
}
```

> ✅ **`java.base`** module is implicitly required by all modules.

### 📚 Module Dependencies

If Module A wants to use Module B:

```java
module A {
    requires B;
}
```

- `B` must `exports` the relevant packages
    

### 🚨 Rules:

- Unnamed packages are **not allowed** in modules
    
- `module-info.java` must be at the **root** of the module source folder
    

---

## 🧩 Compilation Unit Structure

Each `.java` file follows this strict structure:

1. `package` declaration (optional but mandatory in modules)
    
2. `import` statements (optional)
    
3. One or more type declarations (class, interface, etc.)
    

### 🧪 Example:

```java
package com.jdojo.intro;
import java.util.*;

public class Welcome {
    public static void main(String[] args) {
        System.out.println("Welcome to Java 17!");
    }
}
```

---

## 📂 Package Declarations

### 🔡 Syntax:

```java
package com.jdojo.intro;
```

### 📦 Naming Convention:

- Reverse domain naming: `com.jdojo.intro`
    
- All lowercase, case-sensitive
    

### 🗂️ Directory Mapping:

```
com.jdojo.intro → com/jdojo/intro/
```

> ⚠️ Must be the first non-comment, non-whitespace line

---

## 📥 Import Declarations

### 📌 Purpose:

Import allows using simple names for classes instead of full names.

### ✏️ Syntax:

```java
import java.util.List;   // Single type
import java.util.*;      // Wildcard (not recursive)
```

> 🚫 `import com.*.*;` is **not valid**

### ✅ Auto-import:

- `java.lang` package is automatically imported
    

### 🔎 Example without Import:

```java
java.util.ArrayList<String> list = new java.util.ArrayList<>();
```

---

## 🧱 Class Declaration & `main()` Method

### 🏗️ Basic Class Syntax:

```java
public class ClassName {
    // Fields, Constructors, Methods, etc.
}
```

### 🧠 `main()` Method:

```java
public static void main(String[] args) {
    System.out.println("Hello Java!");
}
```

> ✅ Entry point for the JVM

### 🔄 Breakdown:

- `public`: accessible from JVM
    
- `static`: can run without an object
    
- `void`: returns nothing
    
- `String[] args`: command-line input
    

---

## 🛠️ Compilation & Execution (With Modules)

### 🧾 Compile:

```bash
javac -d mod/jdojo.intro \
  src/jdojo.intro/module-info.java \
  src/jdojo.intro/com/jdojo/intro/Welcome.java
```

- `-d`: Output directory
    

### ▶️ Run:

```bash
java --module-path mod --module jdojo.intro/com.jdojo.intro.Welcome
```

**Expected Output:**

```
Welcome to Java 17!
```

---

## 📋 Summary Table

|Feature|Required?|Description|
|---|---|---|
|`package` declaration|✅ in modules|Specifies the package location|
|`import` statement|Optional|Imports specific classes or packages|
|Public class filename|✅|Must match the file name exactly|
|`main` method|✅|Entry point for standalone apps|
|`module-info.java`|✅ in modules|Declares module dependencies and exports|

---

## 🔗 Further Reading & Resources

- 📚 [Java SE Modules (Oracle)](https://docs.oracle.com/javase/9/docs/api/java/lang/module/ModuleDescriptor.html)
    
- 📖 [JDK 17 Java Language Specification](https://docs.oracle.com/javase/specs/jls/se17/html/index.html)
    
- 🛠️ [Java Modules by Example](https://openjdk.org/projects/jigsaw/quick-start)
    

---

## 💡 Real-World Use Cases

- Modularizing enterprise Java apps
    
- Structuring APIs in SDKs
    
- Large team development: encapsulation via modules
    
- Packaging JavaFX apps
    

---

## 🧪 Bonus Example: Multiple Classes

```java
package com.jdojo.intro;

public class MainApp {
    public static void main(String[] args) {
        Helper.greet("Yamina");
    }
}

class Helper {
    static void greet(String name) {
        System.out.println("Hi, " + name + "! Welcome to Java Modules!");
    }
}
```

**Expected Output:**

```
Hi, Yamina! Welcome to Java Modules!
```

---
