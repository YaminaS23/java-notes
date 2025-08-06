
# Java Strings, Equality, Precedence & Lexicographical Order

---

## 🧐 **Introduction to String Methods**

> A `String` variable in Java is not simple like primitive types (e.g., `int`). Instead, it is an object of the `String` class, which includes data (a sequence of characters) and methods for manipulating that data.

---

## ⚙️ **Basic String Methods**

### 🔸 **`length()`**

> Returns the number of characters in a `String` object.

**Example:**

```java
public class LengthDemo {
    public static void main(String[] args) {
        String greeting = "Hello";
        int length = greeting.length();
        System.out.println("The length is: " + length);
    }
}
```

**Expected Output:**

```
The length is: 5
```

### 🔸 **Counting spaces and symbols:**

```java
String command = "Sit Fido!";
String answer = "bow-wow";

System.out.println("Command length: " + command.length());
System.out.println("Answer length: " + answer.length());
```

**Expected Output:**

```
Command length: 9
Answer length: 7
```

---

## 📍 **Index and Positions in Strings**

- **Java strings are zero-indexed.**
    
    - First character = index 0
        
    - Last character = index `length() - 1`
        
- Spaces and symbols count too!


> Indices in Java strings start from **0**.

```markdown
"Hi Mom"
Indices:  0  1  2  3  4  5
Chars:    H  i     M  o  m
```

> ⚠️ If you try `s.charAt(12)` here, Java will throw an **IndexOutOfBoundsException**.


### 🔸 **`indexOf()`**

> Finds the position of the first occurrence of a substring.

**Example:**

```java
public class IndexDemo {
    public static void main(String[] args) {
        String phrase = "Java is fun.";
        int index = phrase.indexOf("fun");
        System.out.println("Index of 'fun': " + index);
    }
}
```

**Expected Output:**

```
Index of 'fun': 8
```

---

## 🧩 **String Manipulation**

> Strings in Java are **immutable** (cannot be changed directly). However, variables referencing strings can point to new objects.

**Example:**

```java
public class StringChangeDemo {
    public static void main(String[] args) {
        String name = "D'Aargo";
        name = "Ka " + name;
        System.out.println(name);
    }
}
```

**Expected Output:**

```
Ka D'Aargo
```

---

## 🏷️ Core String Methods & Real-World Examples

|Method|What it Does|Example Usage|Output|
|---|---|---|---|
|`length()`|Returns number of characters|`"hi ".length()`|3|
|`charAt(idx)`|Returns character at given index|`"cat".charAt(2)`|'t'|
|`indexOf(sub)`|Returns index of substring (first)|`"hello".indexOf("e")`|1|
|`substring(start, end)`|Returns a substring|`"hello".substring(1,4)`|"ell"|
|`toUpperCase()`|All uppercase letters|`"ok".toUpperCase()`|"OK"|
|`toLowerCase()`|All lowercase letters|`"OK".toLowerCase()`|"ok"|
|`equals(str)`|Checks if strings match (case)|`"Yes".equals("yes")`|false|
|`equalsIgnoreCase(str)`|Checks if strings match (ignore case)|`"Yes".equalsIgnoreCase("yes")`|true|
|`replace(a, b)`|Replaces all occurrences of a with b|`"abcabc".replace('a','x')`|"xbcxbc"|
|`trim()`|Removes whitespace front & back|`" hi ".trim()`|"hi"|

> ✅ **All methods work in Java 8 and newer (including Java 21).**

---


## 📝 **String Processing Example**

### 🛠️ **Using multiple methods** (`substring()`, `toUpperCase()`)

```java
public class StringDemo {
    public static void main(String[] args) {
        String sentence = "Text processing is hard!";
        int position = sentence.indexOf("hard");

        System.out.println(sentence);
        System.out.println("012345678901234567890123");
        System.out.println("The word \"hard\" starts at index " + position);

        sentence = sentence.substring(0, position) + "easy!";
        sentence = sentence.toUpperCase();

        System.out.println("The changed string is:");
        System.out.println(sentence);
    }
}
```

**Expected Output:**

```
Text processing is hard!
012345678901234567890123
The word "hard" starts at index 19
The changed string is:
TEXT PROCESSING IS EASY!
```

---

## ⚠️ **Gotcha: String Index Out of Bounds**

> Indices must be between **0** and **`length - 1`**.

**Example (Incorrect):**

```java
String word = "Java";
System.out.println(word.charAt(4)); // Runtime error
```

**Correct approach:**

```java
String word = "Java";
System.out.println(word.charAt(word.length() - 1));
```

**Expected Output:**

```
a
```

---

## 💡 **Real-World Use Case**

### 🔎 **Data Validation with String Methods:**

```java
public class ValidationDemo {
    public static void main(String[] args) {
        String email = "user@example.com";
        if(email.contains("@") && email.contains(".")){
            System.out.println("Valid email format.");
        } else {
            System.out.println("Invalid email format.");
        }
    }
}
```

**Expected Output:**

```
Valid email format.
```

---

## 📋 **Quick Reference Table:**

|Method|Purpose|Example|
|---|---|---|
|`.length()`|Returns length of the string|`"Hello".length()` → `5`|
|`.indexOf()`|Returns index of first occurrence of substring|`"Hello".indexOf("e")` → `1`|
|`.substring(a, b)`|Extracts substring from index `a` to `b-1`|`"Hello".substring(1, 4)` → `ell`|
|`.toUpperCase()`|Converts all characters to uppercase|`"Hello".toUpperCase()` → `HELLO`|
|`.toLowerCase()`|Converts all characters to lowercase|`"Hello".toLowerCase()` → `hello`|

---

## 🔤 Lexicographical Ordering of Strings

Lexicographical order = **dictionary order**. It compares strings character by character using Unicode values.

### 🧠 Theory

> In Java, string comparison uses **Unicode** values character by character, starting from the beginning of each string.

### ✅ Rules:

1. If all characters match and one string ends before the other ➡️ shorter string is considered **smaller**.
    
2. If mismatch occurs, order is based on the **first mismatched character**.
    
3. If both strings are equal in length and all characters match ➡️ strings are **equal**.
    
 45
### 📍Examples:

|String 1|String 2|Result|
|---|---|---|
|`lake`|`like`|`lake` < `like` (because `a` < `i`)|
|`like`|`live`|`like` < `live` (because `k` < `v`)|
|`live`|`liver`|`live` < `liver` (because `\0` < `r`)|

---

## 📚 Comparing Strings in Java

### ✅ Methods:

- `equals()` → checks if **content** is the same
    
- `compareTo()` → checks **lexicographical order**
    

### 📌 Syntax:

```java
strOne.equals(strTwo);
strOne.compareTo(strTwo);
```

### 💡 `compareTo()` Returns:

- Negative if `strOne < strTwo`
    
- Positive if `strOne > strTwo`
    
- `0` if both strings are equal
    
- ### **Returns:**
    
    - `0` → Strings are _identical_
        
    - `< 0` → Calling string is _less than_ the compared one
        
    - `> 0` → Calling string is _greater than_ the compared one
        

> ⚠️ Don't rely on the exact integer, only the **sign** (positive, negative, zero).

#### ✅ Example:

```java
strOne.compareTo(strTwo);
```

- Compares ASCII value differences from the first mismatching character.

---

## 🧰 String Comparison Methods

### `equals()` Method

Checks **content equality**.

```java
String str1 = "Hello";
String str2 = "Hello";
System.out.println(str1.equals(str2)); // true
```

### `compareTo()` Method

checks **lexicographical order.**

```java
String a = "apple";
String b = "banana";
System.out.println(a.compareTo(b)); // Negative number
```

> ✅ Use `equals()` for **equality check**, `compareTo()` for **sorting** or **ordering**

---

### ⚠️ Don't rely on actual integer from `compareTo()`, just use its **sign**.

### 🧪 Code Example 1:

```java
public class Main
{
    public static void main(String[] args)
    {
        String strOne = "America the beautiful";
        String strTwo = "America the beautiful!";
        String strThree = "Maple leaf";
        String strFour = "Maple Leaf";
        String strFive = "Maple Leaf";

        System.out.println("strOne.equals(strTwo) is " + strOne.equals(strTwo));
        System.out.println("strOne.compareTo(strTwo) is " + strOne.compareTo(strTwo));
        System.out.println("strTwo.equals(strOne) is " + strTwo.equals(strOne));
        System.out.println("strTwo.compareTo(strOne) is " + strTwo.compareTo(strOne));
        System.out.println("strThree.equals(strFour) is " + strThree.equals(strFour));
        System.out.println("strThree.compareTo(strFour) is " + strThree.compareTo(strFour));
        System.out.println("strThree.equals(\"Maple leaf\") is " + strThree.equals("Maple leaf"));
        System.out.println("strFour.compareTo(strFive) is " + strFour.compareTo(strFive));
    }
}
```

### 🧾 Expected Output:
```
strOne.equals(strTwo) is false
strOne.compareTo(strTwo) is -1
strTwo.equals(strOne) is false
strTwo.compareTo(strOne) is 1
strThree.equals(strFour) is false
strThree.compareTo(strFour) is 32
strThree.equals("Maple leaf") is true
strFour.compareTo(strFive) is 0
```

### 🧪 Observations:

| Comparison                         | Result | Explanation |
|------------------------------------|--------|-------------|
| strOne.equals(strTwo)             | false  | `!` is extra in `strTwo` |
| strOne.compareTo(strTwo)         | -1     | `!` makes `strTwo` greater (lexically) |
| strTwo.equals(strOne)            | false  | Order doesn't matter in `.equals()`—still false |
| strTwo.compareTo(strOne)         | 1      | Reverse order → result is +1 |
| strThree.equals(strFour)         | false  | `leaf` vs `Leaf` (case-sensitive) |
| strThree.compareTo(strFour)      | 32     | `'l' - 'L' = 108 - 76 = 32` |
| strThree.equals("Maple leaf")     | true   | Matches exactly |
| strFour.compareTo(strFive)       | 0      | Both have same content |
### 🧠 Note:

- `.compareTo()` gives a **positive** or **negative** value based on **first mismatched character**'s Unicode value.
- Always check the **sign** of the result, not the exact number (except when learning/debugging).

---

### 🧪 Code Example 2:

```java
public class EqualsCompareToStringMethods {
    public static void main(String[] args) {
        String strOne = "America the beautiful";
        String strTwo = "America the beautiful!";
        String strThree = "Maple leaf";
        String strFour = "Maple Leaf";
        String strFive = "Maple Leaf";

        System.out.println("strOne.equals(strTwo): " + strOne.equals(strTwo));
        System.out.println("strOne.compareTo(strTwo): " + strOne.compareTo(strTwo));
        System.out.println("strThree.equals(strFour): " + strThree.equals(strFour));
        System.out.println("strThree.equals(\"Maple leaf\"): " + strThree.equals("Maple leaf"));
        System.out.println("strFour.compareTo(strFive): " + strFour.compareTo(strFive));
    }
}
```

### 🧾 Expected Output:

```
strOne.equals(strTwo): false
strOne.compareTo(strTwo): -1
strThree.equals(strFour): false
strThree.equals("Maple leaf"): true
strFour.compareTo(strFive): 0 
```

---

## 💥 Equality Operators vs `.equals()` in Strings

### 📖 Theory

> "$==$" checks **reference equality** (are they pointing to the same memory?).  
> `.equals()` checks **content equality**.

### 👨‍🔬 Code Example:

```java
import java.util.Scanner;

public class EqualityOperatorsOnString {
    public static void main(String[] args) {
        String strOne = "Have a nice day!";
        String strTwo = "Have a nice day!";
        String strThree = "Happy birthday to you";
        String strFour = strThree;
        String strFive = "America";

        System.out.println("strOne == strTwo: " + (strOne == strTwo));
        System.out.println("strThree == strFour: " + (strThree == strFour));

        Scanner scannedInfo = new Scanner(System.in);
        System.out.print("Input the word America twice: ");
        strOne = scannedInfo.next();
        strTwo = scannedInfo.next();

        System.out.println("strOne == strTwo: " + (strOne == strTwo));
        System.out.println("strOne.equals(strTwo): " + strOne.equals(strTwo));
        System.out.println("strOne == strFive: " + (strOne == strFive));
        System.out.println("strOne.equals(strFive): " + strOne.equals(strFive));
    }
}
```

### 📌 Input:

```
strOne == strTwo: true
strThree == strFour: true
Input the word America twice: America America
```

### 📌 Output:

```
strOne == strTwo: true
strThree == strFour: true
Input the word America twice: America America
strOne == strTwo: false
strOne.equals(strTwo): true
strOne == strFive: false
strOne.equals(strFive): true
```


## 🔬 Step 1: Compile-Time vs Runtime Strings

```java
String strOne = "Have a nice day!";
String strTwo = "Have a nice day!";
System.out.println(strOne == strTwo); // ✅ true (same reference in memory pool)
```

> ✅ **Why?** Both are literals → Interned in Java → Stored in same memory location.

## 🔗 Step 2: Reference Equality (Aliasing)

```java
String strThree = "Happy birthday to you";
String strFour = strThree;
System.out.println(strThree == strFour); // ✅ true (pointing to same object)
```

> 🔎 **Why?** `strFour` is an alias of `strThree`.

## ⌨️ Step 3: User Input Creates New Objects

```java
Scanner scannedInfo = new Scanner(System.in);
strOne = scannedInfo.next();
strTwo = scannedInfo.next();
System.out.println(strOne == strTwo); // ❌ false
```

> 💡 **Why?** Even if the content is the same, two inputs create different String objects.

## ✅ Step 4: Use `.equals()` for Content Comparison

```java
System.out.println(strOne.equals(strTwo)); // ✅ true
```

> 📌 **Because:** Both contain same text ("America") → Content is equal.

## 🚫 Step 5: Even If One is Literal, $==$ Fails

```java
String strFive = "America";
System.out.println(strOne == strFive);       // ❌ false
System.out.println(strOne.equals(strFive));  // ✅ true
```

> 🧪 **Why?** `strOne` is input (new object), `strFive` is a literal (interned).


### 💡 Note:

> Compile-time literals may refer to the same object, but user inputs during **runtime** create new `String` objects!

---

## 🧠 Advanced: Equality Operators with Strings

### $==$ vs `equals()`

- $==$ checks **reference** equality (same memory address)
    
- `equals()` checks **content** equality
    

```java
String str1 = "Hello";
String str2 = "Hello";
System.out.println(str1 == str2); // true (compiler optimization)

String s1 = new String("Hi");
String s2 = new String("Hi");
System.out.println(s1 == s2); // false (different objects)
System.out.println(s1.equals(s2)); // true
```

### ⚠️ Input Strings Are Always New Objects

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        String str1 = input.next(); // "America"
        String str2 = input.next(); // "America"
        System.out.println(str1 == str2); // false
        System.out.println(str1.equals(str2)); // true
    }
}
```

### 📌 Input:

```
America
America
```

### 📌 Output:

```
America
America
false
true
```

> ✅ Prefer `.equals()` when comparing **String content**!

---

## 🔢 Precedence Rules in Java

Java respects a strict hierarchy when evaluating expressions.

### 📘 Highlights:

1. **Assignment ($=$)** has the lowest precedence.
    
2. **Arithmetic > Relational > Logical > Assignment**
    
3. Use parentheses to clarify complex expressions!
    

### 📊 Precedence Table:

| Precedence | Operators                         | Type                 | Associativity |
| ---------- | --------------------------------- | -------------------- | ------------- |
| 1          | `++`, `--`                        | Post-increment       | L to R        |
| 2          | `++`, `--`, `+`, `-`, `!`         | Pre-increment, Unary | R to L        |
| 4          | `*`, `/`, `%`                     | Arithmetic           | L to R        |
| 5          | `+`, `-`                          | Arithmetic           | L to R        |
| 7          | `<`, `<=`, `>`, `>=`              | Relational           | L to R        |
| 8          | $==$, `!=`                        | Equality             | L to R        |
| 10         | `^`                               | Logical XOR          | L to R        |
| 12         | `&&`                              | Logical AND          | L to R        |
| 13         | `                                 |                      | `             |
| 15         | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | Assignment           | R to L        |

---

## 🧪 Code Example: Operator Precedence

```java
public class OperatorPrecedence {
    public static void main(String[] args) {
        boolean workCompleted = true;
        boolean errorFound = false;
        char letter = 'J';
        int numOne = 7, numTwo = 9;
        double valueOne = 2.25, valueTwo = 0.452;

        System.out.println("!errorFound: " + (!errorFound));
        System.out.println("!workCompleted: " + (!workCompleted));
        System.out.println("workCompleted && !errorFound: " + (workCompleted && !errorFound));
        System.out.println("letter == 'P': " + (letter == 'P'));
        System.out.println("workCompleted || letter == 'P': " + (workCompleted || letter == 'P'));
        System.out.println("numOne + numTwo < 15: " + (numOne + numTwo < 15));
        System.out.println("numOne >= 0 && numOne <= 9: " + (numOne >= 0 && numOne <= 9));
        System.out.println("letter >= 'a' && letter <= 'z': " + (letter >= 'a' && letter <= 'z'));
        System.out.println("letter >= 'A' && letter <= 'Z': " + (letter >= 'A' && letter <= 'Z'));
        System.out.println("valueOne < 7.75 || valueTwo > 0.25 && valueTwo < 0.45: "
            + (valueOne < 7.75 || valueTwo > 0.25 && valueTwo < 0.45));
        System.out.println("(valueOne < 7.75 || valueTwo > 0.25) && valueTwo < 0.45: "
            + ((valueOne < 7.75 || valueTwo > 0.25) && valueTwo < 0.45));
    }
}
```

### ✅ Expected Output:

```
!errorFound: true
!workCompleted: false
workCompleted && !errorFound: true
letter == 'P': false
workCompleted || letter == 'P': true
numOne + numTwo < 15: false
numOne >= 0 && numOne <= 9: true
letter >= 'a' && letter <= 'z': false
letter >= 'A' && letter <= 'Z': true
valueOne < 7.75 || valueTwo > 0.25 && valueTwo < 0.45: true
(valueOne < 7.75 || valueTwo > 0.25) && valueTwo < 0.45: false
```

> 🧠 **Use parentheses liberally to clarify logic and control precedence!**

---

## ✅ Self-Check Solutions

11. `"Bad".compareTo("Good")` → **Returns a negative integer** ("Bad" < "Good") ✅
    
12. `"Better".compareTo("Best")` → **Returns a negative integer** ("Better" < "Best") ✅
    
13. **True**: If `strOne == strTwo` is true, then `.equals()` is **definitely** true.
    
14. **True**: If `strOne.equals(strTwo)` is false, they can’t be the same object → $==$ is false.
    
15. **True**: Relational operators (like `<`, `>`) have higher precedence than assignment $=$
    
16. **False**: Logical operators have **lower** precedence than arithmetic operators.
    

---

## 🔗 Further Reading

- [Java Docs: String.compareTo()](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#compareTo-java.lang.String-)
    
- [Java Operator Precedence Table - Oracle](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html)
    
- [Understanding String Pool in Java](https://www.geeksforgeeks.org/string-pool-java/)
    
- [Java Official Documentation (String Class)](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)
    
- [Baeldung: Java Strings](https://www.baeldung.com/java-string)
    
- [W3Schools: Java String Methods](https://www.w3schools.com/java/java_ref_string.asp)
    

---

## 🧠 Bonus Quiz Time (Let’s see if you’re sharp!)

### Q1. What will be the result of `"banana".compareTo("Banana")`?

A) 0  
B) > 0 ✅  
C) < 0  
D) Compilation error

> Hint: Unicode value of lowercase 'b' is **greater** than uppercase 'B'.

### Q2. If `str1 = "abc"` and `str2 = new String("abc")`, what’s `str1 == str2`?

A) true  
B) false ✅

---

Stay tuned next week, Yamina! We're diving into **StringBuilder**, performance hacks, and juicy Java trivia 🔥💻
