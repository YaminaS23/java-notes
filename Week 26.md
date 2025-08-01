
# Ternary Operator (`?:`)  &  System.exit() Method

---

## 🔍 Overview

Java provides a special **ternary operator** (`?:`) that can replace simple `if...else` statements, especially for value assignments. It's a compact, readable way to conditionally assign a value based on a boolean expression.

> 📌 It's called the **conditional operator** and is the **only ternary operator** in Java.

---

## 🧪 Syntax of the Ternary Operator

```java
variable = (condition) ? valueIfTrue : valueIfFalse;
```

> 🧠 **Think of it as:** _"If the condition is true, assign valueIfTrue; otherwise, assign valueIfFalse"_

---

## ✅ Replacing an `if...else` Statement

### 🚫 Traditional `if...else`:

```java
if (valueOne <= valueTwo) {
    minValue = valueOne;
} else {
    minValue = valueTwo;
}
```

### ✅ Using the Ternary Operator:

```java
minValue = (valueOne <= valueTwo) ? valueOne : valueTwo;
```

> 🎯 Use the ternary operator when you're assigning a value based on a condition.

### 🛠️ More Theory

- The conditional operator always **returns a value**.
    
- It's only a replacement for _value-producing_ `if-else` statements, **not** for all forms of control flow!
    

### 🧑‍💻 **Code Example : Payroll with Overtime**

Suppose an employee gets overtime pay (1.5x) for hours > 40.

#### 🔗 `if-else` approach

```java
if (hoursWorked <= 40)
    pay = hoursWorked * payRate;
else
    pay = 40 * payRate + 1.5 * payRate * (hoursWorked - 40);
```

#### 🔗 Ternary Operator approach

```java
pay = (hoursWorked <= 40) ?
        (hoursWorked * payRate) :
        (40 * payRate + 1.5 * payRate * (hoursWorked - 40));
```

#### **Expected Output:**

> If hoursWorked = 35, pay = 35 * payRate
> 
> If hoursWorked = 50, pay = 40 * payRate + 1.5 * payRate * 10


### 👀 Real-World Use Cases

- Calculating grades: `grade = (score >= 50) ? "Pass" : "Fail";`
    
- Picking a string for error or success: `status = (success) ? "OK" : "ERROR";`
    
- Choosing between two numbers, objects, etc.

---

## 🧑‍💻 Code Example: Absolute Value Using `?:`

```java
// Demonstrate ?: (ternary operator)
public class Ternary {
    public static void main(String[] args) {
        int i, k;

        i = 10;
        k = i < 0 ? -i : i; // get absolute value
        System.out.println("Absolute value of " + i + " is " + k);

        i = -10;
        k = i < 0 ? -i : i;
        System.out.println("Absolute value of " + i + " is " + k);
    }
}
```

### 🖨️ Expected Output:

```
Absolute value of 10 is 10
Absolute value of -10 is 10
```

---

## 🌐 Real-World Example: Divide Safely

```java
// Prevent division by zero
int ratio = denom == 0 ? 0 : num / denom;
```

> 🚨 Avoid runtime errors by using ternary operator to validate conditions (like divide-by-zero).

---

## 🏨 "A Classy Hotel" Challenge: Room Assignment

Imagine a program assigning rooms based on **smoking preference** using ternary:

```java
String roomType = smoking ? "Smoking Room" : "Non-Smoking Room";
System.out.println("Assigned: " + roomType);
```

- Add subclass `LuxuryRoom` extending `Room`
    
- Add max occupancy validation:
    

```java
if (guests <= maxOccupancy) {
    assignRoom();
} else {
    System.out.println("Too many guests!");
}
```

---

## 📋 Ternary Operator Rules (Quick Table)

|Condition Type|Must return a boolean|
|---|---|
|Value If True|Must match Value If False|
|Value If False|Must match Value If True|
|Return Type|Cannot be void|

> 🧠 Ternary is best used for short, readable conditionals. Avoid for complex logic.

---

## 🔥Step-by-Step Code Example with User Input

Let's make a little program where the user enters two numbers and the program tells which one is smaller using **the ternary operator**.


```java
import java.util.Scanner;

public class MinValueTernary {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter first number: ");
        int num1 = scanner.nextInt();
        
        System.out.print("Enter second number: ");
        int num2 = scanner.nextInt();

		// Use the ternary operator to find the smaller value
        int min = (num1 <= num2) ? num1 : num2;
        
        System.out.println("The smaller number is: " + min);
        
        scanner.close();
    }
}
```

### 🖨️ Input:

```
Enter first number: 5
Enter second number: 10
```

### 🖨️ Expected Output:

```
Enter first number: 5
Enter second number: 10
The smaller number is: 5
```

---

## 💡 Best Practices

✅ Use for:

- Assigning values based on simple conditions
    
- Avoiding multiple `if...else` blocks
    

🚫 Avoid:

- Nesting ternary operators (very unreadable)
    
- Complex or multiline logic inside ternary
    

---

## 🟥 The `System.exit()` Method

### 📌 Purpose

The `System.exit()` method is used to **immediately terminate** the currently running Java program. It's rarely needed, but can save your program from disaster if continuing is pointless (like division by zero, critical error, or when required by `JOptionPane`).

### 🧑‍💻 **Code Example: Safe Division**

```java
if (numberOfWinners == 0) {
    System.out.println("Error: Dividing by zero.");
    System.exit(0); // Normal termination
} else {
    oneShare = payoff / numberOfWinners;
    System.out.println("Each winner will receive $" + oneShare);
}
```

#### **Expected Output:**

> If numberOfWinners = 0:
> 
> Error: Dividing by zero.

> Program stops here—no further code runs!

> If numberOfWinners = 4:
> 
> Each winner will receive $ [calculated_share]

### ⚙️ How `System.exit()` Works

- `System` is a Java core class, always available (no import needed).
    
- `exit(int status)` ends the program:
    
    - `0` = normal termination
        
    - `1` or other = abnormal termination (not an error, but the OS will see it as not normal)
        
- Only use `exit()` when truly necessary!
    

### 👀 Real-World Use Cases

- Fatal errors (e.g., critical missing input, file corruption, division by zero)
    
- Programs that use **JOptionPane** dialogs (require `System.exit()` to properly close)
    
- Command-line tools with unrecoverable state
    

> ⚠️ **Warning:**
> 
> - Overuse of `System.exit()` is bad design! Try to let your code finish normally, use exceptions for error handling.
>     

### 🚩 Table: System.exit() Arguments

| Argument | Meaning              | Typical Use               |
| -------- | -------------------- | ------------------------- |
| 0        | Normal termination   | End of main, no errors    |
| 1+       | Abnormal termination | Critical error, notify OS |

> 📝 **Note:**
> 
> - Does _not_ mean the program succeeded! Just that it stopped in a controlled way.
>

---

## 📚 Further Reading

- [Oracle Java Docs – Operators](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/opsummary.html)
    
- [Baeldung – Java Ternary Operator](https://www.baeldung.com/java-ternary-operator)
    
- [GeeksforGeeks – Conditional Operator in Java](https://www.geeksforgeeks.org/conditional-or-ternary-operator-in-java/)
    
- [System.exit() explained - Baeldung](https://www.baeldung.com/java-system-exit)
    
- [System.exit() - Oracle Java SE API](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/System.html#exit\(int\))

---

## 🧠 Remember:

> "You learn Java the same way you get to Carnegie Hall: Practice! Practice! Practice!"

🧪 Want a quiz on Ternary Operator or practice challenges? Just say the word! 💬

---

## 🔁 Java Version Compatibility

✅ **Ternary Operator `?:`** has been part of Java since the very beginning — **Java 1.0**. It's not an outdated or deprecated feature. It's **still valid in the latest Java versions (Java 21+)**.

✅ Works in all modern IDEs: IntelliJ IDEA, Eclipse, NetBeans, BlueJ, etc.

---






