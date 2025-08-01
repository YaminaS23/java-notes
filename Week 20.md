
# Java Relational Operators

---

## 🔎 What are Relational Operators?

Relational operators in Java are used to compare two values or expressions. They return a boolean value — either `true` or `false` — based on the relationship between the operands.

> Relational operators are mainly used in **decision-making** and **looping constructs**.

---

## 🔧 List of Java Relational Operators

| Operator | Meaning                  | Example  | Result |
| -------- | ------------------------ | -------- | ------ |
| `<`      | Less than                | `5 < 7`  | `true` |
| `<=`     | Less than or equal to    | `3 <= 3` | `true` |
| `>`      | Greater than             | `10 > 2` | `true` |
| `>=`     | Greater than or equal to | `9 >= 9` | `true` |
| $==$     | Equal to                 | `4 == 4` | `true` |
| `!=`     | Not equal to             | `5 != 6` | `true` |

> ❌ **Note:** $=<$ is NOT valid in Java. Always use `<=`.

---

## 🧮 Working with Numeric Types

### 🔢 Integer and Double Comparison Example

```java
public class NumericComparison {
    public static void main(String[] args) {
        int numberOne = 22;
        int numberTwo = 7;
        double fractionOne = 5.0 / 11.0;
        double fractionTwo = 6.0 / 11.0;

        System.out.println("numberOne < 22: " + (numberOne < 22));
        System.out.println("numberOne <= 22: " + (numberOne <= 22));
        System.out.println("numberOne == 22: " + (numberOne == 22));
        System.out.println("fractionOne <= fractionTwo: " + (fractionOne <= fractionTwo));
    }
}
```

**Expected Output:**

```
numberOne < 22: false
numberOne <= 22: true
numberOne == 22: true
fractionOne <= fractionTwo: true
```

---

## ⚠️ Floating-Point Precision Issues

Due to how floating-point numbers are stored in memory (IEEE 754), arithmetic results can be **slightly inaccurate**.

### 🤯 Example: Comparing Floating-Point Values (⚠️ Risky!)

```java
public class FloatingComparison {
    public static void main(String[] args) {
        double result = 1.0 / 11.0 * 11;
        System.out.println("result == 1.0: " + (result == 1.0));
        System.out.println("Actual result: " + result);
    }
}
```

**Expected Output:**

```
result == 1.0: true
Actual result: 1.0
```


### 🤯 Example: Double Precision Surprise

```java
public class RelationalOperator {
    public static void main (String[] args) {
        
        double fractionOne = 1.0 / 11.0;
        double fractionTwo = fractionOne + fractionOne + fractionOne + fractionOne + fractionOne + fractionOne;
        double fractionThree = fractionTwo + fractionOne + fractionOne + fractionOne + fractionOne + fractionOne;
        
        System.out.println(" fractionOne = " + fractionOne );
        System.out.println(" fractionTwo = " + fractionTwo );
        System.out.println(" fractionThree = " + fractionThree );
        System.out.println(" (fractionThree == 1.0) is " + (fractionThree == 1.0));
        System.out.println(" (fractionThree > 1.0) is " + (fractionThree > 1.0));
        
    }
    
}
```

**Expected Output:**

```
 fractionOne = 0.09090909090909091
 fractionTwo = 0.5454545454545455
 fractionThree = 1.0000000000000002
 (fractionThree == 1.0) is false
 (fractionThree > 1.0) is true
```

> ✅ Instead of `(x == y)`, use `Math.abs(x - y) <= ERROR_ALLOWED`

```java
final double ERROR_ALLOWED = 1.0E-14;
if (Math.abs(x - y) <= ERROR_ALLOWED) {
    // Considered equal
}
```

### ✅ Safe Comparison with `double`

```java
public class SafeDoubleComparison {
    public static void main(String[] args) {
        final double ERROR_ALLOWED = 1.0E-14;
        double x = 1.0;
        double y = 1.0 / 11.0 * 11;

        System.out.println("Close enough: " + (Math.abs(x - y) <= ERROR_ALLOWED));
    }
}
```

**Expected Output:**

```
Close enough: true
```

---

## 🔡 Comparing Characters

Characters are compared based on their **Unicode values**. Example:

- `'A'` = 65
    
- `'a'` = 97
    
- `' '` (space) = 32
    
- `'8'` = 56
    

### 🔠 Character Comparison Example

```java
public class CharRelationalOperator {
    public static void main(String[] args) {
        char space = ' ';
        char upperA = 'A';
        char lowerA = 'a';
        char upperZ = 'Z';
        char char8 = '8';

        System.out.println("space < 'A': " + (space < 'A'));
        System.out.println("space == 32: " + (space == 32));
        System.out.println("'A' < 'a': " + (upperA < lowerA));
        System.out.println("'Z' < 'a': " + (upperZ < lowerA));
        System.out.println("'8' < 8: " + (char8 < 8));
    }
}
```

**Expected Output:**

```
space < 'A': true
space == 32: true
'A' < 'a': true
'Z' < 'a': true
'8' < 8: false
```

> `'b' < 'H'` is **false** because `'b'` (98) is greater than `'H'` (72)

### 🔍 Step : Running Comparisons and Outputs

##### ✅ 1. `space < 'A'`

- `' '` = 32, `'A'` = 65
    
- `32 < 65` → `true`
    

```java
System.out.println("space < 'A': " + (space < 'A'));
```

##### ✅ 2. `space == 32`

- `' '` = 32 (ASCII)
    
- `32 == 32` → `true`
    

```java
System.out.println("space == 32: " + (space == 32));
```

##### ✅ 3. `'A' < 'a'`

- `'A'` = 65, `'a'` = 97
    
- `65 < 97` → `true`
    

```java
System.out.println("'A' < 'a': " + (upperA < lowerA));
```

##### ✅ 4. `'Z' < 'a'`

- `'Z'` = 90, `'a'` = 97
    
- `90 < 97` → `true`
    

```java
System.out.println("'Z' < 'a': " + (upperZ < lowerA));
```

##### ❌ 5. `'8' < 8`

- `'8'` = 56, `8` is just an int literal
    
- `56 < 8` → `false`
    

```java
System.out.println("'8' < 8: " + (char8 < 8));
```

---

## 🔄 Relational Operators in Real-World Use Cases

- 🔐 Security check: `if (age >= 18)` → Grant access
    
- 📦 Stock filter: `if (price <= budget)` → Show product
    
- 📝 Score evaluation: `if (score == 100)` → Perfect!
    
- 🔍 Character sorting: `'A' < 'B'` → Alphabetical order
    

---

## 🧊 Real-World Example: Celsius to Fahrenheit

```java
import java.util.Scanner;

public class CelsiusToFahrenheit {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        System.out.print("Enter Celsius: ");
        double celsius = keyboard.nextDouble();

        double fahrenheit = 9.0 / 5.0 * celsius + 32.0;
        System.out.println("Fahrenheit: " + fahrenheit);

        System.out.print("Is room temperature (69.8)? ");
        System.out.println(fahrenheit == 69.8);
        keyboard.close();
    }
}
```

**Input:**

```
Enter Celsius: 21
```

**Expected Output:**

```
Fahrenheit: 69.80000000000001
Is room temperature (69.8)? false
```

> 😱 Java uses IEEE 754 floating-point precision! Always expect rounding issues!

✅ Recommended Fix:

```java
System.out.println(Math.abs(fahrenheit - 69.8) <= 0.01);
```

🧠 _What it does:_

- Uses `Math.abs` to find the difference.
    
- Compares it within a small **tolerance (0.01)**.
    
- Returns `true` if the difference is small enough.

---

## 🧍‍♂️ Comparing Objects

You can't use `<`, `>`, `<=`, `>=` for objects like `String`, `Student`, etc.

Use `.equals()` for equality:

**Example 1:**

```java
String name1 = "Luffy";
String name2 = "Luffy";
System.out.println(name1 == name2);        // true depending on reference
System.out.println(name1.equals(name2));   // Always true if content matches
```

**Example 2:**

```java
String a = new String("Hello");
String b = new String("Hello");

System.out.println(a == b);         // false, different objects
System.out.println(a.equals(b));    // true, same content
```

- Objects don't have a natural ordering.
    
- Use `.equals()` to test object equality, **not** $==$ (which tests reference equality).
    
- For ordering, implement `Comparable<T>` interface or use `Comparator<T>`.
    

> 	✨ We'll dive deeper into object comparisons and `.compareTo()` in **Lectures!**

---
## 📋 Java vs. C/C++: Important Difference

- In **C/C++**:
    
    ```c
    int done = 0;
    if (!done) {...}  // valid
    ```
    
- In **Java**:
    
    ```java
    int done = 0;
    if (done == 0) {...} // correct
    if (done) {...} // ❌ INVALID
    ```
    

> In Java, `true` and `false` are **strict boolean types**, not just numbers.

---

## 📌 Summary Table: Comparison Operators

| Symbol | Meaning                     | Example                    |
| ------ | --------------------------- | -------------------------- |
| $==$   | is equal to                 | `myGuess == winningNumber` |
| `!=`   | is not equal to             | `5 != numberOfCows`        |
| `<`    | is less than                | `strikes < 3`              |
| `>`    | is greater than             | `score > 70`               |
| `<=`   | is less than or equal to    | `sum <= 25`                |
| `>=`   | is greater than or equal to | `marks >= 50`              |

---

## 📚 Further Reading

- 🔗 [Oracle Java Docs - Operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op2.html)
    
- 🔗 [IEEE Floating Point Guide](https://floating-point-gui.de/)
    
- 🔗 [Baeldung - Comparing Floats and Doubles in Java](https://www.baeldung.com/java-comparing-doubles)
    

---

## ✅ Self-Check Answers

5. ❌ False: `<=` cannot be written as $=<$
    
6. ✅ True: Java supports relational operators.
    
7. ✅ `3 <= 3` → `true`
    
8. ❌ `3 < 3` → `false`
    
9. ✅ `'A' <= 65` → `true`
    
10. ✅ `'a' > 'Z'` → `true`
    

---

💡 **Pro Tip:** Use `System.out.println()` generously when debugging comparisons in Java.

> 🔍 Print the **actual value** before comparing it with something else. Surprises often hide in decimals!
