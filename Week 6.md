
# Java Data Types

---

## ⚠️ Strong Typing in Java

> Java is a **strongly typed language**, which means:

- Every variable and expression has a type.
    
- All type compatibility is strictly enforced at **compile-time**.
    
- No automatic coercion between conflicting types (unlike JavaScript or Python).
    

**✅ Why this matters:** It provides **robust error checking** and avoids unexpected behavior due to implicit conversions.

---

## 🧱 What is a Data Type?

> A **data type** is a set of values with a set of operations that can be performed on those values.

Examples:

- Names ➡️ Strings
    
- Salary ➡️ Numeric types
    

> 💡 Java separates data into types to prevent meaningless operations (like multiplying names 😅).

---

## 🗂️ Two Categories of Data Types in Java

### 1. **Primitive Data Types** (🔨 Not Objects)

Java has **8 primitive data types**, split into 3 main categories:

|Category|Types|
|---|---|
|Boolean|`boolean` (true or false)|
|Integer (Integral)|`byte`, `short`, `int`, `long`, `char`|
|Floating Point|`float`, `double`|

### 2. **Reference Types** (📦 Objects)

- Includes: `String`, arrays, classes, interfaces, etc.
    
- Stored as **references**, not raw values.
    

![[Pasted image 20250725162906.png]]

---

## 🧮 Primitive Data Types Breakdown

| Data Type | Range/Values                                            | Memory  | Notes                            |     |
| --------- | ------------------------------------------------------- | ------- | -------------------------------- | --- |
| `boolean` | `true/false`                                            | 1 bit   | Only two values (no null)        |     |
| `char`    | 0 to 65535                                              | 2 bytes | Represents a Unicode character   |     |
| `byte`    | -128 to 127                                             | 1 byte  | Smallest integer type            |     |
| `short`   | -32,768 to 32,767                                       | 2 bytes | Used for memory optimization     |     |
| `int`     | -2,147,483,648 to 2,147,483,647                         | 4 bytes | Default for integer literals     |     |
| `long`    | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 8 bytes | Add `L` suffix for long literals |     |
| `float`   | ~±3.4E+38 (6-7 digits precision)                        | 4 bytes | Add `f` or `F` suffix            |     |
| `double`  | ~±1.7E+308 (15 digits precision)                        | 8 bytes | Default for floating point       |     |

> 💡 Use `int` and `double` unless memory optimization is needed.

---

## 🧪 Examples + Code + Output

### Example 1: Using All Primitive Types

```java
public class DataTypeDemo {
    public static void main(String[] args) {
        boolean isJavaFun = true;
        char letter = 'J';
        byte smallNum = 100;
        short mediumNum = 20000;
        int num = 150000;
        long bigNum = 123456789012345L;
        float pi = 3.14f;
        double e = 2.718281828;

        System.out.println("Boolean: " + isJavaFun);
        System.out.println("Char: " + letter);
        System.out.println("Byte: " + smallNum);
        System.out.println("Short: " + mediumNum);
        System.out.println("Int: " + num);
        System.out.println("Long: " + bigNum);
        System.out.println("Float: " + pi);
        System.out.println("Double: " + e);
    }
}
```

**Expected Output:**

```
Boolean: true
Char: J
Byte: 100
Short: 20000
Int: 150000
Long: 123456789012345
Float: 3.14
Double: 2.718281828
```

---

### Example 2: Type Safety in Action

```java
public class TypeErrorDemo {
    public static void main(String[] args) {
        // int result = "Hello" * 5; // ❌ Compile-time error
    }
}
```

> 🚫 Strings cannot be multiplied like in Python. Java will throw an error before it even runs.

---

## 🛠️ Real-World Use Cases

- `int` ➡️ Age, salary, quantity
    
- `double` ➡️ Scientific calculations, currency with decimals
    
- `char` ➡️ Processing names, single characters
    
- `boolean` ➡️ Flags, conditions (`isLoggedIn`, `hasPermission`)
    
- `long` ➡️ Timestamps, IDs in big systems
    

---

## 🧠 Did You Know?

> Java always uses fixed sizes for data types, unlike C/C++ which depends on system architecture.

- `int` is always 32-bit
    
- `long` is always 64-bit
    
- ✅ This ensures code runs the same on all platforms (Write Once, Run Anywhere™ ☕)
    

---

## 🧵 Further Reading

- [Oracle Docs – Primitive Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- [Java Language Specification – Types](https://docs.oracle.com/javase/specs/jls/se17/html/jls-4.html)
    
- [Baeldung - Primitive Types in Java](https://www.baeldung.com/java-primitives)
    

---

## 🧠 Self-Check Time!

> Test yourself without peeking! 👀

1. What’s the range of `byte` in Java?
    
2. What’s the default data type for decimal numbers?
    
3. Can you assign an `int` to a `byte`?
    
4. Which type would you use for an astronomical constant like the speed of light?
    
5. What is the size of a `char` in Java?
    

---

## ✅ Summary

- Java has **8 primitive types** that are **not objects**
    
- Java is **strongly typed**, meaning you can’t mix types recklessly
    
- Each primitive type has a **defined size and range**, platform-independent
    
- Use primitive types for **efficiency** and **performance**
    

> 🔥 Remember: Strings are not primitives in Java. They're objects. And no, you can’t multiply them. Java's not that kind of crazy. 😜

---

Wanna jump to reference types next? Or practice building a mini calculator using `int`, `double`, and `boolean`? 💡