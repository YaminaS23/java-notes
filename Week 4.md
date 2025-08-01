
# Java Application Programs & Language Elements

---

## 🧠 Overview

This week focuses on the **structure of Java application programs**, the difference between **keywords vs identifiers**, and how Java syntax mimics natural language to make programming intuitive.

---

## 💡 Java Application Program

### 🧱 Traditional vs Java-style Programming

- Before Java, all languages created **stand-alone applications**.
    
- Java introduced:
    
    - **Application Programs**
        
    - **Applets** (small programs that run inside browsers)


> ✅ For this course, we focus on **Application Programs** first.

### 🧬 Java Program = Collection of Classes

- Every Java app has **at least one class**.
    
- **Basic Syntax Template:**
    

```java
[accessModifiers] class className [classModifiers] {
    [members]
}
```

### 📌 Important Notes

- Items in square brackets (`[]`) are **optional**.
    
- `className`: Name of the class (e.g., `HelloWorld`)
    
- `accessModifiers`: e.g., `public`, `private`
    
- `classModifiers`: e.g., `abstract`, `final` 
    
- `members`: Fields and methods
    

> 🔐 `public` makes the class accessible to the **Java Virtual Machine (JVM)**. You must have **at least one public class**.

### 🏷️ Keywords vs Identifiers

- **Keywords**: Reserved words like `public`, `class`, `static`, etc.
    
- **Identifiers**: Names you create — e.g., `ThingsILike`, `args`
    

---

## 🧩 Elements of a Java Program

### 🗣️ Language Comparison: Java vs English

|English|Java|
|---|---|
|Words|Keywords|
|Names|Identifiers|
|Sentence structure|Code syntax|

> 🧠 Tip: Java is more consistent and easier than English. It's case-sensitive and has strict rules.

---

## 🔑 Java Keywords

Java has **50+ reserved keywords**.

### 🗂️ Full Table of Java Keywords

| Keyword    | Keyword    | Keyword      | Keyword     | Keyword        |
| ---------- | ---------- | ------------ | ----------- | -------------- |
| `abstract` | `continue` | `for`        | `new`       | `switch`       |
| `assert`   | `default`  | `goto`❌      | `package`   | `synchronized` |
| `boolean`  | `do`       | `if`         | `private`   | `this`         |
| `break`    | `double`   | `implements` | `protected` | `throw`        |
| `byte`     | `else`     | `import`     | `public`    | `throws`       |
| `case`     | `enum`     | `instanceof` | `return`    | `transient`    |
| `catch`    | `extends`  | `int`        | `short`     | `try`          |
| `char`     | `final`    | `interface`  | `static`    | `void`         |
| `class`    | `finally`  | `long`       | `strictfp`  | `volatile`     |
| `const`❌   | `float`    | `native`     | `super`     | `while`        |

> 🚫 You **cannot redefine** a keyword (e.g., `public = 6;` is invalid).

### ❗ Reserved but Not Used in Java:

- `const`
    
- `goto`
    

> `const` and `goto` are **reserved but never used**. Basically there to troll C++ users 😅
---

## 🚫 "Restricted" or Special Identifiers

These aren’t technically keywords but are still **off-limits** or need caution:

### ⚠️ Table: Words to Avoid

|Restricted Identifiers|
|---|
|`exports`, `null`, `provides`, `transitive`, `var`|
|`false`, `open`, `requires`, `true`, `with`|
|`module`, `opens`, `to`, `uses`, `yield`|

> 👾 Treat these as **read-only words** — don’t mess with them.

---

## 🆔 Identifiers You Define

### 📛 Naming Conventions

- You can name your classes and variables anything **not a keyword**
    
    - Examples: `GooseGrease`, `Enzyme`, `ThingsILike`, `args`
        

### ✅ Good Practice:

Use meaningful names:

```java
String[] commandLineArguments; // Better than cheese or args
```

---

## 🧠 Identifiers with Standard Meaning (from Java API)

### 🤝 Predefined Identifiers:

|Identifier|Meaning|
|---|---|
|`main`|Program’s entry point|
|`String`|A sequence of characters/text|
|`System`|A utility class with useful features|
|`out`|Output stream object|
|`println`|Method to print text to screen and add newline|

### 📄 Example:

```java
public class ThingsILike {
    public static void main(String[] args) {
        System.out.println("Chocolate, royalties, sleep");
    }
}
```

**Expected Output:**

```
Chocolate, royalties, sleep
```

> 🔁 These identifiers can technically be redefined but **you shouldn’t** — it breaks conventions and confuses others.

---

## 💥 Case Sensitivity in Java

- Java is **case-sensitive**.
    
- `Public`, `PUBLIC`, and `public` are not the same.
    

### 🚫 Example of Breaking Case Sensitivity

```java
Public class Hello { // ❌ Wrong: 'Public' should be 'public'
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

> 💣 This won’t compile — JVM won’t recognize it as a valid public class.

---

## 📚 Further Reading

- [Oracle Java Language Specification](https://docs.oracle.com/javase/specs/)
    
- [Java Keywords (GeeksforGeeks)](https://www.geeksforgeeks.org/java-reserved-keywords/)
    
- [Java Identifiers Naming Rules](https://www.baeldung.com/java-variable-naming-conventions)
    
- [Java API Documentation](https://docs.oracle.com/javase/8/docs/api/)
    

---

## 🔤 Literals in Java

> A **literal** is a value directly written in code, exactly representing what it is.

### 📌 String Literal Example:

```java
System.out.println("Chocolate, royalties, sleep");
```

**Expected Output:**

```
Chocolate, royalties, sleep
```

- The text within quotes is called a **string literal**.
    
- It directly represents the characters to be displayed/output.
    
- In Java, all **string literals** are represented using the `String` class.
    

---

## 💯 Numeric Literals

### Example:

```java
mySalary = 1000000.00;
```

- `1000000.00` is a **numeric literal**.
    
- It directly represents a floating-point number.
    

### 🔢 Underscore in Literals (Since Java 7)

```java
mySalary = 1_000_000.00;
```

✅ Legal and improves readability.

### 💡 Regional Formatting Trivia

|Region|Formatting Example|Java Allows?|
|---|---|---|
|US|1,234,567.89|❌ No commas|
|France|1234567,89|❌ No commas|
|India|1_23_45_67_890.55|✅ with `_`|
|Switzerland|1’234’567.89 or 1 234 567.89|❌ Not valid|

> 📌 Java _only_ accepts underscores `_` in numeric literals, **not** commas, quotes, or spaces.

> 🧭 For displaying local formats, use `Locale` and `NumberFormat` classes. 

---

## 🔣 Punctuation & Indentation in Java

```java
public class ThingsILike {
    public static void main(String[] args) {
        System.out.println("Chocolate, royalties, sleep");
    }
}
```

### Key Punctuation:

- `{}` → curly braces define blocks.
    
- `()` → parentheses are for method calls.
    
- `;` → semicolon ends a statement.
    
-  `[]` → Square brackets (arrays)
    
- Proper **indentation** is crucial for code readability.
    
- IntelliJ IDEA can **auto-indent**: `Code ➜ Reformat Code`
    

> ✨ Well-indented code saves your future self from suffering!

---

## 🗨️ Java Comments

> Comments help programmers (including future you 👀) understand the code. The compiler ignores them.

### 📝 1. Traditional Comment

```java
/*
 * This is a traditional comment
 * spanning multiple lines.
 */
```

### 🧾 2. End-of-Line Comment

```java
System.out.println("Sleep"); // This prints sleep
```

### 🚫 Commenting Out Code

```java
// System.out.println("Sleep");
```

Temporarily disables code without deleting it.

### 📄 3. Javadoc Comment

```java
/**
 * Print a string followed by a newline.
 */
```

Use `javadoc` tool to auto-generate documentation web pages!

> 🔗 [Learn More: Java Javadoc Tool](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html)

---

## 🏛️ Java Class Structure

Java is based on **Object-Oriented Programming (OOP)**.

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of **objects**, which can contain **data** (fields or attributes) and **code** (methods or operations).

### 🔐 Encapsulation

- Bundling of data (attributes) and methods that operate on the data into a single unit (**class**).
    
- Prevents direct access to internal data; promotes data security and integrity.
    

### 🔒 Information Hiding

- The user doesn’t need to know how the internals work—just how to use the public interface (methods).
    
- Example: You can operate a TV without understanding its circuitry.
    

> **💡 Example:** You don't know how your microwave works internally, but you do know how to press the "Start" button. That’s encapsulation and information hiding in action!

### OOP Timeline:

- **1960s**: Simula
    
- **1970s**: Smalltalk
    
- **1980s**: C++
    
- **1990s-Present**: Java, Python, etc.
    


## 📒 Java Class Template

```java
public class ClassName {
    // attributes (variables)
    // operations (methods)
}
```

### 🗃️ Example: Stock Class

```java
public class Stock {
    private int numberOfShares;
    private String tickerSymbol;
    private double dividend;
}
```

> This class has three instance variables: shares owned, ticker symbol, and yearly dividend.

---

### 📦 Java Class Example:

```java
public class ThingsILike {
    public static void main(String[] args) {
        System.out.println("Chocolate, royalties, sleep");
    }
}
```

- Class = `ThingsILike`
    
- Method = `main(String[] args)`
    
- Statement = `System.out.println(...)`
    

> 📌 **Every Java program must start from a class.** You can’t run code outside a class!

### 🔄 Refactor Class Name in IntelliJ

- Right-click `ThingsILike` ➜ Refactor ➜ Rename ➜ `MyFavorites`
    

### 🔍 Word Play & Java Errors

### Try Changing Keywords:

- `class` → `bologna` ➡️ ❌ **Error** (keyword violation)
    
- `args` → `malarkey` ➡️ ✅ Still works
    
- `ThingsILike` → `MyFavorites` ➡️ ❌ unless you rename the file & class together
    

📢 IntelliJ Fix: Right-click class → `Refactor > Rename`

### Identifier Swaps:

- `println` → `display` ➡️ ❌ **Error** (undefined method)
    

### Change Punctuation:

- Remove `{}` ➡️ ❌ Error!
    

### Commenting Out Code:

- End-of-line style: `// System.out.println(...);` → Program runs but prints nothing ✅
    
- Traditional style:

```
/*
System.out.println("...");
*/
```

> Same behavior ✅

---

## 🆔 Identifiers in Java

Identifiers are **names** for variables, methods, classes, etc.

### ✅ Rules:

1. Must consist of letters (A-Z, a-z), digits (0–9), underscore `_`, or dollar sign `$`.
    
2. First character **cannot** be a digit.
    
3. Must **not** be a reserved keyword.
    

### ❌ Common Errors:

- Spaces in identifiers → `hello there` ❌
    
- Hyphens in identifiers → `hello-there` ❌
    
- Starting with digits → `75` or `7args` ❌
    

### 🟢 Valid Examples:

- `Carrot`
    
- `Tiger`
    
- `bonusSalary`
    
- `number_of_lines_per_page`
    
- `_0`, `$1` (legal but bad naming practice)
    

### ❌ Illegal Identifiers:

|Identifier|Error|
|---|---|
|`7args`|Starts with a digit|
|`hello there`|Contains a space|
|`hello-there`|Contains a hyphen|
|`public`|Reserved keyword|
|`@args`|Contains illegal character `@`|

> 🧠 Java is **case-sensitive**. `HiThere` ≠ `hithere`

### ✅ Naming Conventions:

- Class names: `PascalCase` ➜ `MyFirstClass`
    
- Variables/methods: `camelCase` ➜ `totalAmount`
    

### 🧪 Try changing `args` in IntelliJ to:

|Identifier|Valid?|
|---|---|
|`helloThere`|✅ Yes|
|`hello_there`|✅ Yes|
|`args7`|✅ Yes|
|`ar7gs`|✅ Yes|
|`75`|❌ No|
|`7args`|❌ No|
|`hello there`|❌ No|
|`hello-there`|❌ No|
|`public`|❌ No|
|`royalties`|✅ Yes|
|`@args`|❌ No|
|`#args`|❌ No|
|`/arg`|❌ No|

---

## 🔗 Further Reading

- 📖 [Oracle’s Official Java Docs](https://docs.oracle.com/javase/tutorial/)
    
- 📘 [Effective Java by Joshua Bloch](https://amzn.to/3KS8dM4)
    
- 💡 [JetBrains IntelliJ IDEA Docs](https://www.jetbrains.com/idea/documentation/)
    

---
