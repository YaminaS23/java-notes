
# Java Floating Point Data Types

---

## 📌 Overview

Floating point data types in Java are used to handle **real numbers**, which include both an integer and a **fractional part**. They're essential when working with measurements, scientific calculations, or anything involving **precision** beyond whole numbers.

---

## 🔢 What is a Floating Point Number?

Floating-point numbers contain:

- An **integer part**
    
- A **fractional part**
    
- A **decimal point** separating the two
    

### ✅ Valid Floating Point Examples:

```text
123.456   ✅
123.0     ✅
123.      ✅
0.456     ✅
.456      ✅
```

> ⚠️ Either the integer or the fractional part may be omitted, but **the decimal point must be present.**

---

## 💡 Good Programming Practice 2.8

> 🚫 Avoid using `float` when dealing with real numbers in Java.  
> ✅ Use `double` instead to avoid truncation or precision errors like:
> 
> - `"Possible loss of data"`
>     
> - `"Truncation from double to float"`
>     

---

## 📘 Note: Float vs Double Literals in Java

By **default**, Java treats any floating-point literal as a `double`.

To specify a `float` explicitly, **append** `f` or `F` at the end of the number:

```java
float myFloat = 123.456F;
double myDouble = 123.456;
```

> 👀 `123.456` is a `double`, but `123.456F` is a `float`.

---

## 📚 Self-Check Answers

> 1. Area of a property is of the type ➤ `double`
>     
> 2. The number of completed years of service is of the type ➤ `int`
>     

---

## 🌐 Advanced Topic: Floating Point Notation

- `0.456` is **not** an octal value despite starting with a `0`
    
- Floating-point values are always **decimal-based** in Java
    

Java supports:

- **Scientific Notation** (e.g. `1.2E3` → 1200)
    
- **Floating Point Notation** (e.g. `123.45`)
    

### 📊 Table: Floating Point Data Types

|Data Type|Width (Bits)|Approximate Range|Precision|Memory|
|---|---|---|---|---|
|`float`|32|1.4E-45 to 3.4E+38|6-7 digits|4 bytes|
|`double`|64|4.9E-324 to 1.8E+308|~15 digits|8 bytes|

---

## 🔬 Real-World Use Cases

- 📐 Calculating area, volume, distance
    
- 💸 Representing money (carefully!)
    
- 🌡️ Storing temperature, pressure, etc.
    
- 📊 Statistical analysis and AI models
    
- 🧮 Scientific and engineering simulations
    

---

## ⚙️ Java Code Examples

### 🟢 Example 1: Using `double` to compute area of a circle

```java
public class Area {
    public static void main(String[] args) {
        double pi, r, a;
        r = 10.8;          // radius of the circle
        pi = 3.1416;       // value of pi
        a = pi * r * r;    // formula for area of circle

        System.out.println("Area of circle is " + a);
    }
}
```

**Expected Output:**

```text
Area of circle is 366.132288
```

> ✅ Use `double` when higher precision is required!

---

### ✅ Example 2: Declaring `float` Variables

```java
public class Weather {
    public static void main(String[] args) {
        float highTemp = 38.7f;
        float lowTemp = 22.3f;

        System.out.println("High: " + highTemp + "°C");
        System.out.println("Low: " + lowTemp + "°C");
    }
}
```

**Expected Output:**

```
High: 38.7°C
Low: 22.3°C
```

> ⚠️ Without the `f` suffix, Java will throw an error because it expects a `double` by default.

---

### 🟠 Example 3: Float vs Double Precision

```java
public class PrecisionDemo {
    public static void main(String[] args) {
        float floatVal = 1.23456789F;
        double doubleVal = 1.2345678901234567;

        System.out.println("Float Value: " + floatVal);
        System.out.println("Double Value: " + doubleVal);
    }
}
```

**Expected Output:**

```text
Float Value: 1.2345679
Double Value: 1.2345678901234567
```

> 🎯 `double` retains more digits of precision than `float`

---

### 🔵 Example 4: Scientific Notation in Java

```java
public class SciNotation {
    public static void main(String[] args) {
        double val1 = 1.23E3;  // 1230.0
        double val2 = 4.56E-2; // 0.0456

        System.out.println("Value 1: " + val1);
        System.out.println("Value 2: " + val2);
    }
}
```

**Expected Output:**

```text
Value 1: 1230.0
Value 2: 0.0456
```

> 📈 Scientific notation is useful when dealing with **very large/small** numbers

### ✅ Example 5: Scientific Notation in Java Again

```java
public class SciNotation {
    public static void main(String[] args) {
        double avogadro = 6.022E23;
        double small = 4.9e-324;

        System.out.println("Avogadro's number: " + avogadro);
        System.out.println("Smallest double: " + small);
    }
}
```

**Expected Output:**

```
Avogadro's number: 6.022E23
Smallest double: 4.9E-324
```

> 💡 Java uses **E notation** (scientific notation) to represent very large or small real numbers.

---

## 🧮 Summary

- Java supports two floating-point types: `float` (32-bit) and `double` (64-bit)
    
- Prefer `double` for most use cases due to better precision and fewer conversion errors
    
- Use `float` when memory is constrained or performance matters **and** precision isn't critical
    
- All math functions like `Math.sin()` return `double` by default
    

---

## 📖 Further Reading

- [📜 Oracle Docs – Floating Point Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [🔍 IEEE 754 Standard for Floating-Point Arithmetic](https://en.wikipedia.org/wiki/IEEE_754)
    
- [🔧 Java Math API – java.lang.Math](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Math.html)
    

---

## 🧠 Mini Quiz Time!

1. What's the precision range of `double`?
    
2. Which type will you use to store `12.345F` in Java?
    
3. How would you represent `3.2 × 10^5` in Java using scientific notation?
    
4. What happens if you assign a double to a float without casting?
    

_Wanna go full-on CS geek mode? Keep floating with more Java fun!_ 🌊💻