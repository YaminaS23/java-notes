
# Java Variables

---

## 📘 Overview

Variables are the **basic unit of storage** in Java. They hold data that your program can use and manipulate. Every variable in Java has:

> 🔹 A **Type** (like `int`, `double`, `char`)  
> 🔹 An **Identifier** (the variable name)  
> 🔹 An optional **Initializer** (a starting value)  
> 🔹 A **Scope** (where it's accessible)  
> 🔹 A **Lifetime** (how long it lives in memory)

This guide is based on standard Java (Java 8 to Java 21) and reflects both older and newer styles, including info on `var`.

---

## 🛠️ Declaring Variables

```java
// Syntax
Type identifier = value;
```

### ✅ Examples

```java
int a, b, c;               // declares 3 int variables
int d = 3, e, f = 5;       // initializes d and f
byte z = 22;               // z is 22
char x = 'x';              // x is a character
```

> 📌 The identifier name does not reveal the variable's type.

---

## ⚡ Dynamic Initialization

Java allows dynamic initialization using expressions, method calls, and literals.

### 📐 Hypotenuse Example

```java
public class DynInit {
    public static void main(String[] args) {
        double a = 3.0, b = 4.0;
        double c = Math.sqrt(a * a + b * b); // Dynamic
        System.out.println("Hypotenuse is " + c);
    }
}
```

**Expected Output:**

```
Hypotenuse is 5.0
```

> 🧠 `Math.sqrt()` is a built-in method from Java's `Math` class.

---

## 🔒 Scope and Lifetime of Variables

### 🧱 What is Scope?

A **scope** is a block of code where a variable is visible. Blocks are defined by `{}`.

- Variables declared inside a block are **local**.
    
- Variables declared outside are accessible to nested scopes but not vice versa.
    

### 🔄 Lifetime

- A variable exists **only while** the block it's in is executing.
    
- After leaving the block, the variable is destroyed.
    

### 🧪 Scope Example

```java
public class Scope {
    public static void main(String[] args) {
        int x = 10; // visible everywhere in main
        if (x == 10) {
            int y = 20; // only visible in this block
            System.out.println("x and y: " + x + " " + y);
            x = y * 2;
        }
        // System.out.println(y); // ❌ Error: y not visible here
        System.out.println("x is " + x);
    }
}
```

**Expected Output:**

```
x and y: 10 20
x is 40
```

> ⚠️ Java does NOT allow variables of the same name in nested scopes.

---

## ⏳ Variable Lifetime in Loops

```java
public class LifeTime {
    public static void main(String[] args) {
        for (int x = 0; x < 3; x++) {
            int y = -1; // initialized every loop
            System.out.println("y is: " + y);
            y = 100;
            System.out.println("y is now: " + y);
        }
    }
}
```

**Expected Output:**

```
y is: -1
y is now: 100
y is: -1
y is now: 100
y is: -1
y is now: 100
```

---

## ⚠️ Illegal Variable Shadowing

```java
public class ScopeErr {
    public static void main(String[] args) {
        int bar = 1;
        {
            // int bar = 2; // ❌ Error: Duplicate variable name
        }
    }
}
```

> ❗ Java doesn't allow re-declaring variables in an inner scope.

---

## 🔁 Moving Variable Declarations

### ✅ Correct Way: Declaration + Initialization Outside Method

```java
public class SnitSoft {
    static double amount = 5.95; // must be static

    public static void main(String[] args) {
        amount = amount + 25.00;
        System.out.print("We will bill $");
        System.out.print(amount);
        System.out.println(" to your credit card.");
    }
}
```

**Output:**

```
We will bill $30.95 to your credit card.
```

### ❌ Incorrect Way: Assignment outside method

```java
public class BadSnitSoftCode {
    static double amount;

    // ❌ Invalid: assignment cannot be outside method or initializer
    amount = 5.95;

    public static void main(String[] args) {
        amount = amount + 25.00;
    }
}
```

> ❌ Variables can't be _assigned_ outside a method. Only declared & initialized.

---

## ⚙️ `var` Keyword (Modern Java Feature - Java 10+)

`var` lets Java **infer** the variable type.

```java
var count = 5; // count is inferred as int
```

> ⚠️ Cannot use `var` for class-level/static variables.

```java
// ❌ Not allowed
static var amount = 5.95;
```

---

## 🧮 Combining Variable Declarations

```java
double flashDrivePrice = 5.95, shippingAndHandling = 25.00, total;
total = flashDrivePrice + shippingAndHandling;
```

You can also split them:

```java
double flashDrivePrice;
double shippingAndHandling;
double total;
```

Both are valid. Choose based on readability.

---

## 💡 Real-World Use Case: Parking Tip Calculator

```java
import java.util.Scanner;

public class TipCalculator {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter the garage price: $");
        double price = input.nextDouble();
        double total = price + 2.00; // $2 tip
        System.out.println("Total with tip: $" + total);
    }
}
```

**Expected Output:** (for input `8.00`)

```
Enter the garage price: $8.00
Total with tip: $10.0
```

---

## 🧮 DOUBLE PRICE (Challenge)

```java
import java.util.Scanner;

public class DoublePrice {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter flash drive price: $");
        double price = input.nextDouble();
        double total = price * 2; // doubled price
        System.out.println("Charged amount: $" + total);
    }
}
```

### ✅ Output:

```
Enter flash drive price: $ 5
Total (double price): $10.0
```

---

## 📊 Summary Table

|Concept|Description|
|---|---|
|Declaration|Type + Identifier (optionally = value)|
|Scope|Where the variable is visible|
|Lifetime|When the variable is created/destroyed|
|Dynamic Init|Using expressions/methods to initialize|
|`var` (Java 10+)|Type inference (not for class-level vars)|
|Static Variables|Declared outside methods with `static`|

---

## 🔗 Further Reading

- [Oracle Java Documentation](https://docs.oracle.com/en/java/)
    
- [Java SE Language Specification](https://docs.oracle.com/javase/specs/)
    
- [W3Schools Java Variables](https://www.w3schools.com/java/java_variables.asp)
    
- [GeeksForGeeks Java Variables](https://www.geeksforgeeks.org/variables-in-java/)
    
- [Baeldung on var](https://www.baeldung.com/java-var-type)
    

---

## 🧠 Bonus Challenge for You!

> Write a program that reads the radius of a circle from the user and prints both the **area** and **circumference**. Use `Math.PI` and `Math.pow()`.

---

Want a quiz on variables, scope, and lifetime next? Or maybe a battle between `static` and `instance`? 😏