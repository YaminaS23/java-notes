
# Java Two-Way Selection (`if-else`)

---

## 📌 Overview

Java's two-way selection structure allows your program to choose between **two different sets of actions** based on a condition. It's used when **you want one thing to happen if a condition is true, and something else if it's false**.

> 🔥 Keyword: `if ... else`

---

## 📚 Syntax

```java
if (condition)
    statement1;
else
    statement2;
```

### 🔑 Rules:

- The condition must return a `boolean` value (either `true` or `false`).
    
- Each statement can be:
    
    - A **single statement** (no braces needed).
        
    - A **block of statements** (must be wrapped in `{ }`).
        

---

## 💡 How It Works

> **If the condition is true:** Execute `statement1`  
> **If the condition is false:** Execute `statement2`

Only one of the statements will execute. Never both.

---

## 🔥 Real-World Example (Bank Account)

Imagine a bank:

- If your balance is positive (>= 0), you get monthly interest.
    
- If it's negative, you get a penalty fee.
    

```java
if (balance >= 0)
    balance = balance + (INTEREST_RATE * balance) / 12;
else
    balance = balance - OVERDRAWN_PENALTY;
```

> ⚡️ The symbol `>=` means "greater than or equal to". Java doesn't support the mathematical ≥ symbol.

---

## 👀 Example: Full Java Program

### 🧑‍💻 Basic Bank Balance Program

```java
import java.util.Scanner;

public class BankBalance {
    public static final double OVERDRAWN_PENALTY = 8.00;
    public static final double INTEREST_RATE = 0.02; // 2% annually

    public static void main(String[] args) {
        double balance;
        System.out.print("Enter your checking account balance: $");
        Scanner keyboard = new Scanner(System.in);
        balance = keyboard.nextDouble();
        System.out.println("Original balance $" + balance);

        if (balance >= 0)
            balance = balance + (INTEREST_RATE * balance) / 12;
        else
            balance = balance - OVERDRAWN_PENALTY;

        System.out.print("After adjusting for one month ");
        System.out.println("of interest and penalties,");
        System.out.println("your new balance is $" + balance);
    }
}
```

#### **Expected Output**

```
Enter your checking account balance: $505.67
Original balance $505.67
After adjusting for one month of interest and penalties,
your new balance is $506.5127833333333
```

#### **Another Sample Output**

```
Enter your checking account balance: $-15.53
Original balance $-15.53
After adjusting for one month of interest and penalties,
your new balance is $-23.53
```

---

## 🎯 Compound Statements (Grouping Multiple Actions)

> If you want to run more than one statement inside the `if` or `else`, use curly braces `{}` to group them.

**Syntax:**

```java
if (condition) {
    // Statement 1
    // Statement 2
}
else {
    // Statement 3
    // Statement 4
}
```

### 👾 Example with Compound Statements

```java
if (balance >= 0) {
    System.out.println("Good for you. You earned interest.");
    balance = balance + (INTEREST_RATE * balance) / 12;
}
else {
    System.out.println("You will be charged a penalty.");
    balance = balance - OVERDRAWN_PENALTY;
}
```


---

## ✅ Example 1: Age Difference — Same Generation

### 🎯 Goal: Determine if two people are from the same generation (age difference ≤ 20).

```java
import java.util.Scanner;

public class TwowayAge {
    public static void main(String[] args) {
        String firstNameOne, lastNameOne;
        String firstNameTwo, lastNameTwo;
        int ageOne, ageTwo, ageDifference;

        Scanner scannedInfo = new Scanner(System.in);

        System.out.print("Enter first name, last name and age : ");
        firstNameOne = scannedInfo.next();
        lastNameOne = scannedInfo.next();
        ageOne = scannedInfo.nextInt();

        System.out.print("Enter first name, last name and age : ");
        firstNameTwo = scannedInfo.next();
        lastNameTwo = scannedInfo.next();
        ageTwo = scannedInfo.nextInt();

        ageDifference = Math.abs(ageTwo - ageOne);

        System.out.print(firstNameOne + " " + lastNameOne + " and " +
                         firstNameTwo + " " + lastNameTwo + " ");
        
        if (ageDifference <= 20)
            System.out.println("are of the same generation.");
        else
            System.out.println("are of different generations.");
    }
}
```

### 🖥️ Input:

```
Enter first name, last name and age : Joy Mathew 37 
Enter first name, last name and age : Chris Cox 57
```

### 🖥️ Expected Output:

```
Enter first name, last name and age : Joy Mathew 37
Enter first name, last name and age : Chris Cox 57
Joy Mathew and Chris Cox are of the same generation.
```


### 1️⃣ **Prompt for First Person's Details**

```java
System.out.print("Enter first name, last name and age : ");
firstNameOne = scannedInfo.next();
lastNameOne = scannedInfo.next();
ageOne = scannedInfo.nextInt();
```

> **Note:**
> 
 - `.next()` reads the next word (so input must be in order: name, surname, age).
>     
 - `.nextInt()` reads the integer for age.
>     


### 2️⃣  **Prompt for Second Person's Details**

```java
System.out.print("Enter first name, last name and age : ");
firstNameTwo = scannedInfo.next();
lastNameTwo = scannedInfo.next();
ageTwo = scannedInfo.nextInt();
```

> **Note:**
> 
 - Same process as above for the second person.
>     


### 3️⃣ **Calculate Age Difference**

```java
ageDifference = Math.abs(ageTwo - ageOne);
```

> **Note:**
> 
 - `Math.abs()` gives the absolute value (always positive).
>     
 - This prevents negative results if, say, person 1 is older.
>     


### 4️⃣ **Print Both Names Together**

```java
System.out.print(firstNameOne + " " + lastNameOne + " and " +
                 firstNameTwo + " " + lastNameTwo + " ");
```

> **Note:**
> 
 - Concatenates the names for the output message.
>     


### 5️⃣ **Check Generation and Print Result**

```java
if (ageDifference <= 20)
    System.out.println("are of the same generation.");
else
    System.out.println("are of different generations.");
```

> **Note:**
> 
 - If age difference is less than or equal to 20, they're considered the same generation (totally arbitrary but fun rule).
>     
 - Otherwise, they're from different generations.
>     
 - The `if-else` logic prints the appropriate message.
>

---

## ✅ Example 2: Lexicographical Name Comparison

### 🎯 Goal: Check if the last name comes after the first name alphabetically.

#### 🧠 **Concept Used:**

```java
firstName.compareTo(lastName) < 0
```

This checks if `firstName` comes **before** `lastName` alphabetically.

```java
import java.util.Scanner;

public class AscendingName {
    public static void main(String[] args) {
        String firstName, lastName;
        Scanner scannedInfo = new Scanner(System.in);

        System.out.print("Enter first name, last name: ");
        firstName = scannedInfo.next();
        lastName = scannedInfo.next();

        if (firstName.compareTo(lastName) < 0) {
            System.out.println("Hi " + firstName + " " + lastName);
            System.out.println("You got an ascending Name!");
        } else {
            System.out.println("Sorry! " + firstName + " " + lastName);
            System.out.println("Your name is not an ascending one!");
        }
    }
}
```

### 🖥️ Input:

```
Enter first name, last name: James Jones
```

### 🖥️ Expected Output:

```
Enter first name, last name: James Jones
Hi James Jones
You got an ascending Name!
```

### 📌 **Quick Breakdown:**

- `.compareTo()` is a **string method** that returns:
    
    - `< 0` if firstName < lastName
        
    - $==$ `0` if firstName == lastName
        
    - `> 0` if firstName > lastName
        
- So this program is checking:
    

> _"Does your last name come later than your first name alphabetically?"_


---

## 🤖 Example 3: Yes/No Oracle (Random)

```java
import java.util.Scanner;
import java.util.Random;

public class AnswerYesOrNo {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in); // Create Scanner object
        Random myRandom = new Random(); // Create Random object

        System.out.print("Type your question, my child: ");
        keyboard.nextLine(); // Input swallowed. Read user input (question)

        int randomNumber = myRandom.nextInt(10) + 1; // Range: 1–10

        if (randomNumber > 5) {
            System.out.println("Yes. Isn't it obvious?");
        } else {
            System.out.println("No, and don't ask again.");
        }

        keyboard.close(); // Close the Scanner
    }
}
```

### 🖥️ Input:

```
Type your question, my child: Will I be rich?
```

### 🖥️ Expected Output:

```
Type your question, my child: Will I be rich?
Yes. Isn't it obvious?
```

**or**

### 🖥️ Input:

```
Type your question, my child: Will I pass the exam?
```

### 🖥️ Expected Output:

```
Type your question, my child: Will I pass the exam?
No, and don't ask again.
```


### ### `Random myRandom = new Random();`

- Initializes a random number generator.
    
- `nextInt(n)` returns an integer from `0` to `n-1`.
    
- So `nextInt(10) + 1` produces numbers from **1 to 10**.
    

### ### `if (randomNumber > 5)`

- Basic conditional check.
    
- If the number is **greater than 5**, it prints a **positive message**.
    
- Otherwise, it prints a **negative message**.


---

## ❗ Common Errors with `if-else`

| Mistake                                                  | Example                                | Result                     |
| -------------------------------------------------------- | -------------------------------------- | -------------------------- |
| Missing `()`                                             | `if randomNumber > 5`                  | Syntax error: `(` expected |
| Extra `;` after `if`                                     | `if (x > y); {}`                       | The block always runs      |
| Forgetting `{}` for multiple statements                  | Only the first statement runs in block |                            |
| Using `(____ == true)` instead of directly using boolean | `if (flag == true)`                    | Just use `if (flag)`       |

> ✅ Always use braces `{}` even for one-line blocks to prevent logic errors.

---

## 🧪 Self-Check Exercises

### 1. Net Worth Check

```java
import java.util.Scanner;

public class NetWorthEvaluator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Prompt for net worth input
        System.out.print("Enter your net worth in dollars: $");
        double netWorth = scanner.nextDouble();
        
        // Evaluate financial status
        if (netWorth > 10000000) {
            System.out.println("Set for life!");
        } else {
            System.out.println("Not there yet!");
        }
        
        scanner.close();
    }
}
```

### 🖥️ Expected Output:

#### 🎯 **Input 1:** 

```
Enter your net worth in dollars: $12000000
```

#### 🎯 **Output:** 

```
Enter your net worth in dollars: $12000000
Set for life!
```

#### 🎯 **Input 2:** 

```
Enter your net worth in dollars: $5000000
```

#### 🎯 **Output:** 

```
Enter your net worth in dollars: $5000000
Not there yet!
```

---

### 2. Cost Evaluation

```java
if (cost > 25.00)
    System.out.println("Expensive item");
else
    System.out.println("Reasonable Item");
```

### 3. Uppercase Letter Check

```java
isUppercaseLetter = ('A' <= charOne && charOne <= 'Z');
```

### 4. Can this work?

```java
('a' <= charOne <= 'z') ❌ Invalid in Java
```

> ❌ Java doesn't support chained relational comparisons like Python. Must split into two:

```java
('a' <= charOne && charOne <= 'z') ✅ Valid
```

---

## 📎 Boolean Notes Recap

- Boolean is a primitive data type: `boolean isDone = true;`
    
- Use logical expressions directly:
    

```java
isLowercaseLetter = ('a' <= charOne && charOne <= 'z');
```

- `if (flag == true)` is equivalent to `if (flag)` ✅
    
- `if (flag == false)` is equivalent to `if (!flag)` ✅
    
---

## 🧠 Real-World Use Cases

- Eligibility check for loans or scholarships
    
- Logging users in based on correct password
    
- UI reactions (e.g., dark mode if night, else light)
    
- Discount calculation for eCommerce apps
    

> 🎯 `if-else` is the heart of decision-making logic in every real-world app 💥

---

## 🔧 Logical Operators in Java

### ### Table: Logical Operators Cheat Sheet

| Operator | Symbol | Meaning                                    | Example                  | Result                                                 |
| -------- | ------ | ------------------------------------------ | ------------------------ | ------------------------------------------------------ |
| AND      | `&&`   | True if **both** conditions are true       | `age > 4 && age < 8`     | True if age is 5, 6, or 7                              |
| OR       | $\|\|$ | True if **at least one** condition is true | `age < 4` \|\| `age > 8` | True if age is either less than 4 `OR` greater than 8. |
| NOT      | `!`    | Inverts the boolean value                  | `!isLoggedIn`            | True if `isLoggedIn` is false                          |

### ✅ Examples

```java
int age = 6;
System.out.println(age > 4 && age < 8); // true
System.out.println(age < 4 || age > 8); // false
```

> 💡 **Note**: `||` is **inclusive OR**—so either side or both can be true.

---

## 🤓 Syntax & Usage

### AND: `&&`

- **Both** sub-expressions must be true for the whole thing to be true.
    
- Used for combining checks (range, multiple conditions, etc).
    

#### 🧑‍💻 Example:

```java
if ((pressure > min) && (pressure < max)) {
    System.out.println("Pressure is OK.");
} else {
    System.out.println("Warning: Pressure is out of range.");
}
```

**Expected Output:**

> Pressure is OK. _(if within range)_ Warning: Pressure is out of range. _(otherwise)_

> 🚩 **You can't write:** `min < pressure < max`. This is NOT valid in Java! You must use: `(pressure > min) && (pressure < max)`

---

### OR: `||`

- At least **one** sub-expression must be true.
    
- Used when you want to allow for multiple possibilities.
    

#### 🧑‍💻 Example:

```java
if ((salary > expenses) || (savings > expenses)) {
    System.out.println("Solvent");
} else {
    System.out.println("Bankrupt");
}
```

**Expected Output:**

> Solvent _(if either salary OR savings beats expenses)_ Bankrupt _(otherwise)_

---

### NOT: `!`

- Negates a boolean value.
    
- Use to invert conditions, but avoid if possible for clarity.
    

#### 🧑‍💻 Example:

```java
if (!(number >= min)) {
    System.out.println("Too small");
} else {
    System.out.println("OK");
}
```

**Expected Output:**

> Too small _(if number < min)_ OK _(otherwise)_

#### 🛑 Better Style:

```java
if (number < min) {
    System.out.println("Too small");
} else {
    System.out.println("OK");
}
```

> 🏆 **Tip:** Avoid `!` if you can rewrite the condition for more readability!

---

## 🧨 Gotchas, Traps & Pro Tips

### 1. **Assignment vs. Equality**

- $=$ is the assignment operator. _Never_ use it to test equality!
    
- Use $==$ to compare values.
    

#### ❌ Wrong:

```java
if (x = y) // Syntax error! Assigns y to x, not compare
```

#### ✅ Right:

```java
if (x == y)
```

> 🚨 **Common bug for beginners!**

### 2. **Comparing Floating-Point Values**

- $==$ or `!=` are _dangerous_ for `float` and `double` because of rounding/precision errors.
    
- Instead, test if their difference is within a small range (epsilon):
    

#### 🧑‍💻 Example:

```java
double a = 0.1 * 7;
double b = 0.7;

if (Math.abs(a - b) < 1e-9) {
    System.out.println("a and b are close enough to be equal");
} else {
    System.out.println("a and b are NOT equal");
}
```

**Expected Output:**

> a and b are close enough to be equal

> 📌 For doubles/floats: Use **approximate equality** instead of ==

### 3. **Parentheses and Readability**

- Java doesn't _require_ parentheses around simple boolean expressions inside if/else, but **using them is best practice** for clarity, especially with complex conditions.
    
- Always wrap the whole condition in parentheses in `if`, `while`, etc.
    

#### 🧑‍💻 Example:

```java
if ((a > b) && (c < d))
```

---

## 🏢 Real-World Use Cases

### 1. **Range Checking**

```java
if ((temperature >= 20) && (temperature <= 30)) {
    System.out.println("Ideal temperature range!");
}
```

### 2. **Eligibility Check**

```java
if ((age >= 18) && ((citizen == true) || (hasPermanentResidency == true))) {
    System.out.println("Eligible to vote!");
}
```

### 3. **Login Validation**

```java
if ((username.equals("admin")) && (password.equals("1234"))) {
    System.out.println("Access Granted");
}
```

---

## 🧠 Key Concepts

### 🔄 Combining Conditions (AND, OR, NOT)

- Use `&&` to make **both conditions** required.
    
- Use `||` to make **either condition** sufficient.
    
- Use `!` to **negate a condition**.
    

### ❌ Common Mistake

```java
if (3 <= people <= 10) // ❌ Invalid in Java
```

🔧 Fix:

```java
if (3 <= people && people <= 10) // ✅ Correct
```

> ✅ Use `&&` instead of trying chained comparisons like in math or English.

---

## 🎲 Dice Roll Use Case

```java
import java.util.Random;

public class DiceRoll {
    public static void main(String[] args) {
        Random rand = new Random();
        int die1 = rand.nextInt(6) + 1;
        int die2 = rand.nextInt(6) + 1;

        System.out.println("Die 1: " + die1);
        System.out.println("Die 2: " + die2);

        if (die1 + die2 == 8 && die1 == die2) {
            System.out.println("You rolled doubles summing to 8! 🎉");
        } else if (die1 + die2 == 8) {
            System.out.println("Total is 8, but not doubles.");
        } else {
            System.out.println("You rolled something else.");
        }
    }
}
```

### 🧾 Expected Output (Example)

```
Die 1: 4
Die 2: 4
You rolled doubles summing to 8! 🎉
```

### 🎲 `rand.nextInt(6) + 1`

- Random number between 1 and 6
    
- Simulates a 6-sided die
    

### 🤖 Conditions

- ✅ If **sum = 8** AND **both dice are equal** ➝ 🎉 Special message
    
- ✅ If **sum = 8** but **not doubles** ➝ Simple 8 message
    
- ❌ Else ➝ Generic message

---

## 🎟️ Movie Ticket Price Example

```java
import java.util.Scanner;

public class TicketPrice {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        int age;
        double price = 0.00;

        System.out.print("How old are you? ");
        age = keyboard.nextInt();

        if (age >= 12 && age < 65) {
            price = 9.25; // Regular price
        }
        if (age < 12 || age >= 65) {
            price = 5.25; // Kids or Seniors
        }

        System.out.print("Please pay $");
        System.out.print(price);
        System.out.print(". ");
        System.out.println("Enjoy the show!");
        keyboard.close();
    }
}
```

### 🧾 Input

```
How old are you? 66
```

### 🧾 Expected Output

```
How old are you? 66
Please pay $5.25. Enjoy the show!
```

---

## 🧠 Why Initialize `price = 0.00`?

Java requires all **local variables** to be explicitly initialized **before use**. Even though we _know_ one of the `if` statements will run, the compiler doesn’t.

### 🛑 Without initialization

```java
// Compiler error: Variable 'price' might not have been initialized
System.out.print(price);
```

### ✅ Best practice:

```java
double price = 0.00; // Ensures default value
```

> 🧠 Unlike `age = input.nextInt()` (which is outside the if statements and always runs), both `price =` assignments are inside ifs, so the compiler isn’t 100% sure they will run.

---

## 📎 Real-World Examples

### 🧒👵 Age-Based Pricing

- Amusement parks
    
- Theme parks (Disney)
    
- Movie theaters
    

### 🎯 Multi-Condition Decisions

- Game logic (e.g., critical hits = random roll + level + bonus)
    
- Access control (e.g., loggedIn && isAdmin)
    
- Data validation (e.g., password length && includes number)
    

---

## 🧠 Challenge Time!

> ❓ What’s the output of this code?

```java
int age = 10;
if (age > 8 && age < 12 || age == 65) {
    System.out.println("Special case!");
}
```

Answer: `Special case!` — Because `10 > 8 && 10 < 12` is true, so entire OR is true.

---

## ✅ Summary

- Use `&&`, `||`, `!` to form compound conditions.
    
- Use parentheses `()` to clarify logic.
    
- Always initialize local variables before use.
    
- Avoid chaining comparisons directly.
    
- Think like a compiler! 🧠
    

---

> 🎓 Now that you’ve mastered compound conditions, you’re one step closer to writing smarter, more dynamic Java programs!

Next lesson? `switch` statements and nested conditionals 🔥


---

## 📘 Further Reading

- [Oracle Java Docs - if Statement](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/if.html)
    
- [Java Random Class API](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Random.html)
    
- [W3Schools - Java Conditions](https://www.w3schools.com/java/java_conditions.asp)
    
- [GeeksforGeeks - if-else](https://www.geeksforgeeks.org/java-if-else-statement/)
    
-  [Oracle Java Operators Doc](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/op2.html)
    
- [Logical Operators in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/logical-operators-java/)
    
- [Boolean Expressions (W3Schools)](https://www.w3schools.com/java/java_conditions.asp)

---

Next up? Let’s level up with `else-if ladders` and `nested ifs`. 🧗‍♂️
