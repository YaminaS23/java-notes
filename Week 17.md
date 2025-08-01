
# Java Increment and Decrement Operators

---

## 📌 Overview

Java provides **increment (`++`)** and **decrement (`--`)** operators to increase or decrease a variable's value by 1. These are concise alternatives to writing expressions like `x = x + 1` or `x = x - 1`. These operators come in two flavors:

- **Pre-increment / Pre-decrement** (`++x`, `--x`)
    
- **Post-increment / Post-decrement** (`x++`, `x--`)
    

> ✅ These are available in **all versions of Java** — not deprecated or outdated!

---

## 🔄 Pre-Increment vs Post-Increment

|Operator|Form|Effect Timing|Description|
|---|---|---|---|
|Pre-increment|`++x`|Before expression used|Adds 1 to `x` then uses updated value|
|Post-increment|`x++`|After expression used|Uses original `x`, then adds 1|
|Pre-decrement|`--x`|Before expression used|Subtracts 1 from `x` then uses updated value|
|Post-decrement|`x--`|After expression used|Uses original `x`, then subtracts 1|

> 💡 Pre- and post- operators behave identically when used alone as statements.

---

## 🚀 Example 1: Pre-Increment

```java
public class AddMoreGumballs {
    public static void main(String[] args) {
        int gumballs = 27;

        ++gumballs;
        System.out.println(gumballs);       // Output 1
        System.out.println(++gumballs);     // Output 2
        System.out.println(gumballs);       // Output 3
    }
}
```

**Expected Output:**

```
28
29
29
```

> 📌 `++gumballs` increments before usage.

---

## 🧃 Example 2: Post-Increment

```java
public class AddEvenMoreGumballs {
    public static void main(String[] args) {
        int gumballs = 27;

        gumballs++;
        System.out.println(gumballs);       // Output 1
        System.out.println(gumballs++);     // Output 2
        System.out.println(gumballs);       // Output 3
    }
}
```

**Expected Output:**

```
28
28
29
```

> 📌 `gumballs++` uses the old value, then increments.

---

## 📌 Pre/Post Decrement Examples

```java
public class DecrementDemo {
    public static void main(String[] args) {
        int candies = 10;

        System.out.println(--candies);  // Pre-decrement → 9
        System.out.println(candies--);  // Post-decrement → prints 9, then decrements to 8
        System.out.println(candies);    // Prints 8
    }
}
```

### **Expected Output**

```
9
9
8
```

---

## 🧪 Code Exploration with Decrement Operators

```java
public class Main {
    public static void main(String[] args) {
        int i = 10;

        System.out.println(i++);  // prints 10, then i becomes 11
        System.out.println(--i);  // i becomes 10, prints 10
        --i;                      // i becomes 9
        i--;                      // i becomes 8
        System.out.println(i);    // prints 8
        System.out.println(++i);  // i becomes 9, prints 9
        System.out.println(i--);  // prints 9, then i becomes 8
        System.out.println(i);    // prints 8
        
        i++;                      // i becomes 9
        i = i++ + ++i;            // tricky part: evaluated left-to-right
        System.out.println(i);    // prints 21

        i = i++ + i++;            // 21 + 22 = 43, i becomes 23
        System.out.println(i);    // prints 43
    }
}
```

**Expected Output:**

```
10
10
8
9
9
8
20
41
```

---

## 🧪 Code Example: Stand-alone Increment / Decrement

```java
public class CounterExample {
    public static void main(String[] args) {
        int numberOfItems = 25;
        numberOfItems = numberOfItems + 1;  // traditional way
        numberOfItems++;                    // using post-increment

        int itemsOnStock = 157;
        itemsOnStock = itemsOnStock - 1;    // traditional way
        itemsOnStock--;                     // using post-decrement

        System.out.println("Items Found: " + numberOfItems);
        System.out.println("Items Left in Stock: " + itemsOnStock);
    }
}
```

**Expected Output:**

```
Items Found: 27
Items Left in Stock: 155
```

---

## 💬 Expressions vs Statements

### 👉 Expression

An **expression** returns a value.

```java
int x = i++;
```

Here, `i++` is an **expression** — `x` gets the old value of `i`.

### 👉 Statement

```java
i++;
```

This is a **statement** — tells the computer to increment `i`, no value used.

---

## 🎯 Advanced Use in Assignment Expressions

### 🔹 Example 1: Pre vs Post in Assignment

```java
int i = 137;
int j = 65;

// Pre-increment
i = ++j;  // j becomes 66, then assigned to i

// Post-increment
i = j++;  // i gets 65, then j becomes 66
```

> 🔎 **Key Takeaway:**
> 
> - `i = ++j;` → `j = j + 1; i = j;`
>     
> - `i = j++;` → `i = j; j = j + 1;`
>     

---

## 🧪 Code Example: In Expressions with Multiplication 1

```java
public class ExpressionTest {
    public static void main(String[] args) {
        int i;
        int j = 65;
        int k = 10;

        i = (++j) * k;  // j = 66, i = 660
        System.out.println("i = (++j) * k => i = " + i + ", j = " + j);

        j = 65;
        i = (j++) * k;  // i = 650, j = 66
        System.out.println("i = (j++) * k => i = " + i + ", j = " + j);
    }
}
```

**Expected Output:**

```
i = (++j) * k => i = 660, j = 66
i = (j++) * k => i = 650, j = 66
```

---

## 🧪 Code Example: In Expressions with Multiplication 2

```java
public class ExpressionDemo {
    public static void main(String[] args) {
        int i;
        int j = 65;
        int k = 10;

        i = (++j) * k; // j = 66, i = 660
        System.out.println("i = " + i + ", j = " + j);

        j = 65; // reset
        i = (j++) * k; // i = 650, j = 66
        System.out.println("i = " + i + ", j = " + j);

        j = 65; // reset
        i = (--j) * k; // j = 64, i = 640
        System.out.println("i = " + i + ", j = " + j);

        j = 65; // reset
        i = (j--) * k; // i = 650, j = 64
        System.out.println("i = " + i + ", j = " + j);
    }
}
```

**Expected Output:**

```
i = 660, j = 66
i = 650, j = 66
i = 640, j = 64
i = 650, j = 64
```

---

### 🔹 Example 2: In Expressions (Explained)

```java
int i = 137;
int j = 65;
int k = 10;

// Pre-increment
i = (++j) * k; // j becomes 66, then i = 66 * 10 = 660

// Post-increment
i = (j++) * k; // i = 65 * 10 = 650, then j becomes 66
```

**Expected Results:**

|Expression|Result|`j` after|
|---|---|---|
|`i = (++j) * k;`|660|66|
|`i = (j++) * k;`|650|66|

---

## ✅ Best Practices

> 💡 **Good Programming Practice 2.13:**  
> Use increment/decrement operators **only in stand-alone statements** for clarity and readability.

Avoid this:

```java
i = ++j * k;  // unclear side effects
```

Prefer this:

```java
++j;
i = j * k;
```

---

## 🧪 Code Example: Combined Demo (from textbook)

```java
public class IncDec {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        int c;
        int d;

        c = ++b;  // b becomes 3, c = 3
        d = a++;  // d = 1, then a becomes 2
        c++;      // c = 4

        System.out.println("a = " + a);
        System.out.println("b = " + b);
        System.out.println("c = " + c);
        System.out.println("d = " + d);
    }
}
```

**Expected Output:**

```
a = 2
b = 3
c = 4
d = 1
```

---

## 🧠 Real-World Use Cases

1. **Loops**
    

```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

2. **Tracking Counters**
    

```java
int numberOfItems = 0;
numberOfItems++;  // After finding an item
```

3. **Simulating Timestamps or Steps**
    

```java
int step = 1;
System.out.println("Step " + step++); // Step 1, Step 2...
```

---

## 📚 Further Reading

- [Java Language Specification - JLS §15.14](https://docs.oracle.com/javase/specs/jls/se21/html/jls-15.html#jls-15.14)
    
- [Oracle Java Tutorials - Expressions](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)
    
- [GeeksforGeeks - Increment/Decrement in Java](https://www.geeksforgeeks.org/increment-decrement-operators-in-java/)
    

---

## 🎉 Summary Cheatsheet

```text
// Pre-Increment
++x → Increments x, then returns new value

// Post-Increment
x++ → Returns x, then increments

// Pre-Decrement
--x → Decrements x, then returns new value

// Post-Decrement
x-- → Returns x, then decrements
```

> 🚨 Use `++` and `--` wisely to avoid logic bugs. Prefer standalone usage when possible.

---

💬 **Quick Quiz:**  
What’s the output of this code?

```java
int x = 5;
System.out.println(x++ + ++x);
```

🤔 Think you know? (Answer: `5 + 7 = 12`, because `x++` gives 5, then x becomes 6, and `++x` becomes 7)

---