
# Java Input Statements & Scanner Class

---

## 📌 Overview

Java provides powerful tools to read input from various sources such as the keyboard, files, strings, and streams. The primary tool for reading input is the **`Scanner`** class, which is a part of the **`java.util`** package.

> 🧠 **Standard Input Device:** Keyboard  (usually via `System.in`)
> 🧠 **Standard Output Device:** Monitor (usually via `System.out`)

Previously, you’ve seen `System.out` for output. Now, we’ll explore `System.in` for **input**.

---

## 🎯 Introduction to Java Input & Scanner

> In Java, **standard input** is typically the keyboard (via `System.in`), and **standard output** is the monitor (via `System.out`). You’ve already used `System.out` to print output; now it’s time to read data from the user!

- `System.in` provides raw byte input.
    
- We want to convert raw input into meaningful **tokens** like numbers or words.
    
- Java’s **Scanner class** is the go-to for breaking input into tokens and parsing them.

---

## 🗂️ Packages and the `import` Statement

Java organizes related classes into **packages**. For example:

- `java.lang`: Auto-imported, contains basic classes (like `String`, `Math`, `System`)
    
- `java.util`: Contains utility classes like `Scanner`
    

>💡 **Note**: `java.lang` is imported by default. Other packages like `java.util` must be imported manually.

### Importing Scanner:

Java classes are grouped into **packages**.

> 🧩 The `Scanner` class belongs to the `java.util` package.


```java
import java.util.*;          // imports the entire utility package
import java.util.Scanner;    // imports only Scanner class
```

> 🔗 Official Java Docs: [Oracle Scanner Class](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)

---

## 🧾 Creating a Scanner Object

```java
Scanner scanner = new Scanner(System.in);
```

### Breakdown:

1. **Reference Variable:** `scanner` of type `Scanner`
    
2. **Object Creation:** `new Scanner(System.in)`
    
3. **Memory Allocation:** The object is stored in memory and its address is assigned to `scanner`
    

Similar to:

```java
int k = 10;
```

---

## 🔍 Tokenizing Input

- Scanner splits input into **tokens** based on delimiters (default whitespace).

Given this input:

```
123-45-6789 James Watts 56 5432.78
```

**Tokens are:**

- `123-45-6789` → `String`
    
- `James` → `String`
    
- `Watts` → `String`
    
- `56` → `int`
    
- `5432.78` → `double`
    

---

## 🧪 Sample Code: Basic Scanner Usage

```java
import java.util.Scanner;

public class ScannerOne {
    public static void main(String[] args) {
        String socialSecNum, firstName, lastName;
        int age;
        double monthlySalary;

        Scanner scannedInfo = new Scanner(System.in);

        socialSecNum = scannedInfo.next();
        firstName = scannedInfo.next();
        lastName = scannedInfo.next();
        age = scannedInfo.nextInt();
        monthlySalary = scannedInfo.nextDouble();

        System.out.println(socialSecNum);
        System.out.println(firstName);
        System.out.println(lastName);
        System.out.println(age);
        System.out.println(monthlySalary);
    }
}
```

### ✅ Input

```text
123-45-6789 James Watts 56 5432.78
```
### ✅ Expected Output

```
123-45-6789
James
Watts
56
5432.78
```

---

## ✍️ Single Character Input

### Strategy:

- `next()` gives you a `String` (even if it's one letter)
    
- Use `.charAt(0)` to extract the **first character** from that string
    

### Example:

```java
String middle;
char middleInitial;
middle = scannedInfo.next();
middleInitial = middle.charAt(0);
```

### OR combine it:

- `Scanner.next()` returns a `String`, but if you want a single `char`:

```java
char middleInitial = scannedInfo.next().charAt(0);
```

### Full Example with Middle Initial:

```java
import java.util.Scanner;

public class ScannerTwo {
    public static void main(String[] args) {
        String socialSecNum, firstName, lastName;
        char middleInitial;
        int age;
        double monthlySalary;

        Scanner scannedInfo = new Scanner(System.in);

        socialSecNum = scannedInfo.next();
        firstName = scannedInfo.next();
        middleInitial = scannedInfo.next().charAt(0);
        lastName = scannedInfo.next();
        age = scannedInfo.nextInt();
        monthlySalary = scannedInfo.nextDouble();

        System.out.println(socialSecNum);
        System.out.println(firstName);
        System.out.println(middleInitial);
        System.out.println(lastName);
        System.out.println(age);
        System.out.println(monthlySalary);
    }
}
```

### ✅ Input

```text
123-45-6789 James T Watts 56 5432.78
```
### ✅ Expected Output

```
123-45-6789 ↵
↵
James T ↵
↵
↵
Watts ↵
↵
56 ↵
5432.78 ↵
```

This input is still valid.

> 🔔 Note: Line breaks or blank lines don’t matter — as long as the **data order and type match**.

---

## 🔍 Scanning Basics

- Scanner reads **tokens**, separated by **whitespace (default)** or **custom delimiters**.
    
- Can use **regex** patterns to match specific input types.
    
- Methods are divided into two sets:
    
    - `hasNextX()` → Checks if the next input is of type X
        
    - `nextX()` → Retrieves the next input of type X
     
---
## 🔁 Scanner Input Types & Methods

### `hasNextX()` Methods

Used to **check** if the next input token matches a specific type.

|Method|Description|
|---|---|
|`hasNext()`|Any token available|
|`hasNextInt()`|Next token is `int`?|
|`hasNextDouble()`|Next token is `double`?|
|`hasNextLine()`|Next line is available?|
|`hasNextBoolean()`|Next token is `boolean`?|
|...|Other types: byte, float, long, BigInteger, etc.|

### `nextX()` Methods

Used to **read and convert** the next token to a specific type.

| Method             | Returns                | Description                                      |
| ------------------ | ---------------------- | ------------------------------------------------ |
| `next()`           | `String`               | Reads next token as `String`                     |
| `nextInt()`        | `int`                  | Reads next token and converts to `int`           |
| `nextDouble()`     | `double`               | Reads next token and converts to `double`        |
| `nextLine()`       | Whole line as `String` | Reads entire line (including spaces)             |
| `nextBoolean()`    | `boolean`              | Reads next token as a `boolean` value            |
| `next().charAt(0)` | `char`                 | Read next token as `String` and get first `char` |

### Example with Loop

```java
Scanner conin = new Scanner(System.in);
int i;

while (conin.hasNextInt()) {
    i = conin.nextInt();
    System.out.println("Integer read: " + i);
}
```


## 💻 Detailed Code Example

### Complete Example:

```java
import java.util.Scanner;

public class ScannerDemo {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);

        System.out.println("Enter two whole numbers separated by one or more spaces:");
        int n1 = keyboard.nextInt();
        int n2 = keyboard.nextInt();
        System.out.println("You entered " + n1 + " and " + n2);

        System.out.println("Next enter two numbers (decimal point is OK):");
        double d1 = keyboard.nextDouble();
        double d2 = keyboard.nextDouble();
        System.out.println("You entered " + d1 + " and " + d2);

        System.out.println("Next enter two words:");
        String s1 = keyboard.next();
        String s2 = keyboard.next();
        System.out.println("You entered \"" + s1 + "\" and \"" + s2 + "\"");

        keyboard.nextLine(); // Consume leftover newline

        System.out.println("Next enter a line of text:");
        s1 = keyboard.nextLine();
        System.out.println("You entered: '" + s1 + "'");
    }
}
```

### ✅ **Expected Output:**

```
Enter two whole numbers separated by one or more spaces:
42 43
You entered 42 and 43
Next enter two numbers (decimal point is OK):
9.99 21
You entered 9.99 and 21.0
Next enter two words:
plastic spoons
You entered "plastic" and "spoons"
Next enter a line of text:
May the hair on your toes grow long and curly.
You entered: 'May the hair on your toes grow long and curly.'
```

---

## 📄 Scanner Constructors Summary

| Constructor                    | Description                                     |
| ------------------------------ | ----------------------------------------------- |
| `Scanner(System.in)`           | Reads from keyboard                             |
| `Scanner(String)`              | Reads from given string                         |
| `Scanner(File)`                | Reads from file (needs `FileNotFoundException`) |
| `Scanner(File, Charset)`       | Reads from file with specific encoding          |
| `Scanner(Path)`                | Reads from file path                            |
| `Scanner(ReadableByteChannel)` | Reads from a channel                            |
>☑️ **Always close the Scanner** using `.close()` to free resources.

### 🔧 Example 1:

```java
Scanner scanner1 = new Scanner(System.in);                // From keyboard
Scanner scanner2 = new Scanner(new File("test.txt"));     // From file
Scanner scanner3 = new Scanner("123 abc");                // From string
```

### 🔧 Example 2:  `Scanner(String)`

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
		
		// String input with different types of data
        String instr = "10 99.88 Hello";
        
	    // Create Scanner using the string instead of System.in
        Scanner scanner = new Scanner(instr);
        
        int x = scanner.nextInt();
        double y = scanner.nextDouble();
        String msg = scanner.next();
        
	    // Print the extracted values
        System.out.println(x + ", " + y + ", " + msg);
    }
}
```

### ✅ Expected Output

```
10, 99.88, Hello
```

---

## ⚠️ Exceptions

- `InputMismatchException`: Wrong data type (e.g., expecting `int`, got `String`)
    
- `NoSuchElementException`: No input available
    

### ✅ Best Practice

> Always use `hasNextX()` to validate input **before** calling `nextX()`.

---

## 🧠 Self-Check Questions

### Fill in the blanks:

**35.** In Java, classes are grouped into → `packages`  
**36.** Scanner class belongs to → `java.util`  
**37.** `charAt` is a method of → `String` class  
**38.** `charAt` returns a → `char`

---

# 🔍 Reading a Character: `findWithinHorizon()`

Java has no direct `nextChar()` method. Instead:

```java
char c = scanner.findWithinHorizon(".", 0).charAt(0);
```

> `.` matches **any character** in regex. The `0` horizon means unlimited look-ahead.

### ⚠️ Important

- A blank space is **also a character**.
    
- Always check for `null` to avoid `NullPointerException`.
    

>❗ Input like `po` is read as `'p'` and `'o'`.  If you type `p o`, you'll get `'p'` and `' '` (space).

---

# 💡 Real-World Example: Reverse a 4-letter Word

```java
import java.util.Scanner;

public class ReverseWord {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        char c1, c2, c3, c4;
        
		// Read one character at a time
        c1 = keyboard.findWithinHorizon(".", 0).charAt(0);
        c2 = keyboard.findWithinHorizon(".", 0).charAt(0);
        c3 = keyboard.findWithinHorizon(".", 0).charAt(0);
        c4 = keyboard.findWithinHorizon(".", 0).charAt(0);

		// Print characters in reverse order
        System.out.print(c4);
        System.out.print(c3);
        System.out.print(c2);
        System.out.print(c1);

        keyboard.close();
    }
}
```

### 🎯 Input:

```
pots
```

### 🎯 Expected Output:

```
stop
```

## 🧠 Why This Works

Each call to `findWithinHorizon` grabs the **next** character. When we store each one separately and then print them in **reverse order**, we reverse the word!

Perfect for beginners learning about **input**, **characters**, and **control of flow** in Java. 

---

# ✍️ Exercise: Capitalizing a Name

```java
import java.util.Scanner;

public class CapitalizeName {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        char first = Character.toUpperCase(sc.findWithinHorizon(".", 0).charAt(0));
        char second = Character.toLowerCase(sc.findWithinHorizon(".", 0).charAt(0));
        char third = Character.toLowerCase(sc.findWithinHorizon(".", 0).charAt(0));

        System.out.println("Capitalized Name: " + first + second + third);

        sc.close();
    }
}
```

### 🎯 Input:

```
aNN
```
### 🎯 Output:

```
Capitalized Name: Ann
```

---
## 🔍 Behind `findWithinHorizon()`

### 📜 Regular Expressions (Regex)

- `.` → Any character (except newline)
    
- `\d` → A single digit (0–9)
    
- `\d\d\d` → Three digits in a row
    

### Code Examples:

```java
import java.util.Scanner;

public class DigitSequenceFinder {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        
        String digitSequence = keyboard.findWithinHorizon("\\d\\d\\d", 0);
        System.out.println("Found digit sequence: " + digitSequence);
        
        keyboard.close();
    }
}
```

### **Input:** 

```
Testing 123 Testing
```

### **Output:**

```
Found digit sequence: 123
```


```java
System.out.println(keyboard.findWithinHorizon("\\d\\d\\d", 9)); // null
System.out.println(keyboard.findWithinHorizon("\\d\\d\\d", 11)); // 123
```

> 🧠 The horizon value limits how far into the input Java searches.

---

# 🧠 Challenge: Print All Permutations of 3-Letter Word

```java
import java.util.Scanner;

public class PermuteThree {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        char a = sc.findWithinHorizon(".", 0).charAt(0);
        char b = sc.findWithinHorizon(".", 0).charAt(0);
        char c = sc.findWithinHorizon(".", 0).charAt(0);

        System.out.println("\nAll arrangements:");
        System.out.println("" + a + b + c);
        System.out.println("" + a + c + b);
        System.out.println("" + b + a + c);
        System.out.println("" + b + c + a);
        System.out.println("" + c + a + b);
        System.out.println("" + c + b + a);

        sc.close();
    }
}
```

### 🎯 Input:

```
box
```
### 🎯 Output:

```
All arrangements:
box
bxo
obx
oxb
xbo
xob
```

### 📥 **User Input**

The user types a 3-letter word like:

```
box
```

Each letter is read individually using:

```java
char a = sc.findWithinHorizon(".", 0).charAt(0);
```

> ✏️ This line grabs one character at a time from the input.

### ⚙️ **Behind the Scenes**

- Characters `a`, `b`, and `c` are assigned the 1st, 2nd, and 3rd letters.
    
- Six `System.out.println` statements print all the different orders:
    

```java
System.out.println("" + a + b + c);
System.out.println("" + a + c + b);
System.out.println("" + b + a + c);
System.out.println("" + b + c + a);
System.out.println("" + c + a + b);
System.out.println("" + c + b + a);
```

> 🎯 This covers all **6 permutations** of the 3 characters.

---

## ⚠️ `findWithinHorizon()` vs `nextInt()`

| Method                                | Input Format                            | Behavior                                  |
| ------------------------------------- | --------------------------------------- | ----------------------------------------- |
| `nextInt()`                           | Space-separated integers (e.g., `80 6`) | Reads integer tokens; fails on `80x`      |
| `findWithinHorizon(".", 0).charAt(0)` | No space required                       | Reads one character (even space itself)\| |

# 🧪 Input Mismatch Example

```java
Scanner sc = new Scanner(System.in);
int x = sc.nextInt();  // expects number
char y = sc.findWithinHorizon(".", 0).charAt(0);  // expects char
```

### ❌ Problem Case

```
Input: 80x
➡️ Error: InputMismatchException at nextInt()
```

### ✅ Fix

```
Input: 80 x
➡️ x is now captured properly with separate space
```

---

## 📌 Java's Boolean Data Type

### 🔹 Declaration

```java
boolean isJavaFun;
```

### 🔹 Initialization

```java
boolean isJavaFun = true;
```

### 🔹 Assignment

```java
isJavaFun = false;
```

### 🔹 Input (via `Scanner`)

Java lets the user input `true` or `false` (case-insensitive):

```java
Scanner input = new Scanner(System.in);
boolean userInput = input.nextBoolean();
```

> 🚨 Note: You can enter `TRUE`, `TrUe`, or `true` as input, and Java will still accept it.

---

## 💻 Full Code Example: Boolean Variables

```java
import java.util.Scanner;

/**
 * Illustrates declaration, initialization, input and
 * output of logical variables
 */
public class LogicalData {
    public static void main(String[] args) {
        boolean numberFound;                // Declaration
        boolean processFinished = false;    // Initialization
        boolean errorReport = true;         // Initialization

        Scanner scannedInfo = new Scanner(System.in);

        // Output
        System.out.println("processFinished = " + processFinished);
        System.out.println("errorReport = " + errorReport);

        // Input
        System.out.print("Enter two boolean values: ");
        System.out.flush();
        numberFound = scannedInfo.nextBoolean(); // Reads first boolean input

        // Assignment
        processFinished = errorReport;
        errorReport = scannedInfo.nextBoolean(); // Reads second boolean input

        // Output final values
        System.out.println();
        System.out.println("New values are as follows:");
        System.out.println("numberFound (first input) = " + numberFound);
        System.out.println("processFinished (previous value of errorReport) = " + processFinished);
        System.out.println("errorReport (second input) = " + errorReport);
    }
}
```

### ✅ Expected Output

```
processFinished = false
errorReport = true
Enter two boolean values: TRue FaLSe

New values are as follows:
numberFound (first input) = true
processFinished (previous value of errorReport) = true
errorReport (second input) = false
```

### 🧾 **Variable Reassignment**

```java
processFinished = errorReport;
errorReport = scannedInfo.nextBoolean();
```

- `processFinished` now takes **the current value of errorReport** (`true`).
    
- `errorReport` takes **the second boolean input** (`false` in example).

---

## 📒 Important Notes

> 🔸 Boolean literals (`true`, `false`) are **case-sensitive** when used in code. Use exactly `true` or `false`.

> 🔸 Input values are interpreted **at runtime**, and they are parsed from `String` to `boolean` using `nextBoolean()`.

> ⚠️ Typing anything other than valid `true/false` during input (like `yes`, `no`, `maybe`) will crash the program with an `InputMismatchException`.

---

## 🧠 Real-World Use Cases

|Situation|Logical Expression|
|---|---|
|Go for a run if it's not raining|`boolean isRaining = false;`|
|Show discount if user is a student|`boolean isStudent = true;`|
|Turn on heater if temp < 20 degrees|`boolean tempTooLow = currentTemp < 20;`|

---

## 📊 Table: Boolean Operations Summary

| Operation   | Syntax Example      | Result  |
| ----------- | ------------------- | ------- |
| Logical AND | `true && false`     | `false` |
| Logical OR  | `true` \|\| `false` | `true`  |
| Logical NOT | `!true`             | `false` |

---

## 🔍 Self-Check Quiz

> ✅ True or False: “Bill is taller than George” is a logical expression.  
> ✅ **Answer: True** (Because it can be evaluated to either true or false)

> ❌ True or False: “How are you?” is a logical expression.  
> ❌ **Answer: False** (Because it's just a question, not a condition with true/false result)

---

## 🔍 Changing Scanner Delimiters

Java's `Scanner` class by default uses whitespace characters (spaces, tabs, and line breaks) as delimiters to separate input tokens. However, Java provides a way to customize these delimiters.

> **Important:** Once the delimiter is changed, whitespace is no longer recognized as a delimiter.

### 📌 How to Change Scanner Delimiters

Here's how to change the delimiter from whitespace to a custom string like `##`:

```java
Scanner keyboard2 = new Scanner(System.in);
keyboard2.useDelimiter("##");
```

### 📖 Real-world Example

Consider this input:

```
funny wo##rd ##
```

This input will be split into tokens as `funny wo` and `rd` .

### 🖥️ Full Java Example

```java
import java.util.Scanner;

public class DelimitersDemo {
    public static void main(String[] args) {
        Scanner keyboard1 = new Scanner(System.in);
        Scanner keyboard2 = new Scanner(System.in);
        keyboard2.useDelimiter("##");

        String s1, s2;

        System.out.println("Enter a line of text with two words:");
        s1 = keyboard1.next();
        s2 = keyboard1.next();
        System.out.println("The two words are \"" + s1 + "\" and \"" + s2 + "\"");

        System.out.println("Enter a line of text with two words delimited by ##:");
        s1 = keyboard2.next();
        s2 = keyboard2.next();
        System.out.println("The two words are \"" + s1 + "\" and \"" + s2 + "\"");
    }
}
```

### 📋 **Expected Output**:

```
Enter a line of text with two words:
funny wo##rd##
The two words are "funny" and "wo##rd##"
Enter a line of text with two words delimited by ##:
funny wo##rd##
The two words are "funny wo" and "rd"
```

> 🔑 **Key takeaway:** Different `Scanner` objects can simultaneously have different delimiters.

---

# 📐 Formatted Output with `printf`

Java (from version 5.0 onwards) supports formatted output using the `printf` method, similar to the C programming language.

## 📌 Syntax

```java
System.out.printf("format specifier", arguments);
```

> **Important:** Format specifiers determine how the argument(s) are displayed.

### 📖 Common Format Specifiers:

|Specifier|Output Type|Example|Output|
|---|---|---|---|
|`%c`|Character|`%c`|`A`|
|`%d`|Decimal Integer|`%5d`|`42`|
|`%f`|Floating-point number|`%6.2f`|`19.50`|
|`%e`|Exponential Floating-point|`%e`|`1.950000e+01`|
|`%s`|String|`%10s`|`Widgets`|

### 🧑‍💻 Example

```java
public class PrintfExample {
    public static void main(String[] args) {
        double price = 19.5;
        int quantity = 2;
        String item = "Widgets";

        System.out.println("Price using println:" + price);
        System.out.printf("Price using printf formatting:%6.2f\n", price);

        System.out.printf("%10s sold:%4d at $%5.2f. Total = $%1.2f\n",
                item, quantity, price, quantity * price);
    }
}
```

### 📋 **Expected Output**:

```
Price using println:19.5
Price using printf formatting: 19.50
   Widgets sold:   2 at $19.50. Total = $39.00
```

> 🚨 **Note:** Extra spaces are added if the output requires fewer characters than specified. If the output requires more, the field expands automatically.

---

## 📌 Version Compatibility Notes

- All provided Java notes, including Scanner and `printf`, are valid for Java 5 and above.
    
- `Scanner` and `printf` remain essential and widely used in the latest Java versions (Java 21 as of now).
    

---

## 📚 Further Reading

- 📖 [Java Scanner (Oracle)](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)
    
- 📖 [Scanner Tutorial (W3Schools)](https://www.w3schools.com/java/java_user_input.asp)
    
- 📖 [Java Input Explained (GeeksForGeeks)](https://www.geeksforgeeks.org/scanner-class-in-java/)
    
- 📖 [Java Booleans - W3Schools](https://www.w3schools.com/java/java_booleans.asp)
    
- 📖 [Oracle Docs - Primitive Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
    
- 📖 [Baeldung - Boolean Logic in Java](https://www.baeldung.com/java-boolean-operators)
    
- 📖[Oracle Documentation - Scanner](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Scanner.html)
    
- 📖[Oracle Documentation - Formatter](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Formatter.html)
    
- 📖[Java printf Guide](https://www.baeldung.com/java-printstream-printf)
    

---

## 🎮 Real-World Use Cases

- Taking user input in console applications
    
- Reading CSV or text files line-by-line
    
- Parsing command-line arguments or text-based configs
    
- Making simple terminal-based forms
    

---

## 🧪 Challenge Practice (for you 💡)

Write a program that:

- Reads 2 integers
    
- Reads a full line of text
    
- Prints them in reverse order (text, int2, int1)
    

---

Want a quiz next? Or a game on Java input statements? 😏