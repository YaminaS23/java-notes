
# Java Logical Operators

---

## 📌 Overview

Logical operators in Java allow us to create complex conditional expressions by combining two or more boolean expressions. They are crucial in control flow and are used in `if`, `while`, `for`, and other conditional statements.

> These operators evaluate `boolean` expressions and return a boolean result (`true` or `false`).

---

## #️⃣ Logical Operators Summary Table

| Operator | Name                            | Type                           | Symbol                     | Description                                      |
| -------- | ------------------------------- | ------------------------------ | -------------------------- | ------------------------------------------------ |
| `!`      | Logical NOT                     | Unary                          | `!`                        | Negates a boolean value.                         |
| `&&`     | Logical AND (short-circuit)     | Binary                         | `&&`                       | Returns true only if **both** operands are true. |
| `        |                                 | `                              | Logical OR (short-circuit) | Binary                                           |
| `&`      | Logical AND (non-short-circuit) | Binary                         | `&`                        | Same as `&&`, but always evaluates both sides.   |
| `        | `                               | Logical OR (non-short-circuit) | Binary                     | `                                                |
| `^`      | Logical XOR                     | Binary                         | `^`                        | Returns true **only if** operands are different. |
| $==$     | Equality                        | Binary                         | $==$                       | Returns true if values are equal.                |
| `!=`     | Inequality                      | Binary                         | `!=`                       | Returns true if values are not equal.            |
| `?:`     | Ternary (if-else)               | Ternary                        | `?:`                       | Short form for `if-else` logic.                  |

---

## ✅ Logical NOT (`!`) Operator

Negates the value of a boolean expression.

```java
boolean fileMissing = false;
boolean fileFound = !fileMissing; // fileFound is true
```

### Truth Table:

|Operand|!Operand|
|---|---|
|true|false|
|false|true|

> ❗ Useful for toggling or reversing a boolean value.

---

## ✅ Logical AND (`&&`) Operator (Short-circuit)

Returns `true` if **both** operands are true.

```java
int age = 6;
if (age > 4 && age < 8) {
    System.out.println("Child is in early childhood range.");
}
```

### Truth Table:

| A     | B     | A && B |
| ----- | ----- | ------ |
| false | false | false  |
| false | true  | false  |
| true  | false | false  |
| true  | true  | true   |

---

## ✅ Logical OR (`||`) Operator (Short-circuit)

Returns `true` if **at least one** operand is true.

```java
int age = 10;
if (age < 4 || age > 8) {
    System.out.println("Age is not between 4 and 8.");
}
```

### Truth Table:

| A     | B     | A \|\| B |
| ----- | ----- | -------- |
| false | false | false    |
| false | true  | true     |
| true  | false | true     |
| true  | true  | true     |

---

## ✅ Logical XOR (`^`) Operator

Returns `true` only if **exactly one** operand is true.

```java
boolean a = true;
boolean b = false;
System.out.println(a ^ b); // true
```

### Truth Table:

|A|B|A ^ B|
|---|---|---|
|false|false|false|
|false|true|true|
|true|false|true|
|true|true|false|

> ⚠️ XOR is rarely used in high-level application logic but useful in algorithmic problems.

---

## ⚡ Short-Circuiting Explained

Java short-circuits `&&` and `||`. That means:

- `A && B`: If `A` is false, `B` is **never evaluated**.
    
- `A || B`: If `A` is true, `B` is **never evaluated**.
    

### ✅ Safe Division Example:

```java
if (denominator != 0 && numerator / denominator > 10) {
    System.out.println("Valid division result");
}
```

> ✅ Prevents division by zero errors! Always use short-circuit `&&` for such cases.

### ⚠️ Using non-short-circuit `&` may cause errors:

```java
if (denominator != 0 & numerator / denominator > 10) {
    // Both sides are evaluated, possible crash if denominator = 0
}
```

---

## 🧪 Self Check – Practice

1. What is the result of `(false && false) || true`?
    
    > `false || true` → `true`
    
2. What is `false && (false || true)`?
    
    > `false && true` → `false`
    

---

## 💻 Full Java Code Example: Truth Tables

```java
public class LogicalOperator {
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;

        System.out.println("Logical NOT:");
        System.out.println("!true = " + !a);
        System.out.println("!false = " + !b);

        System.out.println("\nLogical AND:");
        System.out.println("true && false = " + (a && b));
        System.out.println("true && true = " + (a && true));

        System.out.println("\nLogical OR:");
        System.out.println("true || false = " + (a || b));
        System.out.println("false || false = " + (b || false));

        System.out.println("\nLogical XOR:");
        System.out.println("true ^ false = " + (a ^ b));
        System.out.println("true ^ true = " + (a ^ true));
    }
}
```

### 🔎 Expected Output

```
Logical NOT:
!true = false
!false = true

Logical AND:
true && false = false
true && true = true

Logical OR:
true || false = true
false || false = false

Logical XOR:
true ^ false = true
true ^ true = false
```

---

## 🔍 Real-World Use Cases

- ✅ Login validation: `if (usernameValid && passwordValid)`
    
- ✅ Form input check: `if (!input.isEmpty())`
    
- ✅ Game logic: `if (playerHealth > 0 || hasRevivePotion)`
    
- ✅ Safe resource access: `if (fileExists && canRead)`
    

---

## 🔗 Further Reading

- [Oracle Java Docs – Operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/opsummary.html)
    
- [GeeksforGeeks – Logical Operators in Java](https://www.geeksforgeeks.org/logical-operators-in-java/)
    
- [W3Schools – Java Logical Operators](https://www.w3schools.com/java/java_operators.asp)
    

---

## 🏁 Final Notes

> Java’s logical operators haven’t changed across versions — from Java SE 5 to Java 21, these logical operators behave consistently. No version-specific changes.

> Remember: short-circuit `&&` and `||` are preferred for performance and safety!

Stay logical, code smarter! 🧠💻✨
