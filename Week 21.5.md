


# Java Method Definitions & Variables 

---

## #️⃣ Overview

This guide covers method definitions in Java, including method syntax, return types, parameter lists, local/instance variables, the return statement, and accessor methods. It is tailored for Java beginners and includes code examples, explanations, real-world use cases, and structured markdown notes compatible with **Obsidian**.

---

## 📌 Method Structure

### 🔹 A method has two parts:

1. **Header** — Signature of the method
    
2. **Body** — Set of statements to be executed
    

```java
public static void main(String[] args) {
    // Statements go here
}
```

### 🔸 Method Syntax Template:

```java
[accessModifier] [abstract|final] [static] returnType methodName(parameterList) {
    // Statements
}
```

> 🧠 Only `main()` is static in beginner programs. Other methods are non-static unless shared among all objects.

### 🛠️ Example of a non-main method:

```java
public int square(int number) {
    return number * number;
}
```

---

## 🔁 Return Type

- Specifies the type of value a method returns.
    
- Use `void` for methods that don't return anything.
    

```java
public void greet() {
    System.out.println("Hello!");
}
```

### ✅ Return Statement:

```java
return value;
```

> ⚠️ Required for **value-returning** methods.  
> Optional for `void` methods, but **`return;`** can still be used to exit early.

---

## 🧮 Formal Parameters

### 📥 Definition:

Variables in the method header used to receive input values.

```java
public void displayMessage(String message) {
    System.out.println(message);
}
```

### 🔁 Actual vs. Formal Parameters

- **Actual**: Passed during method call
    
- **Formal**: Declared in the method header
    

> When a method is called, actual parameters are copied into formal parameters.

---

## 🔍 Example: Using Parameters

```java
public class MessagePrinter {
    public void printLine(String line) {
        System.out.println(line);
    }

    public static void main(String[] args) {
        MessagePrinter mp = new MessagePrinter();
        mp.printLine("Java is powerful!");
    }
}
```

### ✅ Expected Output:

```
Java is powerful!
```

---

## 🧠 Self-Check Concepts

| #   | Question                           | Answer |
| --- | ---------------------------------- | ------ |
| 1   | Type of formal param in `charAt()` | `int`  |
| 2   | Can a method have no parameters?   | ✅ True |

---

## 🧪 Variable Categories

|Type|Scope|Lifetime|Modifiable Access|Example|
|---|---|---|---|---|
|Instance|Entire class/object|As long as object exists|private/public|`private int age;`|
|Local|Inside a block|Till block ends|No access modifier|`int x = 5;`|
|Formal|Inside method|For method duration|No access modifier|`void greet(String name)`|

### 🧠 Self-Check:

| #   | Question                                | Answer |
| --- | --------------------------------------- | ------ |
| 1   | A local variable is declared inside a   | block  |
| 2   | A local variable has no access modifier | ✅ True |

---

## ⚙️ Initialization

|Variable Type|When Initialized|
|---|---|
|Instance|In constructor or directly|
|Local|Must be initialized before use|
|Formal|On method invocation|

### Examples

```java
// Local
int age = 20;

// Instance
private double interestRate = 0.05;
```

---

## 🔄 Scope

> Determines where the variable is accessible.

### Examples:

```java
public class Demo {
    private int count = 0; // Instance

    public void show() {
        int temp = 5; // Local
        System.out.println(count + temp);
    }
}
```

### 🧠 Self-Check:

| #   | Question                                         | Answer  |
| --- | ------------------------------------------------ | ------- |
| 1   | Is scope of a local variable < formal parameter? | ✅ True  |
| 2   | Do all local variables have same scope?          | ❌ False |

---

## ⏳ Existence

|Type|Creation|Deletion|
|---|---|---|
|Instance|On object creation|On object destruction|
|Local|On method/block execution|On block exit|
|Formal|On method call|On method return|

### 🧠 Self-Check:

| #   | Question                                       | Answer  |
| --- | ---------------------------------------------- | ------- |
| 1   | Does local variable exist throughout method?   | ❌ False |
| 2   | Does formal parameter exist throughout method? | ✅ True  |

---

## 📤 return Statement

### Syntax:

```java
return expression;
```

### ❗ Rules:

- Must match return type
    
- Omitting return in non-void = compile error
    

### Example:

```java
public int add(int a, int b) {
    return a + b;
}
```

### 🧠 Self-Check:

| #   | Question                                      | Answer |
| --- | --------------------------------------------- | ------ |
| 1   | Must value-returning method return something? | ✅ True |
| 2   | Can void methods skip return?                 | ✅ True |

---

## 📄 Javadoc Convention

```java
/**
 * Prints a greeting message
 * @param name the name to greet
 */
public void greet(String name) {
    System.out.println("Hello, " + name);
}
```

- `/** ... */` before method
    
- `@param` for each input
    
- `@return` for return value
    

---

## 🔐 Encapsulation & Information Hiding

> One of the key principles in OOP is **encapsulation**, which means hiding the internal state of an object and requiring all interaction to be performed through methods.

Private instance variables cannot be accessed directly from outside the class. Instead, we use:

- **Accessor Methods** (`get`): To retrieve data
- **Mutator Methods** (`set`): To change data

---

## 👁️ Accessor Methods (Getters)

### Definition:

> Methods that return instance variables without modifying them.

### Syntax:

```java
public dataType getVariableName() {
    return variableName;
}
```

### Convention:

- Method starts with `get`
    
- First letter of variable capitalized
    

### 🧪 Examples:

```java
private int numberOfShares;
private String tickerSymbol;
private double dividend;

public int getNumberOfShares() {
    return numberOfShares;
}

public String getTickerSymbol() {
    return tickerSymbol;
}

public double getDividend() {
    return dividend;
}
```

### 🧠 Self-Check:

| #   | Question                               | Answer  |
| --- | -------------------------------------- | ------- |
| 1   | Can accessor modify instance variable? | ❌ False |
| 2   | Does accessor return a value?          | ✅ True  |

---

## 🛠️ Mutator Methods (Setters)

### ✅ Definition:
A **mutator method** changes ("mutates") the value of an instance variable.

### 🔣 Syntax Template:
```java
public void setDataMember(DataType inDataMember) {
    dataMember = inDataMember;
}
```

> 📌 `void` means the method does not return a value.

### 🧠 Naming Convention:

- Starts with `set`
- Followed by variable name with first letter capitalized (e.g., `setNumberOfShares`)
- Method: `set` + `InstanceVariableName` (capitalize first letter)
- Parameter: `in` + `InstanceVariableName` (capitalize first letter)

### 🧪 Example:
```java
public void setNumberOfShares(int inNumberOfShares) {
    numberOfShares = inNumberOfShares;
}
```

### 🔍 Real-World Use Case:
Imagine an app that manages stocks. You want to change the number of shares a user owns:

```java
stock.setNumberOfShares(100);
```

### 🧠 Self-Check:

| #   | Question                                                         | Answer  |
| --- | ---------------------------------------------------------------- | ------- |
| 1   | True or false: A method can be both an accessor and a mutator.   | False ❌ |
| 2   | True or false: A mutator method may not have a return statement. | True ✅  |


---

## 🏗️ Constructor

A **Constructor** is a special method used to initialize objects. Unlike other methods, it:

- Has no return type
    
- Has the same name as the class
    

### ✅ Syntax:

```java
public ClassName() {
    // Initialize variables
}
```

### 🔍 Example:

```java
public Stock() {
    numberOfShares = 0;
    tickerSymbol = "[NA]";
    dividend = 0.0;
}
```

> ⚠️ Constructor is **not** technically a method.

### 🧠 Self-Check:

| #   | Question                                                                | Answer  |
| --- | ----------------------------------------------------------------------- | ------- |
| 1   | True or false: A constructor is a method.                               | False ❌ |
| 2   | True or false: One purpose of a constructor is to initialize variables. | True ✅  |


---

## 🛠️ Application-Specific Methods

Sometimes, we add methods that perform calculations using instance variables.

### 🔍 Example:

```java
public double yearlyDividend() {
    double totalDividend = numberOfShares * dividend;
    return totalDividend;
}
```

> 📊 Real-world Use: Useful for finance apps that calculate annual stock dividends.

---

## 🧱 Full Example: Stock Class

```java
class Stock {
    // 1. Instance Variables
    private int numberOfShares;
    private String tickerSymbol;
    private double dividend;

    // 2. Constructor
    public Stock() {
        numberOfShares = 0;
        tickerSymbol = "[NA]";
        dividend = 0.0;
    }

    // 3. Application-specific Method
    public double yearlyDividend() {
        double totalDividend = numberOfShares * dividend;
        return totalDividend;
    }

    // 4. Accessors
    public int getNumberOfShares() {
        return numberOfShares;
    }

    public String getTickerSymbol() {
        return tickerSymbol;
    }

    public double getDividend() {
        return dividend;
    }

    // 5. Mutators
    public void setNumberOfShares(int inNumberOfShares) {
        numberOfShares = inNumberOfShares;
    }

    public void setTickerSymbol(String inTickerSymbol) {
        tickerSymbol = inTickerSymbol;
    }

    public void setDividend(double inDividend) {
        dividend = inDividend;
    }

    // 6. toString Method
    public String toString() {
        return numberOfShares + " " + tickerSymbol;
    }
}
```

### 🖨️ Expected Output

```
Stock s = new Stock();
s.setNumberOfShares(100);
s.setTickerSymbol("AAPL");
s.setDividend(1.5);
System.out.println(s.yearlyDividend());   // Output: 150.0
System.out.println(s);                    // Output: 100 AAPL
```


---

## 📚 Further Reading

- [Oracle Java Docs: Methods](https://docs.oracle.com/javase/tutorial/java/javaOO/methods.html)
    
- [W3Schools: Java Methods](https://www.w3schools.com/java/java_methods.asp)
    
- [GeeksForGeeks: Java Methods](https://www.geeksforgeeks.org/methods-in-java/)
    
- [Java Constructors - Oracle Docs](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)
    
- [Java Encapsulation - W3Schools](https://www.w3schools.com/java/java_encapsulation.asp)
    
- [Java Methods - GeeksForGeeks](https://www.geeksforgeeks.org/methods-in-java/)

---

## ✅ Real-World Use Case

### 🔹 Class: BankAccount

```java
public class BankAccount {
    private double balance;

    public BankAccount(double amount) {
        balance = amount;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        balance += amount;
    }
}
```

### 🧾 Output Example:

```java
BankAccount acc = new BankAccount(1000);
acc.deposit(500);
System.out.println(acc.getBalance()); // Outputs: 1500.0
```

---

## ✨ Summary

|Topic|Details|
|---|---|
|Method|Code block to perform a task|
|Return Type|Type of data returned (or void)|
|Parameters|Inputs to a method|
|Variables|Local, Instance, Formal|
|Scope|Defines visibility|
|return|Exits method and sends back value|
|Accessor|Getter method for private variables|

| Element               | Purpose                              |
| --------------------- | ------------------------------------ |
| `getX()`              | Accessor method – returns a value    |
| `setX(value)`         | Mutator method – sets a new value    |
| `ClassName()`         | Constructor – initializes object     |
| `toString()`          | Displays object in readable format   |
| `applicationMethod()` | Custom logic like `yearlyDividend()` |

