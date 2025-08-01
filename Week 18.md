
# Java Assignment Operators & Compound Assignment

---

## 🧠 What are Assignment Operators?

Assignment operators in Java let you perform a mathematical operation **and** assign the result back to a variable — all in one go. Think of them as shortcuts for math with memory!

> 📌 **Example:** `x += 5` is equivalent to `x = x + 5`

---

## 🔥 Supported Assignment Operators in Java

|Compound Operator|Equivalent Expression|Operation|
|---|---|---|
|`+=`|`x = x + y`|Addition|
|`-=`|`x = x - y`|Subtraction|
|`*=`|`x = x * y`|Multiplication|
|`/=`|`x = x / y`|Division|
|`%=`|`x = x % y`|Modulus (Remainder)|

> ⚠️ You **can't** use multiple `++` or `--` like `x++++`. Java will throw: `Variable expected` or `unexpected type` error.

---

## 🧪 Basic Usage & Experiment

### 🔍 Example Code:

```java
public class Main {
    public static void main(String[] args) {
        int i = 10;
        i += 2;   // i = i + 2 -> 12
        i -= 5;   // i = i - 5 -> 7
        i *= 6;   // i = i * 6 -> 42

        System.out.println(i);          // 42
        System.out.println(i += 3);     // 45
        System.out.println(i /= 2);     // 22
    }
}
```

### ✅ **Expected Output:**

```
42
45
22
```

---

## 🔄 Real-World Example: Shopping Cart 💳

```java
public class ShoppingCart {
    public static void main(String[] args) {
        double amount = 5.95;
        double shippingAndHandling = 25.00;
        double discount = 0.15;          // 15%

        amount += shippingAndHandling;   // Add shipping
        amount -= discount * 2;          // Apply discount

        System.out.println("Total Amount: $" + amount);
    }
}
```

### ✅ **Expected Output:**

```
Total Amount: $30.65
```

> 💡 The discount was 0.30 (0.15 * 2). We subtracted that after adding shipping.


### ✅ Step 1: Add shipping to the total

```java
amount += shippingAndHandling;
```

> **🍯 What does it do?** `amount = amount + shippingAndHandling` => `amount = 5.95 + 25.00 = 30.95`

### ✅ Step 2: Apply the discount

```java
amount -= discount * 2;
```

> **🎉 What's that?** We're subtracting a total discount of `0.15 * 2 = 0.30` => `amount = 30.95 - 0.30 = 30.65`

---

## 🧙 Advanced Usage: `%=` Modulus Operator

Use `%=` to get and store **remainders** in a single step. Super handy in problems involving change-making, parity checks, or clocks.

### 💸 Example: Making Change

```java
public class MakeChange {
    public static void main(String[] args) {
        int amount = 287; // Rs.287
        int hundreds = amount / 100;
        amount %= 100;  // Remaining after removing Rs.100 notes

        int fifties = amount / 50;
        amount %= 50;

        int tens = amount / 10;
        amount %= 10;

        System.out.println("100s: " + hundreds);
        System.out.println("50s: " + fifties);
        System.out.println("10s: " + tens);
        System.out.println("Remaining coins: Rs." + amount);
    }
}
```

### ✅ **Expected Output:**

```
100s: 2
50s: 1
10s: 3
Remaining coins: Rs.7
```

> 🧠 `%=` makes the code cleaner and avoids repetitive writing of `x = x % y`.

---

## 📚 Good Programming Practice

✅ Use `+=` and `-=` when:

- You're **incrementing or decrementing** a variable
    
- You're combining strings
    

### 🧪 Example: String Concatenation

```java
public class Greeting {
    public static void main(String[] args) {
        String s1 = "Hello ";
        String s2 = "there";

        s1 += s2; // Same as s1 = s1 + s2

        System.out.println(s1);
    }
}
```

### ✅ **Expected Output:**

```
Hello there
```

> 🔤 String concatenation using `+=` is clean and readable.

---

## ⚠️ What NOT to Do

```java
int gumballs = 5;
gumballs++++; // ❌ Not allowed
```

**Error:**

```
error: unexpected type
required: variable
found: value
```

> 🚫 Java can't understand `++` chained on a non-variable. Use valid compound assignments only!

---

## 🧾 Java Statement Types

Java has **two main types of statements**:

### 1. **Declaration Statements**

- Declare variables or attributes.
    

```java
int x;
String name;
```

- `int x;` → Creates a variable named `x` of type integer.
    
- `String name;` → Creates a variable named `name` to store text.


### 2. **Executable Statements**

- Perform actions like assignments, outputs, method calls, etc.
    

```java
x = 5;
System.out.println("Hello!");
```

- `x = 5;` → Stores the value 5 in `x`.
    
- `System.out.println("Hello!");` → Prints "Hello!" to the console.

---

## 📘 Further Reading

- [Oracle Java SE Documentation - Operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)
    
- [GeeksForGeeks - Java Assignment Operators](https://www.geeksforgeeks.org/assignment-operators-in-java/)
    
- [Java Tutorials - W3Schools](https://www.w3schools.com/java/java_operators.asp)
    

---

## 🧠 Quick Recap Quiz! (No cheating 😎)

1. What does `x *= 3` do?
    
2. What will be the output?
    

```java
int x = 8;
x %= 3;
System.out.println(x);
```

3. Is `x++++` a valid Java statement?
    
4. What kind of operator is `+=`?
    
5. How would you concatenate two strings using a compound operator?
    

---

Want more code breakdowns, quizzes, or Java history throwbacks? Just ask! 😏
