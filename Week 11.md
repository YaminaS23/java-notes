
# Named Constants and Variables

---

## 🔹 What Are Named Constants & Variables?

### 📦 Memory and Data Types

> Every program stores data in memory during execution. Each memory cell has a unique address.

|**Data Type**|**Bytes Used**|
|---|---|
|`int`|4 bytes|
|`double`|8 bytes|

👉 The **data type** determines:

- How much **memory** is allocated.
    
- Which **operations** are allowed on the stored data.
    

### 💡 Identifiers vs Memory Addresses

> Instead of manually dealing with memory addresses, Java allows us to use **identifiers** (names) for variables and constants.

---

## 🔐 Named Constants in Java

### 🚫 Immutable Values

> Some values should **never change** during execution. E.g., tax rates, conversion ratios, age limits.

### ✅ Syntax

#### Class-Level Named Constant:

```java
public static final dataType IDENTIFIER = literal;
```

#### Method-Level Named Constant:

```java
final dataType IDENTIFIER = literal;
```

### 💬 Explanation:

- `final`: Value **cannot be changed**
    
- `static`: One copy shared across all instances (optional at class level)
    

### 🔠 Naming Convention

> Use **UPPERCASE** and **underscores**:

```java
public static final double POUND_TO_KILOGRAM = 0.454;
```

### ✅ Good Practices:

- ✅ Use `final` for unchangeable values.
    
- ✅ Declare constants for **magic numbers**.
    
- ✅ Makes your code **readable** and **maintainable**.
    

---

### 📌 Examples of Named Constants

```java
public class ConstantsExample {
    public static final char PERCENTAGE = '%';
    public static final int MAXIMUM_ALLOWED_WEIGHT = 4000;

    public static void main(String[] args) {
        final float ERROR_ALLOWED = 0.01F;
        final double POUND_TO_KILOGRAM = 0.454;

        System.out.println("Percentage: " + PERCENTAGE);
        System.out.println("Max Weight: " + MAXIMUM_ALLOWED_WEIGHT);
        System.out.println("Error Margin: " + ERROR_ALLOWED);
        System.out.println("Conversion Rate: " + POUND_TO_KILOGRAM);
    }
}
```

**🖥 Expected Output:**

```
Percentage: %
Max Weight: 4000
Error Margin: 0.01
Conversion Rate: 0.454
```

---

## 🔄 Variables in Java

### 🧮 Variables Are Mutable

> Variables store data that **can change** during execution.

### 🔀 Types of Variables

|**Scope**|**Type**|**Declared At**|
|---|---|---|
|Class-level|Instance Variable|Inside class, no static|
|Class-level|Static Variable|Inside class, with static|
|Block-level|Local Variable|Inside method/block|
|Block-level|Parameter Variable|Method parameter|

### 🔤 Syntax

#### Instance Variable

```java
[accessModifier] dataType identifierOne [= value];
```

#### Static Variable

```java
[accessModifier] static dataType identifierOne [= value];
```

#### Parameter Variable

```java
dataType parameterName
```

#### Local Variable

```java
dataType identifierOne [= value];
```

---

### 📌 Examples of Variables

```java
public class VariableExample {
    static int staticCounter = 0; // static/class-level
    int instanceCounter = 0; // instance-level

    public void displayData(char nextCharacter, int totalGamesPlayed) {
        double stateTaxRate = 6.85; // local variable
        String nextLine = "Have a close look at me!"; // reference variable

        System.out.println("Char: " + nextCharacter);
        System.out.println("Games Played: " + totalGamesPlayed);
        System.out.println("Tax Rate: " + stateTaxRate);
        System.out.println("Message: " + nextLine);
    }

    public static void main(String[] args) {
        VariableExample ve = new VariableExample();
        ve.displayData('A', 25);
    }
}
```

**🖥 Expected Output:**

```
Char: A
Games Played: 25
Tax Rate: 6.85
Message: Have a close look at me!
```

---

## 📚 Memory Visualization

### Primitive vs Reference Variables

|**Type**|**Stores**|**Example**|
|---|---|---|
|Primitive|Actual value|`int total = 50;`|
|Reference|Address of object|`String name = "Yamina";`|

### 🧠 Visualization:

```
Primitive:  
nextCharacter → '?'  (2 bytes)
totalGamesPlayed → 25 (4 bytes)
stateTaxRate → 6.85 (8 bytes)

Reference:
nextLine → memory address → "Have a close look at me!"
```

---

## ⚠️ Common Mistakes & Notes

> 🔴 All constants & variables **must be declared** before use.

> 🔴 In Java, using undeclared variables is a **syntax error**.

> 🔴 Primitive variables **must be initialized** before use.

> 🟡 Reference variables store the **reference (memory address)**, not the object itself.

---

## ✅ Benefits of Named Constants

1. **Maintainability**: Change in one place.
    
2. **Readability**: Easier to understand code.
    
3. **Compiler Safety**: Typos in names caught by compiler.
    

---

## 🧠 Real-World Use Cases

- 🏦 Tax calculations: `TAX_RATE`
    
- 🛒 E-commerce inventory: `MAX_CART_ITEMS`
    
- 📐 Physics calculations: `GRAVITATIONAL_CONSTANT`
    
- 🌐 Web apps: `API_ENDPOINT_URL`
    

---

## 📖 Further Reading

- 🔗 [Java Language Specification - Variables](https://docs.oracle.com/javase/specs/)
    
- 🔗 [Oracle Java Tutorials](https://docs.oracle.com/javase/tutorial/java/index.html)
    
- 🔗 [Primitive Types in Java (Oracle)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    

---

## 📝 Quiz Time!

1. What's the difference between `final` and `static final`?
    
2. Why is it better to use a named constant instead of a literal?
    
3. What does a reference variable actually store?
    
4. What error will the Java compiler throw if a variable is used without declaration?
    

---

Stay tuned for Week 12 🔥 Let me know if you want a practice sheet or a coding worksheet on this topic 💻💡