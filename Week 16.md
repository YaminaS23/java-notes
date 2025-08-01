
# Java Type Conversion and Casting
---

## #️⃣ Type Conversion in Java

### ✅ Automatic (Implicit) Type Conversion

When assigning a **smaller type** to a **larger compatible type**, Java _automatically promotes_ the value.

#### Conditions for Automatic Conversion:

1. Types must be compatible.
    
2. Destination type must be _larger_ than source type.
    

#### Examples of Widening (Safe) Conversions:

|From Type|To Type|
|---|---|
|byte|short, int, long, float, double|
|short|int, long, float, double|
|char|int, long, float, double|
|int|long, float, double|

#### ⚠️ No automatic conversions:

- From numeric types to `char` or `boolean`
    
- Between `boolean` and any other type
    
---

### 🧪 Code Example: Automatic Conversion

```java
public class AutoConversion {
    public static void main(String[] args) {
        int i = 100;
        long l = i; // automatic conversion
        double d = l; // automatic again

        System.out.println("int to long: " + l);
        System.out.println("long to double: " + d);
    }
}
```

**Expected Output:**

```
int to long: 100
long to double: 100.0
```

---

## 📌 What is Type Casting?

Type casting is the process of converting a value from one data type to another. In Java, it is used when:

- Automatic (implicit) conversion is **not allowed**, or
    
- You want to **explicitly convert** between different types.
    

> 🚫 Type casting is **not** about Hollywood roles. It's about converting data types in programming.

---

## 🔄 Two Types of Type Casting in Java

| Type         | Description                                         | Example              |
| ------------ | --------------------------------------------------- | -------------------- |
| **Implicit** | Automatically done by the compiler                  | `double a = 5;`      |
| **Explicit** | Done manually by the programmer using cast operator | `int b = (int) 5.9;` |

---

## 🔄 Casting (Explicit Conversion)

When converting **larger types to smaller types**, or **incompatible types**, use _explicit casting_.

```java
(targetType) value;
```

> 🎯 This is called a **narrowing conversion** and can lead to **data loss or overflow**.

### 🔬 Example 1:

```java
int a = 257;
byte b = (byte) a;
System.out.println(b);  // Outputs: 1 (because 257 % 256 = 1)
```

### ✅ Example 2

```java
double distance = 9.0;
int points = (int) distance;
System.out.println(points);
```

**Expected Output:**

```
9
```

> 💡 The `distance` variable remains 9.0 (unchanged). The value assigned to `points` is 9 — the truncated version.

---

## 🚫 Illegal Assignment Without Type Cast

```java
double distance = 9.0;
int points = distance; // ❌ Compilation error
```

You must use:

```java
int points = (int) distance; // ✅ Valid
```

---

## 📉 Truncation vs Rounding

When casting from a floating-point (like `double`) to an integer type:

- **Decimal part is discarded** (truncation).
    
- No rounding occurs!
    

### Example:

```java
double bill = 26.99;
int dollars = (int) bill;
System.out.println(dollars);
```

**Expected Output:**

```
26
```

> 🔎 26.99 becomes 26, **not** 27. This is called truncation.


---

## 👨‍💻 Full Code Example: Cast Demonstration

```java
public class Conversion {
  public static void main(String[] args) {
    byte b;
    int i = 257;
    double d = 323.142;

    System.out.println("\nConversion of int to byte:");
    b = (byte) i;
    System.out.println("i and b: " + i + " " + b);

    System.out.println("\nConversion of double to int:");
    i = (int) d;
    System.out.println("d and i: " + d + " " + i);

    System.out.println("\nConversion of double to byte:");
    b = (byte) d;
    System.out.println("d and b: " + d + " " + b);
  }
}
```

### ✅ Expected Output:

```
Conversion of int to byte:
i and b: 257 1

Conversion of double to int:
d and i: 323.142 323

Conversion of double to byte:
d and b: 323.142 67
```

---

## ⚙️ Automatic Type Promotion in Expressions

Java promotes **byte**, **short**, and **char** types to **int** when used in expressions.

### ⚠️ Example with Error:

```java
byte b = 50;
b = b * 2;  // ❌ Error! b * 2 is promoted to int
```

### ✅ Correct Version with Casting:

```java
byte b = 50;
b = (byte)(b * 2);  // ✅ Explicit cast to byte
```

---

## 📈 Expression Type Promotion Rules

1. byte, short, char → **int**
    
2. If one operand is **long** → result is **long**
    
3. If one operand is **float** → result is **float**
    
4. If one operand is **double** → result is **double**
    

### Full Code Example: Promotion Chain

```java
public class Promote {
  public static void main(String[] args) {
    byte b = 42;
    char c = 'a';     // Unicode = 97
    short s = 1024;
    int i = 50000;
    float f = 5.67f;
    double d = .1234;

    double result = (f * b) + (i / c) - (d * s);
    System.out.println((f * b) + " + " + (i / c) + " - " + (d * s));
    System.out.println("result = " + result);
  }
}
```

### ✅ Expected Output:

```
238.14 + 556 - 126.3616
result = 667.7784
```

### 🟩 Step : Type Promotions in Expression

```java
double result = (f * b) + (i / c) - (d * s);
```

Java uses **type promotion** in mixed-type arithmetic. Here's how it breaks down:

|Expression|Calculation|Promoted Types|Result|
|---|---|---|---|
|`f * b`|`5.67 * 42`|float * int → float|238.14|
|`i / c`|`50000 / 97`|int / int → int|515 (Note: Original output used `char c = 'a'; // 97`)|
|`d * s`|`0.1234 * 1024`|double * int → double|126.3616|

---

## 🔍 Real-World Example: Money Conversion Error

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);

        
        System.out.print("Enter a dollar amount: ");
        double amount;
        int total;
        amount = keyboard.nextDouble();
        total = (int) (amount * 100); // ✅ Cast double to int
        System.out.println("Total cents: " + total);
        
        keyboard.close();
    }
}
```

### ✅ Input:

```
Enter a dollar amount: 500.2345
```

### ✅ Expected Output:

```
Total cents: 50023
```

> 💡 Use `int` or `long` for currency operations. Avoid `double` due to **precision loss**!

---

## 🎯 Cast Operator with Expressions

### 🤖 Examples:

| Expression                     | Value | Explanation              |
| ------------------------------ | ----- | ------------------------ |
| `(int)(1000.9999)`             | 1000  | Truncates decimal        |
| `(double)(267)`                | 267.0 | Converts to double       |
| `(double)(151 % 2)`            | 1.0   | Modulus then cast        |
| `(double)(151) / 2`            | 75.5  | 151.0 / 2                |
| `(double)(151 / 2)`            | 75.0  | 151/2 = 75 → cast = 75.0 |
| `(int)(2.5 * (double)(1) / 2)` | 12    | = (int)(1.25) = 1        |
| `(int)(2.5 * (double)(1/2))`   | 0     | (1/2) = 0 → 0.0 → 0      |

### 🧪 Expressions

```java
int a = 7, b = 10;
double c = 4.25, d = 5.80;
System.out.println((double)(b/a));       // 1.0
System.out.println((int)(c) + (int)(d)); // 9
System.out.println((int)(c + d));        // 10
System.out.println((double)(a/b) + c);   // 4.25
System.out.println((double)(a)/b + d);   // 6.5
```

---

## 🔤 Cast Between `char` and `int`

```java
System.out.println((int)'J');   // 74
System.out.println((char)74);   // J
System.out.println('J' + '0');  // 122 (No cast needed)
```

Java uses the **Unicode** system to map characters to numeric values.

### Example:

```java
char symbol = '7';
System.out.println((int) symbol);
```

**Expected Output:**

```
55
```

> 🤔 `'7'` is **not** 7. It's Unicode value is **55**. Characters like `'0'` to `'9'` don't map to their digit values.

---

## 🔬 Recommendation for Money/Finance

> 💸 Avoid ❌ `double` for monetary values due to floating-point precision errors.


```java
// Not ideal
double amount = 1.38;
int total = (int)(amount * 100); // Converts 1.38 dollars to 138 cents
```

### 🔍 Better Alternatives

- Use `int` for cents (e.g., $1.38 → 138)
    
- Use `BigDecimal` or `BigInteger` for high precision needs
    
- Use `long` for large money values

---

## 📚 Further Reading

- [Java Language Specification - Type Conversion](https://docs.oracle.com/javase/specs/jls/se21/html/jls-5.html)
    
- [BigDecimal vs Double for Money](https://www.baeldung.com/java-bigdecimal-vs-double)
    
- [Primitive Type Conversions - Oracle Docs](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [Scanner Class - Oracle Docs](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)
    

---

## ✅ Summary

- ✅ Use automatic conversion for widening, compatible types
    
- ⚠️ Use explicit casting when narrowing or precision control is needed
    
- 💡 Promotions can cause errors if not handled carefully
    
- 🚫 Avoid using `double` for money — use `int`, `long`, or `BigDecimal`
    

---

> 🧠 Pro Tip: Always be aware of **data range limits** and **floating-point precision traps**.

---

🧪 Want a challenge?

### 💥 Java Casting Quiz:

1. What is the output of: `(int)(7.9 + 1.1)`?
    
2. What’s wrong with: `byte b = 50; b = b * 2;`?
    
3. What’s the result of: `(double)(3/2)`?
    
4. Why is `(int)(2.5 * (double)(1/2))` equal to 0?
    

DM me for answers, or try solving and I’ll review it 🤓