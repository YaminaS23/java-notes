
# Whole Numbers & Operators

---

### Notable Features Used:

|Feature|Version|Notes|
|---|---|---|
|`Scanner` class|Java 5+|Still standard and used widely|
|`var` keyword|Java 10+|Local variable type inference|

> ⚠️ If you're using **Java 8 or older**, you'll need to **replace `var` with explicit types** like `Scanner keyboard = new Scanner(System.in);`

---

# 📗 Whole Numbers in Java

## 🎯 What are Whole Numbers?

Whole numbers in Java are represented using the `int` type — numbers without a decimal point.

- Example: `int x = 10; // ✅`
    
- But: `int y = 10.5; // ❌ ERROR`
    

---

## 🧪 Real-World Scenario: The Gumball Problem

### Code Example: Divide Gumballs Among Kids

```java
public class KeepingKidsQuiet {
    public static void main(String[] args) {
        int gumballs;
        int kids;
        int gumballsPerKid;

        gumballs = 30;
        kids = 4;
        gumballsPerKid = gumballs / kids;

        System.out.print("Each kid gets ");
        System.out.print(gumballsPerKid);
        System.out.println(" gumballs.");
    }
}
```

### ✅ Expected Output:

```
Each kid gets 7 gumballs.
```

> ⚠️ Reminder: `30 / 4 = 7` in Java because it's **integer division** (no rounding).

---

## 🧑‍💻 Dynamic Input with Scanner

### Code Example: Take Input from User

```java
import java.util.Scanner;

public class KeepingMoreKidsQuiet {
    public static void main(String[] args) {
        var keyboard = new Scanner(System.in);

        int gumballs;
        int kids;
        int gumballsPerKid;

        System.out.print("How many gumballs? How many kids? ");
        gumballs = keyboard.nextInt();
        kids = keyboard.nextInt();

        gumballsPerKid = gumballs / kids;

        System.out.print("Each kid gets ");
        System.out.print(gumballsPerKid);
        System.out.println(" gumballs.");

        keyboard.close();
    }
}
```

### ✅ Expected Output:

```
How many gumballs? How many kids? 80 6
Each kid gets 13 gumballs.
```

> 💡 **Important**: Input order must match variable assignment!

---

## 🔥 Make It & Break It Tests

### ❌ Case 1: Using Decimal Input (e.g. 80.5)

```text
How many gumballs? How many kids? 80.5 6
Exception in thread "main" java.util.InputMismatchException: For input string: "80.5"
```

👉 `nextInt()` expects whole numbers. Decimals cause a crash.

### ❌ Case 2: Quoted Input (e.g. "80" "6")

```text
How many gumballs? How many kids? "80" "6"
Exception in thread "main" java.util.InputMismatchException: For input string: ""80""
```

👉 Quotation marks are not valid for numeric input.

---

## 🧮 Simple Java Calculator

### Code Example: Add Two Whole Numbers

```java
import java.util.Scanner;

public class AddNumbers {
    public static void main(String[] args) {
        var keyboard = new Scanner(System.in);

        int num1, num2, sum;
        System.out.print("Enter two numbers: ");
        num1 = keyboard.nextInt();
        num2 = keyboard.nextInt();

        sum = num1 + num2;
        System.out.println("The sum is: " + sum);

        keyboard.close();
    }
}
```

### ✅ Expected Output:

```
Enter two numbers: 12 8
The sum is: 20
```

### 🔍 Step-by-Step Breakdown:
| Line | Explanation |
|------|-------------|
| `import java.util.Scanner;` | Allows user input from keyboard |
| `Scanner keyboard = new Scanner(System.in);` | Creates input reader |
| `num1 = keyboard.nextInt();` | Reads the first number |
| `num2 = keyboard.nextInt();` | Reads the second number |
| `sum = num1 + num2;` | Adds both numbers |
| `System.out.println("The sum is: " + sum);` | Displays result |

---

# ➕ Arithmetic Operators in Java

|Operator|Description|Example|Result|
|---|---|---|---|
|`+`|Addition|`4 + 5`|`9`|
|`-`|Subtraction|`9 - 3`|`6`|
|`*`|Multiplication|`2 * 3`|`6`|
|`/`|Division (int)|`11 / 4`|`2`|
|`/`|Division (double)|`11.0 / 4`|`2.75`|
|`%`|Modulus (remainder)|`11 % 4`|`3`|

> 🧠 Java uses **truncating division** for `int` types: remainder is discarded.

---

## 🔹 Role of Parentheses

Parentheses help group operations in a specific order, just like in algebra.

### Example 1: Different Results Based on Parentheses

```java
// Expression 1:
total = (cost + tax) * discount;
// Expression 2:
total = cost + (tax * discount);
```

**Explanation**:

- Expression 1 adds `cost` and `tax`, then multiplies by `discount`.
    
- Expression 2 multiplies `tax` and `discount`, then adds to `cost`.
    

---

## 🔹 Without Parentheses: Relying on Precedence

Java still evaluates expressions without parentheses by applying precedence rules.

### Example

```java
total = cost + tax * discount;
```

This is interpreted as:

```java
total = cost + (tax * discount);
```

Because:

- `*` (multiplication) has higher precedence than `+` (addition).

---

## 🔹 Coding Style Tips

✅ **Use Parentheses For Clarity**:

```java
balance = balance + (interestRate * balance); // clear but verbose
```

✅ **Omit When Standard**:

```java
balance = balance + interestRate * balance; // same meaning, less clutter
```

> 🎯 Keep your code readable! Parentheses make complex logic easier to understand — but avoid over-parenthesizing.

---

## 🔹 Real‑World Examples with Code

| Ordinary Math Expression | Java (Preferred Form)   | Java (Parenthesized Form) |
| ------------------------ | ----------------------- | ------------------------- |
| $rate^2+ delta$          | `rate * rate + delta`   | `(rate * rate) + delta`   |
| $2(salary + bonus)$      | `2 * (salary + bonus)`  | `2 * (salary + bonus)`    |
| $\frac{1}{time + 3mass}$ | `1 / (time + 3 * mass)` | `1 / (time + (3 * mass))` |
| $\frac{a - 7}{t + 9v}$   | `(a - 7) / (t + 9 * v)` | `(a - 7) / (t + (9 * v))` |

**Observations:**
1. **Exponentiation** → Java requires manual expansion (`rate²` becomes `rate * rate`)
2. **Fraction Bars** → Convert to division with explicit numerator/denominator parentheses
3. **Implied Multiplication** (e.g., `3mass`) → Must write as `3 * mass`
4. **Parenthesized Form** shows absolute precedence clarity (useful for complex expressions)

> 💡 **Java Operator Precedence Tip**: When in doubt, use parentheses – they make code both safer and more readable!

---

# 💰 Making Change Using Modulus Operator

### Code Example: Change Breakdown for US Coins

```java
import java.util.Scanner;

public class MakeChange {
    public static void main(String[] args) {
        var keyboard = new Scanner(System.in);

        int quarters, dimes, nickels, cents;
        int whatsLeft, total;

        System.out.print("How many cents do you have? ");
        total = keyboard.nextInt();

        quarters = total / 25;       // 1 quarter = 25 cents
        whatsLeft = total % 25;      // Remaining cents after quarters

        dimes = whatsLeft / 10;      // 1 dime = 10 cents
        whatsLeft = whatsLeft % 10;  // Remaining cents after dimes

        nickels = whatsLeft / 5;     // 1 nickel = 5 cents
        whatsLeft = whatsLeft % 5;   // Remaining cents after nickels

        cents = whatsLeft;           // Remaining 1-4 cents

        System.out.println();
        System.out.println("From " + total + " cents you get");
        System.out.println(quarters + " quarters");
        System.out.println(dimes + " dimes");
        System.out.println(nickels + " nickels");
        System.out.println(cents + " cents");

        keyboard.close();
    }
}
```

### ✅ Expected Output:

```
How many cents do you have? 138
From 138 cents you get
5 quarters
1 dimes
0 nickels
3 cents
```

---

# 🧠 Extra Tips

## 🏷️ Combined Declarations

Instead of writing:

```java
int quarters;
int dimes;
int nickels;
int cents;
```

You can combine:

```java
int quarters, dimes, nickels, cents;
```

## 🧪 When You Want Decimal Outputs

Use `double`:

```java
System.out.println(11 / 4);     // Output: 2
System.out.println(11.0 / 4);   // Output: 2.75
```

> 💡 Use typecasting to ensure correct data types: `((double)11)/4` gives `2.75`

---

# 📚 Further Reading

- [Java Primitive Data Types (Oracle)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [Scanner Class in Java (W3Schools)](https://www.w3schools.com/java/java_user_input.asp)
    
- [Java Operators (GeeksforGeeks)](https://www.geeksforgeeks.org/operators-in-java/)
    
- [Integer Division in Java (Baeldung)](https://www.baeldung.com/java-integer-division-rounding)
    

---
