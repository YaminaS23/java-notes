
# Java: Nested Structures and Multiway Selection 

---

## 🔎 Overview

Java's **nested structures** allow developers to write more precise and compact decision-making logic by placing one `if` or `if-else` block inside another. This chapter explores nested `if` statements, multiway selection (the `if-else-if` ladder), logical expression ordering, and common pitfalls, all with code examples and real-world scenarios.

---

## 📘 What are Nested Control Structures?

### 🧱 Definition

> A **nested control structure** is a control structure placed inside another control structure.

In Java, you can nest:

- `if` statements inside other `if` statements
    
- `if-else` inside `if`
    
- Multiple levels deep nesting

### 🧠 Example Use Case

James throws a party. If it's a weekday, follow the regular schedule. If not, check if there's a party:

```java
if (weekday)
    // follow weekday schedule
else
    if (throwingParty)
        // follow party schedule
    else
        // follow regular weekend schedule
```

> 🔍 Nesting helps express **hierarchical logic** cleanly but must be used with caution to avoid confusion.

> Placing one control structure (e.g., `if`, `if-else`) **inside another** is called **nesting**.

### Syntax:

```java
if (condition1) {
    if (condition2) {
        // Action
    } else {
        // This else is for inner if (condition2)
    }
} else {
    // This else is for outer if (condition1)
}
```

### Real-World Analogy:

- If it's a **weekday**, follow the **weekday schedule**.
    
- Else, if **throwing a party**, follow the **party schedule**.
    
- Else, follow the **regular weekend** routine.
    

---

## 🔬 Example: Banking Interest Calculation

#### 💡 Theory

- If your balance is positive, check if the interest rate is positive. If yes, add monthly interest.
    
- If not, print an error.
    
- If your balance is negative, apply an overdraft penalty.
    

#### 🧾 Code Example (with & without braces)

##### **Version 1 – With Braces (Clear, Recommended):**

```java
if (balance >= 0) {
    if (INTEREST_RATE >= 0)
        balance = balance + (INTEREST_RATE * balance) / 12;
    else
        System.out.println("Cannot have a negative interest.");
} else {
    balance = balance - OVERDRAWN_PENALTY;
}
```

**Expected Output:**

> Calculates and updates `balance` if positive and interest rate is valid, else prints an error. If negative, applies penalty.

##### **Version 2 – No Braces (Confusing, NOT recommended):**

```java
if (balance >= 0)
    if (INTEREST_RATE >= 0)
        balance = balance + (INTEREST_RATE * balance)/12;
else
    balance = balance - OVERDRAWN_PENALTY;
```

**Expected Output:**

> Logic changes! Here, `else` pairs with the _nearest_ `if`, not always as you might expect by indentation!

#### ⚠️ Braces Matter!

> If in doubt, ALWAYS use braces `{}` to clarify scope!

---

## 🎯 Syntax Refresher

```java
if (logicalExpression)
    actionStatement;

if (logicalExpression)
    actionStatement;
else
    actionStatement;
```

The `actionStatement` can be another full `if` or `if-else` structure!

---

## 🪜 `if-else-if` Ladder

## ✅ Definition

> An `if-else-if` ladder is used when you need to select one out of **many possible conditions**.

### 📌 Syntax

```java
if (condition1) {
    // Statement1
} else if (condition2) {
    // Statement2
} else if (condition3) {
    // Statement3
} else {
    // Default Statement
}
```

---

## 🧑‍💻 Example: Bank Account Status

#### **Classic Nested Form (Messy):**

```java
if (balance > 0)
    System.out.println("Positive balance");
else
    if (balance < 0)
        System.out.println("Negative balance");
    else
        if (balance == 0)
            System.out.println("Zero balance");
```

**Expected Output:**

> Depending on `balance`, prints whether it’s positive, negative, or zero.

#### **Modern Multi-branch (Clear, Preferred):**

```java
if (balance > 0) {
    System.out.println("Positive balance");
} else if (balance < 0) {
    System.out.println("Negative balance");
} else {
    System.out.println("Zero balance");
}
```

**Expected Output:**

> Prints one of three: Positive balance, Negative balance, or Zero balance.

---

## 🧪 Code Example: Nested `if`

```java
public class NestedIfDemo {
    public static void main(String[] args) {
        int i = 10, j = 15, k = 200;
        int a = 0, b = 1, c = 2, d = 3;

        if(i == 10) {
            if(j < 20) a = b;
            if(k > 100) c = d;  // 🟢 Paired with the next else
            else a = c;         // 🟢 This else matches with if(k > 100)
        }
        else a = d;             // 🔵 Matches outer if(i == 10)

        System.out.println("a: " + a + ", c: " + c);
    }
}
```

### ✅ Expected Output

```
a: 1, c: 3
```

## 🧩 Step-by-Step Execution

### 1️⃣ **Variable Initialization**

- `i = 10`
    
- `j = 15`
    
- `k = 200`
    
- `a = 0`, `b = 1`, `c = 2`, `d = 3`
    

> **All variables are set before any logic runs!**

---

### 2️⃣ **First** `if(i == 10)`

- Condition: `i == 10` → `10 == 10` → `true`
    
- **Enters the first if block!**
    

---

### 3️⃣ **Second** `if(j < 20)`

- Condition: `j < 20` → `15 < 20` → `true`
    
- Runs `a = b;` → `a` now equals `1`.
    

---

### 4️⃣ **Third** `if(k > 100)` **with** `else`

- Condition: `k > 100` → `200 > 100` → `true`
    
- Runs `c = d;` → `c` now equals `3`.
    
- The `else` part is SKIPPED because the `if` was true.
    

> ⚠️ **Java Rule:** The `else` matches with the closest previous unmatched `if` within the same block. Here, `else a = c;` matches with `if(k > 100)`, NOT `if(j < 20)`.

---

### 5️⃣ **The Outer** `else`

- Not run! Because the first `if(i == 10)` was true, so `else a = d;` is IGNORED.
    

---

### 6️⃣ **Print Statement**

- Prints current `a` and `c` values:
    
    - `a: 1`
        
    - `c: 3`
        

```
a: 1, c: 3
```

---

## 📚 Examples of Nested Structures

## 💰 Example 1: Income Tax Calculation

**Rules:**

- Income ≤ $25,000 → No tax
    
- $25,000 < Income ≤ $100,000 → 15% tax on excess
    
- Income > $100,000 → $11,250 (15% on 75,000) + 25% on excess
    
| Income Range       | Tax Rate                         |
| ------------------ | -------------------------------- |
| Up to $25,000      | No tax                           |
| $25,001 - $100,000 | 15% on excess                    |
| Above $100,000     | 15% on 75,000 + 25% on remainder |

### ✅ Nested Version

```java
if (totalIncome > 25000.00) {
    if (totalIncome > 100000.00) {
        incomeTax = 11250.00 + (totalIncome - 100000.00) * 0.25;
    } else {
        incomeTax = (totalIncome - 25000.00) * 0.15;
    }
} else {
    incomeTax = 0.0;
}
```

```java
public class Main {
    public static void main(String[] args) {
        double totalIncome = 120000.00; // Given income value
        double incomeTax;
        
        if (totalIncome > 25000.00) {
            if (totalIncome > 100000.00) {
                incomeTax = 11250.00 + (totalIncome - 100000.00) * 0.25;
            } else {
                incomeTax = (totalIncome - 25000.00) * 0.15;
            }
        } else {
            incomeTax = 0.0;
        }
        
        System.out.println("Income Tax for $" + totalIncome + " is $" + incomeTax);
    }
}
```
### 🧾 Expected Output

```
Income Tax for $120000.0 is $16250.0
```


### 🛑 Why Avoid Multiple Independent `if` Statements

```java
if (totalIncome <= 25000.00)
    incomeTax = 0.0;
if (totalIncome > 25000.00 && totalIncome <= 100000.00)
    incomeTax = (totalIncome - 25000.00) * 0.15;
if (totalIncome > 100000.00)
    incomeTax = 11250.00 + (totalIncome - 100000.00) * 0.25;
```

> 🚫 Less efficient. All conditions are checked even if the first one is true.

### ✅ Multiway Selection Version (Better)

```java
if (totalIncome > 100000.00) {
    incomeTax = 11250.00 + (totalIncome - 100000.00) * 0.25;
} else if (totalIncome > 25000.00) {
    incomeTax = (totalIncome - 25000.00) * 0.15;
} else {
    incomeTax = 0.0;
}
```

### ⚙️ Why Multiway is Better

- **More readable**
    
- **Efficient** (fewer condition checks)
    

> Avoid writing multiple standalone `if` statements unless conditions are truly independent.

---

## 🎓 Example 2: Grade Assignment

### Grading Table:

|Weighted Average (wats)|Grade Assigned|
|---|---|
|wats ≥ 90|A|
|85 ≤ wats < 90|A-|
|80 ≤ wats < 85|B|
|75 ≤ wats < 80|B-|
|70 ≤ wats < 75|C|
|60 ≤ wats < 70|D|
|wats < 60|F|

### ✅ Clean if-else-if Ladder

```java
if (wats >= 90)
    grade = "A";
else if (wats >= 85)
    grade = "A-";
else if (wats >= 80)
    grade = "B";
else if (wats >= 75)
    grade = "B-";
else if (wats >= 70)
    grade = "C";
else if (wats >= 60)
    grade = "D";
else
    grade = "F";
```

### ⚠️ Incorrect Order

```java
if (wats >= 70)
    grade = "C";
else if (wats >= 85)
    grade = "A-"; // Never executed!
```

> ❗ Always write the **highest condition first** to avoid logic errors.

---

## 🔥 The Scenario

> Given a score, assign a traditional letter grade: A (90+), B (80–89), C (70–79), D (60–69), F (below 60).

### 📚 Code Example: Grader Program

```java
import java.util.Scanner;

public class Grader {
    public static void main(String[] args) {
        int score;
        char grade;
        System.out.println("Enter your score: ");
        Scanner keyboard = new Scanner(System.in);
        score = keyboard.nextInt();

        if (score >= 90)
            grade = 'A';
        else if (score >= 80)
            grade = 'B';
        else if (score >= 70)
            grade = 'C';
        else if (score >= 60)
            grade = 'D';
        else
            grade = 'F';

        System.out.println("Score = " + score);
        System.out.println("Grade = " + grade);
    }
}
```

#### **Expected Output:**

```
Enter your score:
85
Score = 85
Grade = B
```

---

### 🧠 Theory & Notes

- > Multibranch `if-else` evaluates conditions in order.
    
- Once a true condition is found, the rest are skipped (like a domino effect).
    
- You could use explicit ranges for clarity:
    

```java
if (score >= 90)
    grade = 'A';
else if ((score >= 80) && (score < 90))
    grade = 'B';
else if ((score >= 70) && (score < 80))
    grade = 'C';
else if ((score >= 60) && (score < 70))
    grade = 'D';
else
    grade = 'F';
```

- > Most programmers prefer the short form; it’s more efficient and easier to read.
    
- Both versions are equivalent, but the first is considered more elegant.
    

### ⚡ Real-World Use Case

> Used in educational software, competitive programming, and anywhere grading logic is needed.

---

## 🧠 Pairing Rules for `else`

### 🔀 Which `if` does an `else` belong to?

> An `else` is always paired with the **closest previous `if` that doesn't already have an `else`**.

## 🚗 Example 3: Risk Factor for Insurance

### 🧾 Rule Summary

| Condition                                | Risk Factor |
| ---------------------------------------- | ----------- |
| Age 16–25                                | 5.0         |
| Not high-risk but has high-risk children | 3.0         |
| Default                                  | 1.0         |

```java
int driverAge;
double riskFactor;
boolean hasHighRiskChildren;
riskFactor = 1.0;

if (driverAge >= 26) {
    if (hasHighRiskChildren)
        riskFactor = 3.0;
} else {
    riskFactor = 5.0;
}
```

> 🧩 Else must match the correct `if`. Use `{}` to ensure this!

### ❌ Wrong:

```java
if (driverAge >= 26)
    if (hasHighRiskChildren)
        riskFactor = 3.0;
else
    riskFactor = 5.0; // Gets incorrectly paired with inner if
```

### ✅ Correct (Use braces):

```java
if (driverAge >= 26) {
    if (hasHighRiskChildren)
        riskFactor = 3.0;
} else {
    riskFactor = 5.0;
}
```

> Always use braces `{}` in nested ifs to **avoid mispairing**.

### ✅ Even Better Multiway Version

```java
if (driverAge <= 25)
    riskFactor = 5.0;
else if (hasHighRiskChildren)
    riskFactor = 3.0;
else
    riskFactor = 1.0;
```

---

## 🛠 Reducing Redundancy with Nesting

Let’s say your code does the same check multiple times. That’s a **maintenance hazard**. Instead, nest it once and save time.

### ❌ Wasteful Code

```java
if (age >= 12 && age < 65) {
    price = 9.25;
}

if ((reply == 'Y' || reply == 'y') && (age >= 12 && age < 65)) {
    price -= 2.00;
}
```

### ✅ Better with Nesting

```java
if (age >= 12 && age < 65) {
    price = 9.25;
    if (reply == 'Y' || reply == 'y') {
        price -= 2.00;
    }
} else {
    price = 5.25;
}
```

> 🔥 **This makes the logic centralized and DRY (Don't Repeat Yourself)**

---

## 💡 Real World Example: Movie Ticket Pricing

```java
import java.util.Scanner;

public class AnotherAgeCheck {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int age;
        char reply;
        double price;

        System.out.print("Enter your age: ");
        age = scanner.nextInt();
        System.out.print("Have a coupon? (Y/N): ");
        reply = scanner.findWithinHorizon(".", 0).charAt(0);

        if (age >= 12 && age < 65) {
            price = 9.25;
            if (reply == 'Y' || reply == 'y') {
                price -= 2.00;
            }
        } else {
            price = 5.25;
        }

        System.out.println("Please pay $" + price + ". Enjoy the show!");
        scanner.close();
    }
}
```

### 🖨️ **Expected Output (if age=20, reply=Y)**

```
Enter your age: 20
Have a coupon? (Y/N): Y
Please pay $7.25. Enjoy the show!
```

### 🧓 Step 1: Get User Input

```java
System.out.print("Enter your age: ");
age = scanner.nextInt();
System.out.print("Have a coupon? (Y/N): ");
reply = scanner.findWithinHorizon(".", 0).charAt(0);
```

- Asks for age and coupon.
    
- `findWithinHorizon` is used to get **one character** as input.
    
### 🧮 Step 2: Calculate Price

```java
if (age >= 12 && age < 65) {
    price = 9.25;
    if (reply == 'Y' || reply == 'y') {
        price -= 2.00;
    }
} else {
    price = 5.25;
}
```

- Normal ticket = $9.25
    
- Seniors (<12 or ≥65) = $5.25
    
- If you have a coupon: **get $2 off!**


## 🧠 Deeper Nesting

Yes, you can nest infinitely (though **not recommended**).

### Example:

```java
if (age >= 12 && age < 65) {
    price = 9.25;
    if (reply == 'Y' || reply == 'y') {
        if (isSpecialFeature) {
            price -= 1.00;
        } else {
            price -= 2.00;
        }
    }
} else {
    price = 5.25;
}
```

---

## 🧪 Code Example: Season Checker

```java
public class IfElseSeason {
    public static void main(String[] args) {
        int month = 4; // April
        String season;

        if(month == 12 || month == 1 || month == 2)
            season = "Winter";
        else if(month == 3 || month == 4 || month == 5)
            season = "Spring";
        else if(month == 6 || month == 7 || month == 8)
            season = "Summer";
        else if(month == 9 || month == 10 || month == 11)
            season = "Autumn";
        else
            season = "Bogus Month";

        System.out.println("April is in the " + season + ".");
    }
}
```

### ✅ Expected Output

```
April is in the Spring.
```

#### 🎯 **Step 1: Declare Variables**

```java
int month = 4;
String season;
```

- `month = 4` represents **April**.
    
- `season` will store the result, like "Spring" or "Summer".
    

#### 🧠 **Step 2: Check the Season**

```java
if(month == 12 || month == 1 || month == 2)
    season = "Winter";
```

- If `month` is December, January, or February, it's **Winter**.
    
- April is NOT in this group.
    

#### 🌸 **Step 3: Is it Spring?**

```java
else if(month == 3 || month == 4 || month == 5)
    season = "Spring";
```

- Since `month` is 4 (April), this condition is **true**.
    
- So, `season = "Spring"` ✅
    

#### ☀️ **Step 4: Summer Check (Skipped)**

```java
else if(month == 6 || month == 7 || month == 8)
    season = "Summer";
```

- Skipped because April is already matched in Spring.
    

#### 🍂 **Step 5: Autumn Check (Also Skipped)**

```java
else if(month == 9 || month == 10 || month == 11)
    season = "Autumn";
```

- Not executed.
    

#### 🚨 **Step 6: Invalid Month Catcher**

```java
else
    season = "Bogus Month";
```

- Used if `month` is not in 1-12.
    
- Not executed since 4 is valid.
    

---

## 🏥 Case Study: Body Mass Index (BMI) Calculator

### 📖 What is BMI?

- **Body Mass Index (BMI)**: Estimates health risk based on weight & height.
    
- Invented by Adolphe Quetelet (1800s).
    
- Formula: `BMI = mass / (height^2)` (mass in kg, height in meters).
    

### 📊 Health Risk Categories Table

|BMI Value|Risk Category|
|---|---|
|< 18.5|Underweight|
|18.5 ≤ BMI < 25|Normal weight|
|25 ≤ BMI < 30|Overweight|
|≥ 30|Obese|

### 🛠️ Algorithm Steps

1. Read weight in pounds (`pounds`).
    
2. Read height in feet (`feet`).
    
3. Read extra inches (`inches`).
    
4. Convert height to meters: `((feet * 12) + inches) * 0.0254`.
    
5. Convert pounds to kg: `pounds / 2.2`.
    
6. Calculate BMI: `mass / (heightMeters * heightMeters)`.
    
7. Output BMI & category.
    

> For branching, you only need to check the lower bound for each category after the first.

### 🧑‍💻 Code Example: BMI Calculator

```java
import java.util.Scanner;

public class BMI {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        int pounds, feet, inches;
        double heightMeters, mass, BMI;
        System.out.println("Enter your weight in pounds.");
        pounds = keyboard.nextInt();
        System.out.println("Enter your height in feet followed by a space then additional inches.");
        feet = keyboard.nextInt();
        inches = keyboard.nextInt();
        heightMeters = ((feet * 12) + inches) * 0.0254;
        mass = (pounds / 2.2);
        BMI = mass / (heightMeters * heightMeters);
        System.out.println("Your BMI is " + BMI);
        System.out.print("Your risk category is ");
        
        if (BMI < 18.5)
            System.out.println("Underweight.");
        else if (BMI < 25)
            System.out.println("Normal weight.");
        else if (BMI < 30)
            System.out.println("Overweight.");
        else
            System.out.println("Obese.");
    }
}
```

#### **Expected Output:**

```
Enter your weight in pounds.
150
Enter your height in feet followed by a space then additional inches.
5 5
Your BMI is 25.013498117367398
Your risk category is Overweight.
```

---

### 🚀 Further Theory

- > This code uses _multibranch if-else_, which is more readable and practical than deeply nested ifs.
    
- Inputs are read as integers for pounds/feet/inches, then converted for BMI calculation.
    
- Real-world BMI calculators often include data validation (not covered here).
    

---

## 🛠️ Tips for Writing Nested ifs

- ✅ Use **braces** always
    
- ✅ Maintain **consistent indentation**
    
- ✅ Keep conditions **ordered properly** (from high to low or vice versa)
    
- ✅ Consider replacing with `else-if` ladder for better clarity
    

---

## 📌 Summary Table

|Concept|Description|
|---|---|
|Nested Structure|if/else inside another if/else|
|Pairing Rule|`else` pairs with nearest unmatched `if`|
|Multiway Selection|`if-else-if` ladder|
|Common Pitfall|Misaligned else or incorrect order of conditions|
|Best Practice|Use braces + structured ordering|

---

## 🔗 Further Reading & Practice

- [Oracle Java Docs – Control Flow](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/if.html)
    
- [GeeksForGeeks – Nested if](https://www.geeksforgeeks.org/java-if-else-statement-with-examples/)
    
- [W3Schools Java Conditions](https://www.w3schools.com/java/java_conditions.asp)
    

---

## 🤖 Challenge Time!

### 🧩 Quiz Time

> What will be the output of this code?

```java
int age = 30;
boolean hasCoupon = true;
double price;

if (age >= 12 && age < 65) {
    price = 9.25;
    if (hasCoupon) {
        price -= 2.00;
    }
} else {
    price = 5.25;
}
System.out.println(price);
```

Drop your answer 👇 and I'll tell you if you're a **Certified Nested-if Ninja** 🥷


> What will this print?

```java
int x = 10, y = 20;
if (x > 5)
    if (y < 15)
        System.out.println("A");
    else
        System.out.println("B");
else
    System.out.println("C");
```

✍️ Answer below! (Hint: Which `if` pairs with which `else`?)

---

