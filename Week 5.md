
# Displaying Output & String Handling

---

## 📍 Introduction: Java Greetings Program

Displaying messages on the monitor is a fundamental Java operation. This week focuses on understanding `System.out.print` and `System.out.println`, escape sequences, string literals, and string concatenation.

---

## 🖥️ Screen Output

### 🧑‍💻 Basic Output with `System.out.println`

The most basic method to output text to the screen in Java is using:

```java
System.out.println("Your text here");
```

> 🔍 `**System**` is a standard Java class. 🔍 `**out**` is an object within the `System` class. 🔍 `**println**` is a method within the `out` object used to output text and then move to a new line.

### 📋 Syntax:

```java
System.out.println(Output_1 + Output_2 + ... + Output_Last);
```

---

## 🖥️ Hello World - Greeting Example

```java
/**
 A Greeting Program
*/
public class HiThere {
    public static void main(String[] args) {
        System.out.println("Hello! How are you?");
    }
}
```

**Expected Output:**

```
Hello! How are you?
```

> 🔍 Double quotes `" "` are used to define string literals in Java but are not printed in output.

---

## 💡 What is a String Literal?

A **String literal** in Java is any sequence of characters enclosed in **double quotes**. For example:

|String Literal|Description|
|---|---|
|`null`|Absence of a String object|
|`""`|Empty String (Length 0)|
|`" "`|String with a single space character|
|`"P"`|String of length 1|
|`"Peter"`|String of length 5|
|`"Peter, Paul and Mary"`|String of length 20|

> ❗ `null` ≠ `""`. `null` means _no object exists_, while `""` is just an empty but existing String.

---

## 📤 Multiple Print Statements

You can split a message across multiple `print` statements:

```java
System.out.print("Hello! ");
System.out.println("How are you?");
```

You can also do:

```java
System.out.print("Hello! ");
System.out.print("How ");
System.out.print("are");
System.out.print(" you?");
System.out.println(); // Moves cursor to next line
```

> ❗ **Syntax Error:** Omitting parentheses like `System.out.println;` will result in a compile-time error.

---

## ✨ Java Escape Sequences

Escape sequences help you print special characters and control formatting.

### 📌 Frequently Used Escape Sequences

|Escape Sequence|Purpose|
|---|---|
|`\r`|Carriage Return|
|`\n`|Newline|
|`\f`|Form Feed|
|`\t`|Horizontal Tab|
|`\b`|Backspace|
|`\\`|Backslash|
|`\'`|Single Quote|
|`\"`|Double Quote|

### 🔍 Escape Sequence Demonstration

```java
/**
 Demonstration of Escape Sequences
*/
public class EscapeSequence {
    public static void main(String[] args) {
        System.out.println("A return\r<- character");
        System.out.println("A newline\n<- character");
        System.out.println("A tab stop\t<- character");
        System.out.println("A backspace\b<- character");
        System.out.println("A backslash\\<- character");
        System.out.println("A single quotation\'<- character");
        System.out.println("A double quotation\"<- character");
    }
}
```

**Expected Output:**

```
<- character
A newline
<- character
A tab stop     <- character
A backspac<- character
A backslash\<- character
A single quotation'<- character
A double quotation"<- character
```

> 🔍 Use `\b` cautiously as it removes one character to the left.

---

## 🔄 Print vs Println

- `System.out.print()` **does not** move the cursor to the next line.
    
- `System.out.println()` **does** move the cursor to the next line.
    

> ✅ Good Practice: Use `println` when you want output in a new line.

---
## 🧾 Printing Blank Lines in Java

### 🟢 Syntax

```java
System.out.println();
```

### 💡 Description

- Calling `System.out.println()` with **no arguments** simply moves the cursor to the next line.
    
- This is **commonly used to add space** (i.e., a blank line) between lines of output.
    

### ✅ Example

```java
public class BlankLineExample {
    public static void main(String[] args) {
        System.out.println("Hello World!");
        System.out.println(); // Blank line
        System.out.println("This is after a blank line.");
    }
}
```

### 🔍 Expected Output:

```
Hello World!

This is after a blank line.
```

> ✅ **Use blank lines sparingly to make console output more readable!**

---

## 🔗 String Concatenation

### 📜 Theory

String concatenation means combining multiple strings into one string.

- Done using the **`+` operator**.
    
- Automatically handles different data types (Java converts them to strings).
    
- Java uses `+` to concatenate (combine) Strings.

### 🧠 Syntax

```java
String fullName = "Barry" + " " + "Burd";
```

> 🧃 Java will convert `int`, `double`, `boolean`, etc., to a string when used with `+` for concatenation.

---

### ✅ Example 1

```java
public class StringConcatExample {
    public static void main(String[] args) {
        int total = 237;
        System.out.println("From " + total + " cents you get");
    }
}
```

### 🔍 Expected Output:

```
From 237 cents you get
```

> ⚠️ Order of operations matters! Be careful when mixing numbers and strings.

### ❗ Unexpected Case

```java
System.out.println(1 + 2 + " cats");
```

**Output:** `3 cats`

```java
System.out.println("cats: " + 1 + 2);
```

**Output:** `cats: 12`

### 🔧 Fixing Concatenation Order

```java
System.out.println("cats: " + (1 + 2));
```

**Output:** `cats: 3`

> 📌 Parentheses help control evaluation order in concatenation!

---

### ✅ Example 2


```java
/**
 Demonstration of String concatenation
*/
public class ConcatOperator {
    public static void main(String[] args) {
        System.out.println("\n\n\tHello");
        System.out.println("This line concatenates" + " two Strings");
        System.out.println("This " + "line " + "concatenates" + " 4 Strings");
        System.out.println("\n\n\n\tBye Now");
    }
}
```

**Expected Output:**

```


    Hello
This line concatenates two Strings
This line concatenates 4 Strings



    Bye Now
```

> ✅ Good Practice: Leave space before and after `+` for better readability.

You can even concatenate Strings with numbers or characters:

```java
System.out.println("Age: " + 20);
System.out.println("Grade: " + 'A');
```

**Output:**

```
Age: 20
Grade: A
```

---

## 📚 Real-world Use Case

Consider a scenario of printing the result of arithmetic calculations clearly formatted for users:

```java
public class ArithmeticOutput {
    public static void main(String[] args) {
        double radius = 5.5;
        double area = Math.PI * radius * radius;
        System.out.println("Area of circle with radius " + radius + " is " + area);
    }
}
```

**Expected Output:**

```
Area of circle with radius 5.5 is 95.03317777109125
```

---

## 📦 Full Code Example: Output Formatting & Concatenation

```java
public class MoneyConverter {
    public static void main(String[] args) {
        int total = 237;
        int dollars = total / 100;
        int cents = total % 100;

        System.out.println("\n============================");
        System.out.println("From " + total + " cents you get:");
        System.out.println("Dollars: " + dollars);
        System.out.println("Cents: " + cents);
        System.out.println("============================\n");
    }
}
```

### 🔍 Expected Output:

```
============================
From 237 cents you get:
Dollars: 2
Cents: 37
============================
```

> 🧠 **Use formatting to guide the reader’s eye through structured output.**
---

## 🔢 String Indexing (Character Positioning)

Java indexes Strings starting from **0**.

```txt
"God bless America"
'G' at 0, 'o' at 1, 'd' at 2, ' ' at 3, 'b' at 4,
'l' at 5, 'e' at 6, 's' at 7, 's' at 8, ' ' at 9,
'A' at 10, 'm' at 11, 'e' at 12, 'r' at 13, 'i' at 14,
'c' at 15, 'a' at 16
```

> ✅ Spaces are counted as characters.

---

## ⚠️ Note: 'A' vs "A"

- `'A'` is a **character literal** (single char, stored as `char`).
    
- `"A"` is a **String literal** (a String of length 1).
    

---

## 🧠 Self-Check Challenges

1. **True or False:** A String in Java is enclosed within a pair of single quotes.  
    ➤ ❌ **False.** Characters use single quotes; Strings use **double quotes**.
    
2. **Print Statement:**
    
    ```java
    System.out.println("All is well in the eastern border!");
    ```
    
3. **Concatenation Challenges:**
    
    - "North" + "America" → **NorthAmerica**
        
    - " South" + "Africa" → **SouthAfrica**
        

---

## 📚 Further Reading & Docs

- [Java String (Official Java Docs)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html)
    
- [Escape Sequences in Java](https://www.geeksforgeeks.org/escape-sequences-java/)
    
- [System.out.print vs println](https://www.baeldung.com/java-system-out-println-vs-print)
    

---
