
# Assignment Operator and Changing Data Values

---

## 📌 Overview

In Java, variables store data. You can **change the value of a variable** using:

- Assignment statements
    
- Increment (`++`) or decrement (`--`) operators
    

> 🔁 The **assignment operator** ($=$) is the core tool for updating variable values.

---

## ⚙️ Assignment Statement Syntax

### ✅ Syntax

```java
variable = expression;
```

### ✅ Components:

- **Left-hand side (LHS)**: A variable
    
- **Right-hand side (RHS)**: An expression or value
    

> 💡 The RHS is evaluated first. The result is then stored in the LHS variable.

---

## 🧪 Example 1 – Basic Assignments

```java
char grade;
double currentScore, totalScore = 0.0;
grade = 'A';
currentScore = 30.0;
totalScore = 95.7;
```

> 🧠 Once `grade = 'A';` executes, any previous value in `grade` is lost forever.

---

## 🔍 Key Concept – Java ≠ Math

In mathematics:

> `y = 5` means _y is equal to 5_.

In Java:

> `y = 5` means _store the value 5 in y_.

### ⚠️ Data Type Compatibility Rules:

|RHS Data Type|LHS Type: `int`|LHS Type: `double`|
|---|---|---|
|`37`|✅ Match|✅ Promoted to `37.0`|
|`12.5F`|❌ Error|✅ Promoted to `12.5`|
|`56.8`|❌ Error|✅ Match|

> 🔺 If LHS has **narrower** range than RHS → Error: `possible loss of precision`  
> 🔺 If type mismatch → Error: `incompatible types`

---

## 🚫 Example 2 – Compilation Errors

### ❌ Faulty Code:

```java
public class Assignments {
    public static void main(String[] args) {
        int numberOfStudents;
        float toalPoints;
        String heading;
        boolean smartStudents;

        numberOfStudents = 25.0;         // ❌ double to int
        toalPoints = 2000;               // ✅ int to float is okay
        heading = 2004;                  // ❌ int to String
        smartStudents = "All students";  // ❌ String to boolean
    }
}
```

### 💥 Errors:

```bash
possible loss of precision
found   : double
required: int

incompatible types
found   : int
required: java.lang.String

incompatible types
found   : java.lang.String
required: boolean
```

---

## 💡 Example 3 – Valid Assignment Statements

```java
int hoursWorked;
double hourlyRate, weeklySalary;
char status;
String fullName;

hoursWorked = 5 * 8 - 3;
hourlyRate = 16.75;
weeklySalary = hourlyRate * hoursWorked;
status = 'S';
fullName = "James F. Kirk";
```

### 🧾 Explanation

- `hoursWorked = 5 * 8 - 3;` → RHS evaluates to `37` → stored in `hoursWorked`
    
- Rest of the assignments match their data types.
    
- Variables are created with **specific data types**:
    
    - `int` for whole numbers
        
    - `double` for decimals
        
    - `char` for a single character
        
    - `String` for text

---

## 🔁 Updating with Existing Variable: `k = k + 1;`

```java
int k = 10;
k = k + 1; // k becomes 11
```

> 🔄 RHS evaluated first → 10 + 1 = 11 → stored in `k`

---

## 🔬 Semantics of Assignment Operator – Deep Dive

### Table: Variable States Through Execution

|Statement|i|j|k|p|q|
|---|---|---|---|---|---|
|`int i;`|0|||||
|`int j = 10;`|0|10||||
|`int k = j + 2;`|0|10|12|||
|`double p;`|0|10|12|0.0||
|`double q = 1.234;`|0|10|12|0.0|1.234|
|`i = j * i + k;`|12|10|12|0.0|1.234|
|`k = j % i;`|12|10|10|0.0|1.234|
|`p = i / (k + 2) + q;`|12|10|10|2.234|1.234|
|`k = i / (k + 2) + q;` (⚠ error)|❌|||||

---

## 🧬 Chained Assignment: `a = b = c = d;`

```java
int a, b, c, d;
a = b = c = d = 5;
```

### 🔁 Execution Order (Right-to-Left Associativity)

```java
c = d;
b = c;
a = b;
```

> ✅ All 4 variables will store the value `5`

---

## 🔗 Real-World Use Cases

- Initializing multiple config flags or counters:
    
    ```java
    int count1, count2, count3;
    count1 = count2 = count3 = 0;
    ```
    
- Game state reset:
    
    ```java
    playerHealth = playerMana = playerStamina = 100;
    ```
    
- GUI layout values:
    
    ```java
    int marginTop = marginBottom = marginLeft = marginRight = 10;
    ```
    

---

## 🧠 Advanced Example: Mixed Arithmetic Assignments

```java
public class MixedAssignments {
  public static void main(String[] args) {
    int i = 0;
    int j = 10;
    int k = j + 2;       // k = 12
    double p;
    double q = 1.234;

    i = j * i + k;       // i = 0 + 12 = 12
    k = j % i;           // k = 10 % 12 = 10
    p = i / (k + 2) + q; // 12 / (10 + 2) + 1.234 = 1 + 1.234 = 2.234

    // Error: incompatible types
    // k = i / (k + 2) + q; // double to int without cast ❌

    System.out.println("i = " + i);
    System.out.println("k = " + k);
    System.out.println("p = " + p);
  }
}
```

### ✅ Expected Output

```
i = 12
k = 10
p = 2.234
```

---

## 🧪 Real World Example: Bank Account Update

```java
public class BankUpdate {
  public static void main(String[] args) {
    double balance = 1000.50;
    double deposit = 250.75;
    double withdraw = 100.00;

    balance = balance + deposit - withdraw;
    System.out.println("Updated Balance: Rs. " + balance);
  }
}
```

### ✅ Expected Output:

```
Updated Balance: Rs. 1151.25
```

> 🏦 This mirrors real banking operations: deposits, withdrawals, balance updates.

---

## 🧠 Quiz Time!

> 1. What happens if you write `int x = 5.5;`?
>     
> 2. Why does `x = y = z = 100;` work in Java?
>     
> 3. What is the associativity of the assignment operator?
>     
> 4. What type of error occurs when assigning float to int?
>     

---

## 📚 Further Reading

- [Java Assignment Operator – Oracle Docs](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op1.html)
    
- [Java Language Specification – Assignment](https://docs.oracle.com/javase/specs/jls/se17/html/jls-15.html#jls-15.26)
    
- [GeeksForGeeks – Assignment Operators](https://www.geeksforgeeks.org/assignment-operators-in-java/)
    
- [W3Schools – Java Operators](https://www.w3schools.com/java/java_operators.asp)
    

---

## 🏁 Conclusion

The assignment operator in Java is deceptively simple but **fundamental**. Mastering it gives you power to:

- Track variable values
    
- Perform calculations
    
- Prevent data loss or precision errors
    

🛠️ Always remember:

> RHS evaluated first, then stored in LHS. Match the types carefully.

---