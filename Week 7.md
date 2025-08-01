
# Java Data Types : Part 1

---

## ✅ Boolean Data Type (`boolean`)

The `boolean` data type represents **logical values** — either `true` or `false`. It's used for conditions, decision-making, and controlling program flow.

### 🔍 Key Characteristics:

- Takes only **two values**: `true` or `false`
    
- Size: **1 bit** (though JVM typically uses 1 byte)
    
- **Reserved words**: `boolean`, `true`, `false`
    
- Cannot be involved in arithmetic operations (i.e., `true ≠ 1`, `false ≠ 0`)
    

### 🔑 Real-World Use:

- **If/else control structures**
    
- **Loops** (`while`, `for`, `do-while`)
    
- **Relational operations**
    

### 🧪 Code Example:

```java
// Demonstrate boolean values.
public class BoolTest {
    public static void main(String[] args) {
        boolean b;
        b = false;
        System.out.println("b is " + b);

        b = true;
        System.out.println("b is " + b);

        // A boolean can control an if-statement
        if (b) System.out.println("This is executed.");

        b = false;
        if (b) System.out.println("This is not executed.");

        // Boolean result from relational operator
        System.out.println("10 > 9 is " + (10 > 9));
    }
}
```

### 🧾 Expected Output:

```
b is false
b is true
This is executed.
10 > 9 is true
```

### 💡 Observations:

> ✅ You don’t need to use `if(b == true)`. Just use `if(b)`  
> ✅ Relational operators like `<`, `>`, $==$ return boolean values  
> ✅ Parentheses around `(10 > 9)` are necessary due to `+` operator precedence

---

## 🔤 Char Data Type (`char`)

The `char` data type stores a **single character** and uses **Unicode** internally, allowing representation of **international characters**.

### 📌 Characteristics:

- Size: **2 bytes** (16 bits)
    
- Range: **0 to 65535** (unsigned)
    
- Literal format: enclosed in single quotes, e.g., `'A'`, `'7'`, `'%'`
    
- `' '` (space) is a valid `char`
    
- `char` values map to **Unicode integers**
    

### 🧪 Valid Char Literals:

```java
char ch1 = 'J';
char ch2 = '@';
char space = ' ';
```

### 🗃️ Special Symbols Table:

| Symbol | Meaning               |
| ------ | --------------------- |
| `<=`   | Less than or equal    |
| `>=`   | Greater than or equal |
| $==$   | Equal to              |
| `!=`   | Not equal to          |

> ⚠️ Note: Symbols like `<=` or $==$ are **tokens**, not `char` literals!

---

## 🔠 Unicode & Collating Sequence

Java uses **Unicode** (65536 characters) to support global characters.

- First 128 characters = ASCII
    
- Characters are **ordered** by integer values (collating sequence).
    - `'A'` = 65, `'a'` = 97 → `'A' < 'a'`
    
- Extended Latin: 0 to 255
    
- Characters have implicit **numeric values** (called **collating sequence**)
    

### 🔍 Collating Sequence Example:

```java
public class CollatingSequence {
    public static void main(String[] args) {
        System.out.println('a' - 'A');
        System.out.println('A' - 'a');
        System.out.println('q' - 'Q');
        System.out.println('Q' - 'q');
    }
}
```

### 🧾 Expected Output:

```
32
-32
32
-32
```

> ✅ Difference between lowercase & uppercase letters = 32

### 💡 Pro Tip:

Escape sequences like `\n`, `\t`, `\b` are all considered **single `char` values**

---

## 🔣 Unicode Specification (`\uXXXX`)

Java lets you specify characters using Unicode escapes:

```java
char symbol = '\u0046'; // 'F'
```

### ✅ Example:

```java
// Unicode example
public class UnicodeChar {
    public static void main(String[] args) {
        char unicodeChar = '\u0046';
        System.out.println("Unicode char: " + unicodeChar);
    }
}
```

**Output:**

```
Unicode char: F
```

> Use `\u` followed by 4 hexadecimal digits (case-insensitive)

### 📘 Unicode Format:

Use format `\uXXXX` where `X` is a hexadecimal digit (0-9, A-F).

- Null character: `\0` or `\u0000`
    
- Unicode supports **global characters** (e.g. `\u3042` = あ in Japanese)
    

---

## 🎯 char Arithmetic

Even though `char` stores characters, it acts like an `int`!

### Example: char as Integer

```java
public class CharDemo {
    public static void main(String[] args) {
        char ch1, ch2;
        ch1 = 88; // ASCII code for X
        ch2 = 'Y';

        System.out.print("ch1 and ch2: ");
        System.out.println(ch1 + " " + ch2);
    }
}
```

**Output:**

```
ch1 and ch2: X Y
```

### Example: char Increment

```java
public class CharDemo2 {
    public static void main(String[] args) {
        char ch1 = 'X';
        System.out.println("ch1 contains " + ch1);

        ch1++; // move to next char
        System.out.println("ch1 is now " + ch1);
    }
}
```

**Output:**

```
ch1 contains X
ch1 is now Y
```

> `char` is formally an **integral type**, like `int` or `byte`.

---

## 📚 Further Reading

- [Java Primitive Data Types (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [Unicode Standard](https://www.unicode.org/standard/standard.html)
    
- [Escape Sequences in Java](https://www.geeksforgeeks.org/escape-sequences-in-java/)
    

---

### 🧠 Review Time!

**Q:** What will this print?

```java
System.out.println('B' + 1);
```

**A:** `67` — because `'B'` = 66, and adding 1 gives 67

---

### 🔚 Summary:

- `boolean` is vital for **logic & control structures**
    
- `char` supports **global characters** via Unicode
    
- You can do math on `char` since it maps to integers
    
- Use escape sequences (`\n`, `\t`) to control formatting
    
- Unicode literals (`\uXXXX`) let you access any character by code
    

🚀 Now you're ready to wield booleans and characters like a code-wizard! 🧙‍♂️