
# Java Numeric Data Types and Operators

---

## 🔢 Types of Arithmetic Operations in Java

Java provides five basic arithmetic operators for numeric data types:

### 🔹 **Binary Arithmetic Operators**

|Operator|Description|
|---|---|
|`+`|Addition|
|`-`|Subtraction|
|`*`|Multiplication|
|`/`|Division|
|`%`|Modulus (Remainder)|

### 🔹 **Unary Arithmetic Operators**

|Operator|Description|
|---|---|
|`+`|Unary plus|
|`-`|Unary minus|

### 🔹 **Compound Assignment Operators**

|Operator|Equivalent To|
|---|---|
|`+=`|`a = a + b`|
|`-=`|`a = a - b`|
|`*=`|`a = a * b`|
|`/=`|`a = a / b`|
|`%=`|`a = a % b`|

### 🔹 **Increment & Decrement**

|Operator|Description|
|---|---|
|`++`|Increment (prefix/postfix)|
|`--`|Decrement (prefix/postfix)|

---

## 🧠 Integer Arithmetic Operations

```java
public class IntegerOperator {
    public static void main(String[] args) {
        System.out.println("12 + 51 = " + (12 + 51));
        System.out.println("-12 + 51 = " + (-12 + 51));
        System.out.println("51 - 12 = " + (51 - 12));
        System.out.println("-51 - 12 = " + (-51 - 12));
        System.out.println("3 * 8 = " + (3 * 8));
        System.out.println("19 / 5 = " + (19 / 5));
        System.out.println("20 / 5 = " + (20 / 5));
        System.out.println("19 % 5 = " + (19 % 5));
        System.out.println("-19 % 5 = " + (-19 % 5));
        System.out.println("19 % -5 = " + (19 % -5));
        System.out.println("-19 % -5 = " + (-19 % -5));
        System.out.println("5 % 19 = " + (5 % 19));
    }
}
```

### ✅ Expected Output:

```
12 + 51 = 63
-12 + 51 = 39
51 - 12 = 39
-51 - 12 = -63
3 * 8 = 24
19 / 5 = 3
20 / 5 = 4
19 % 5 = 4
-19 % 5 = -4
19 % -5 = 4
-19 % -5 = -4
5 % 19 = 5
```

---

## 💡 Floating Point Arithmetic in Java

```java
public class FloatingPointOperator {
    public static void main(String[] args) {
        System.out.println("(12.0 + 49.2) = " + (12.0 + 49.2));
        System.out.println("(12.3 + 49.2) = " + (12.3 + 49.2));
        System.out.println("(12.3 - 49.2) = " + (12.3 - 49.2));
        System.out.println("(12.3 * 49.2) = " + (12.3 * 49.2));
        System.out.println("(12.3 / 49.2) = " + (12.3 / 49.2));
    }
}
```

### ✅ Expected Output:

```
(12.0 + 49.2) = 61.2
(12.3 + 49.2) = 61.5
(12.3 - 49.2) = -36.900000000000006
(12.3 * 49.2) = 605.1600000000001
(12.3 / 49.2) = 0.25
```

> 🔍 Note: Floating-point results might show **rounding errors** due to binary representation.

---

## 📐 Operator Precedence & Associativity

### Precedence Table:

|Operators|Description|Associativity|
|---|---|---|
|`+`, `-` (Unary)|Unary plus, minus|Right to left|
|`*`, `/`, `%`|Multiplication, Division, Mod|Left to right|
|`+`, `-`|Addition, Subtraction|Left to right|

### Example:

```java
int result = -4 * 2 + 8 - 9 / 3 * 5 + 7;
System.out.println(result);
```

#### ✅ Expected Output:

```
-8
```

> Parentheses `()` can change execution order and improve clarity!

### 🧮 Step-by-Step Evaluation:

1. **Unary** `-4` (Right to left): becomes `-4`
    
2. `-4 * 2` → `-8`
    
3. `9 / 3` → `3`
    
4. `3 * 5` → `15`
    
5. Combine left to right:
    
    - `-8 + 8 = 0`
        
    - `0 - 15 = -15`
        
    - `-15 + 7 = -8`

---

## 🧮 Mixed Expression Evaluation

Java **promotes** smaller data types in mixed expressions:

```
byte → short → int → long → float → double
```

### Example:

```java
System.out.println(17 / 5 + 34.0); // 3 + 34.0 = 37.0
System.out.println(12 / 5.0 + 10); // 2.4 + 10 = 12.4
```

### 🧪 Mixed Expression Example

```java
public class MixedExpressions {
    public static void main(String[] args) {
        System.out.println("27 / 11 + 4.0 = " + (27 / 11 + 4.0));
        System.out.println("27 / 11.0 + 4 = " + (27 / 11.0 + 4));
    }
}
```

### ✅ Expected Output

```
27 / 11 + 4.0 = 6.0
27 / 11.0 + 4 = 6.454545454545454
```

---

## 🔗 String + Numeric Concatenation

```java
public class ConcatOperatorNumber {
    public static void main(String[] args) {
        System.out.println("1600 + \" Avenue\" = " + 1600 + " Avenue");
        System.out.println("563 + 34 = " + (563 + 34));
        System.out.println("" + 563 + 34);              // 56334
        System.out.println(563 + 34 + " Main Street"); // 597 Main Street
    }
}
```

### ✅ Output:

```
1600 + " Avenue" = 1600 Avenue
563 + 34 = 597
56334
597 Main Street
```

> 🧠 If the first value is a string, Java treats `+` as concatenation.

---

## 💥 Modulus on Floating Point

```java
public class Modulus {
    public static void main(String[] args) {
        int x = 42;
        double y = 42.25;
        System.out.println("x mod 10 = " + x % 10);
        System.out.println("y mod 10 = " + y % 10);
    }
}
```

### ✅ Output:

```
x mod 10 = 2
y mod 10 = 2.25
```

> 🔧 `%` works for both integers **and** doubles in Java!

---

## 💼 Compound Assignment Operator Examples

```java
class OpEquals {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        int c = 3;
        a += 5;  // a = 6
        b *= 4;  // b = 8
        c += a * b; // c = 3 + 48 = 51
        c %= 6;  // c = 51 % 6 = 3

        System.out.println("a = " + a);
        System.out.println("b = " + b);
        System.out.println("c = " + c);
    }
}
```

### ✅ Output:

```
a = 6
b = 8
c = 3
```

> ✍️ Good habit: Use compound operators for **readability** and **performance**.

---

## 📚 Further Reading

- [Java Operators (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)
    
- [Java Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [Floating Point Arithmetic Issues](https://floating-point-gui.de/)
    

---

## ✅ Self-Check Answers

> Try these first, then reveal 👀

### 🧠 1. What is `27 − 8 / 11 + 4`?

- Answer: `27 - (8 / 11) + 4 = 27 - 0 + 4 = 31`
    

### 🧠 2. What is `(27 − 8) / 11 + 4`?

- Answer: `19 / 11 + 4 = 1 + 4 = 5`
    

### 🧠 3. What is `27 / 11 + 4.0`?

- `2 + 4.0 = 6.0`
    

### 🧠 4. What is `27 / 11.0 + 4`?

- `2.454545 + 4 = 6.454545`
    

---

## 🧠 Real-World Use Cases

- 🧾 Finance Apps: Use float/double carefully due to rounding errors.
    
- 🛒 E-commerce: Use `%` to check discount eligibility or every nth item.
    
- 📊 Analytics Dashboards: Mixed expressions for percentage calculations.
    

---

_Ready to level up? Try rewriting a calculator using all compound operators!_

---