
# Java: Random Numbers, If Statements, and Code Indentation

---

## 📅 Java Version Relevance

Most of the features discussed in these notes are valid for **Java 5.0 and onwards**, including:

- `Random` class functionality
    
- Static imports (`import static java.lang.System.out;`)
    
- If/else syntax and blocks
    

> ✅ These are **NOT deprecated** or old-school Java. They are still standard in modern Java (Java 17 and Java 21 LTS).

---

# 🎲 Randomness in Java

## ## What is Randomness?

Randomness in programming doesn't mean _truly_ random. Computers generate **pseudorandom numbers**—they follow patterns that _appear_ random.

> 💡 You can only call a number _random_ when it's part of a collection generated in an unpredictable way.

---

### 🔢 Example: Random Number from 1 to 10

### 🧠 Key Facts

- `Random.nextInt(10)` gives a value from **0 to 9**.
    
- `Random.nextInt(10) + 1` gives **1 to 10**, inclusive.
    
- All values are **equally likely**.
    
- The numbers are **unpredictable**.
    
- The numbers are **uniformly distributed** over time.

```java
import java.util.Random;

public class RandomExample {
    public static void main(String[] args) {
        Random myRandom = new Random();
        for (int i = 0; i < 20; i++) {
            System.out.print(myRandom.nextInt(10) + 1 + " ");
        }
    }
}
```

**Expected Output** (example):

```
7 3 10 2 1 8 6 4 9 5 3 2 7 1 10 6 4 5 8 9
```

> ✨ `nextInt(10) + 1` generates numbers from **1 to 10 inclusive**.

---

## ⚠️ Pseudorandom vs True Random

- Computers use **algorithms** to generate numbers — hence "pseudo" random.
    
- True randomness would need physical randomness sources like:
    
    - Quantum states (e.g., qubits in quantum computers 🧠)
        
    - Real-world entropy (e.g., lottery ping-pong balls 🎱)
        

## 🐱 Schrödinger’s Landlady (Fun Trivia)

- Schrödinger's famous thought experiment was humorously adapted to explain randomness.
    
- Reminder: randomness ≠ pattern prediction.
    

---

# ✅ Java `if` Statements

## ✍️ Syntax:

```java
if (condition) {
    // code block
} else {
    // another block
}
```

### 🧱 Block = One Statement Rule

Even if an `if` block has multiple statements, wrapping them in `{}` makes them one _compound_ statement.

> 📌 Always use braces `{}` even for one-liners for clarity and maintainability.

---

## 📦 Static Imports

### 👇 Syntax:

```java
import static java.lang.System.out;
import static java.lang.System.in;
```

This allows you to:

- Replace `System.out.println` with `out.println`
    
- Replace `System.in` with `in`
    

### 🎯 Benefit:

```java
out.println("Hello World"); // instead of System.out.println()
```

```java
Scanner scanner = new Scanner(in); // No need for System.in
```

> 🧠 Pro Tip: Use this for cleaner code in long files, but avoid overusing for clarity's sake.

> 🧠 This is a Java 5+ feature. Super useful in long code files.

### When to Use:

- When writing lots of `System.out.println()`
    
- For competitive programming or demos
    

### When NOT to Use:

- In team projects (can reduce readability)

---

# 📄 Code Examples

## ✅ Special Offer Program (if without else)

```java
import java.util.Random;

public class SpecialOffer {
    public static void main(String[] args) {
        var myRandom = new Random();
        int randomNumber = myRandom.nextInt(10) + 1;

        if (randomNumber == 7) {
            System.out.println("An offer just for you!");
        }

        System.out.println(randomNumber);
    }
}
```

**Expected Output:**

```
An offer just for you!
7
```
	
(or just the number if it's not 7)

```
1
```

### 🔍 Breakdown:

- `Random.nextInt(10) + 1` generates a number from **1 to 10**.
    
- If it lands on 7, Java prints the offer.
    
- Always prints the number so user can see the result.

---

## ⚾ Winner Display Example (if-else with multiple prints

## ⚡ Static Imports

You can simplify verbose calls like `System.out.println` using **static import**:

```java
import java.util.Scanner;
import static java.lang.System.in;
import static java.lang.System.out;

public class TwoTeams {
    public static void main(String[] args) {
        var keyboard = new Scanner(in);
        int hankees, socks;

        out.print("Hankees and Socks scores? ");
        hankees = keyboard.nextInt();
        socks = keyboard.nextInt();

        out.println();  // print an empty line

        if (hankees > socks) {
            out.println("Hankees: " + hankees);
            out.println("Socks: " + socks);
        } else {
            out.println("Socks: " + socks);
            out.println("Hankees: " + hankees);
        }

        keyboard.close();
    }
}
```

**Expected Output:**

```
Hankees and Socks scores? 8 5

Hankees: 8
Socks: 5
```

## 🧪 Test It Yourself:

Try editing the scores:

- 10 and 5 → Hankees wins
    
- 4 and 7 → Socks wins

### 🔍 Breakdown:

- Uses `Scanner` to get two inputs from the user.
    
- Uses `if-else` to compare which score is higher.
    
- The team with the higher score is displayed first.

### 🤓 Why Static Import?

Saves us from writing `System.out` and `System.in` repeatedly. Keeps code short & sweet.

---

# ❌ Common Errors

## 🚫 Assignment Instead of Comparison

```java
if (number = 12) // ❌ Wrong!
```

Use:

```java
if (number == 12) // ✅ Right!
```

> $=$ assigns. $==$ compares.

---

## 😬 Poor Indentation Confusion Example

```java
int n = 100;
if (n > 100)
    System.out.println("n is big");
System.out.println("Will Java display this line of text?");
if (n <= 100)
    System.out.println("n is small");
System.out.println("How about this line of text?");
```

**Expected Output:**

```
Will Java display this line of text?
n is small
How about this line of text?
```

> Misleading indentation may _fool the reader_, but Java follows brace rules strictly.

---

# 🎮 Programming Challenges

## 🙂 Smiley Face Program

```java
import java.util.Scanner;

public class SmileyFace {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        System.out.print("Do you want to see a smiley face? (Y/N): ");
        char response = keyboard.next().charAt(0);

        if (response == 'Y') {
            System.out.println(":-)");
        } else {
            System.out.println(":-(");
        }
    }
}
```

**Input:** 

```
Do you want to see a smiley face? (Y/N): Y
```

**Expected Output:**

```
Do you want to see a smiley face? (Y/N): Y
:-)
```

## 😐😶 Successive If Statements

```java
if (response == 'Y') {
    System.out.println(":-)");
}
if (response == 'N') {
    System.out.println(":-(");
}
if (response == '?') {
    System.out.println(":-|\n");
}
```


```java
import java.util.Scanner;

public class SmileyFace {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        System.out.print("Do you want to see a smiley face? (Y/N): ");
        char response = keyboard.next().charAt(0);
        
        
        if (response == 'Y') {
            System.out.println(":-)");
        }
        if (response == 'N') {
            System.out.println(":-(");
        }
        if (response == '?') {
            System.out.println(":-|\n");
        }
    }
}
```

**Input:** 

```
Do you want to see a smiley face? (Y/N): ?
```

**Expected Output:**

```
Do you want to see a smiley face? (Y/N): ?
:-|
```

---

## 🎯 Guessing Game

```java
import java.util.Random;
import java.util.Scanner;

public class GuessGame {
    public static void main(String[] args) {
        Random random = new Random();
        int randomNum = random.nextInt(10) + 1;

        Scanner input = new Scanner(System.in);
        System.out.print("Guess a number (1 to 10): ");
        int guess = input.nextInt();

        if (guess == randomNum) {
            System.out.println("You win!");
        } else {
            System.out.println("You lose.");
        }
    }
}
```

---

## 📏 Length Converter

```java
import java.util.Scanner;

public class LengthConverter {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter meters: ");
        int meters = input.nextInt();
        System.out.print("Convert to (c for cm / m for mm): ");
        char unit = input.next().charAt(0);

        if (unit == 'c') {
            System.out.println("Centimeters: " + (meters * 100 + "cm"));
        }

        if (unit == 'm') {
            System.out.println("Millimeters: " + (meters * 1000  + "mm"));
        }
    }
}
```

**Input:** 

```
Enter meters: 10
Convert to (c for cm / m for mm): m
```

**Expected Output:**

```
Enter meters: 10
Convert to (c for cm / m for mm): m
Millimeters: 10000mm
```

---

## 📜 Poetry Program

```java
import java.util.Scanner;

public class PoetryBuff {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Want to read a poem? (Y/N): ");
        char reply = scanner.next().charAt(0);

        if (reply == 'Y') {
            System.out.println("\"The sun is high, the sky is blue,\nClouds drift by, and so do you.\nThe breeze is warm, the day is long,\nNature hums a lovely song.\"");
        } else {
            System.out.println("Sorry!\nI thought you were a poetry buff.\nMaybe you'll want to see the poem the next time you run this program.");
        }
    }
}
```

---

# 📚 Further Reading

|Topic|Link|
|---|---|
|Java Random Class|[https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Random.html](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Random.html)|
|If Statements|[https://docs.oracle.com/javase/tutorial/java/nutsandbolts/if.html](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/if.html)|
|Static Import|[https://docs.oracle.com/javase/8/docs/technotes/guides/language/static-import.html](https://docs.oracle.com/javase/8/docs/technotes/guides/language/static-import.html)|
|Pseudorandomness|[https://en.wikipedia.org/wiki/Pseudorandom_number_generator](https://en.wikipedia.org/wiki/Pseudorandom_number_generator)|

---

> 💬 Want a quick quiz challenge about `if` statements or `Random`? Just say: **"Hit me with a quiz!"**

> ✨ Also, this is the perfect time to start building your own text-based Java games — `Guess the Number`, `Dice Roller`, or even a `RPG name generator` using `Random`. Get creative! 😎
