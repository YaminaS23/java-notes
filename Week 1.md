
# Introduction to Java

---

## 📌 What Is Java?

Java is a **general-purpose programming language** that supports:

- **Object-Oriented Programming (OOP)**
    
- **Procedural Programming**
    
- **Functional Programming**
    

> ✅ Although Java is known for being object-oriented, it can be used purely as a procedural language.

Java was originally developed in **1991** by a team at **Sun Microsystems** (now owned by Oracle). It was officially released in **1995**.

Originally called **Oak**, it was designed for **set-top boxes** and later evolved into a powerful Internet-based development tool.

---

## 💡 Key Features of Java

|Feature|Description|
|---|---|
|**WORA**|Write Once, Run Anywhere — Java code runs on any platform with a JVM|
|**Bytecode**|Java source code is compiled into an intermediate platform-independent code|
|**JVM**|Java Virtual Machine — executes bytecode on different platforms|
|**Automatic Garbage Collection**|Java automatically manages memory|
|**Exception Handling**|Java provides built-in support to handle runtime errors|
|**Threading**|Java has built-in multithreading support|
|**Security**|Java offers strong type-checking, restricted memory access|

> 🧠 Java is not compiled directly to machine code. It is compiled into **bytecode**, which is interpreted by the JVM. This is what makes it **platform-independent**.

---

## 🛠️ Java Syntax & Code Example

### 👇 Hello World Program

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

**Expected Output:**

```
Hello, World!
```

---

## ⚙️ Java Compilation & Execution Process

1. Write code in `.java` file
    
2. Compile using `javac FileName.java` → generates `.class` bytecode file
    
3. Run using `java FileName`
    

> 🧑‍💻 Bytecode runs on JVM, not directly on your OS. That’s the magic behind WORA!

---

## 🚀 Historical Evolution

### 📜 Timeline

- **1991** – Java project initiated by **James Gosling** and team
    
- **1992** – First Oak prototype
    
- **1995** – Renamed to **Java**, publicly launched
    
- **2010** – Oracle acquires Sun Microsystems
    

### 🔑 Contributors

- James Gosling
    
- Patrick Naughton
    
- Bill Joy
    
- Tim Lindholm
    
- Frank Yellin
    

> ☕ Java was originally made for embedded systems like **microwave ovens** and **TV remotes**.

---

## 🌐 Java & The Web

With the **rise of the Internet**, Java became the top choice for **web programming** because of its:

- Platform independence
    
- Secure architecture
    
- Network-centric libraries
    

### 🔄 Applets (Now Deprecated)

```html
<applet code="MyApplet.class" width="300" height="300">
</applet>
```

Applets were Java programs embedded in web pages. Removed since Java SE 9.

> ❌ Browsers no longer support applets due to security concerns.

---

## 🧪 Error Types in Java

|Type|Description|Detected by|
|---|---|---|
|**Compile-time**|Syntax errors (e.g., missing `;`)|Compiler|
|**Runtime**|Errors during execution (e.g., `17 / 0`)|JVM throws Exception|
|**Logic**|Program runs but gives wrong result|Testers or Users|

### 🐞 Debugging

- The process of finding and fixing bugs
    
- IDEs like IntelliJ, Eclipse, NetBeans provide **debuggers**
    

---

## 🧵 Multithreading in Java

Java has built-in support for **concurrent programming**.

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }

    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
    }
}
```

**Expected Output:**

```
Thread running...
```

---

## ☑️ Robustness & Memory Management

- Java uses **automatic garbage collection**.
    
- No manual memory freeing required (unlike C++)
    
- Handles common runtime issues via **exception handling**
    

```java
public class DivideByZero {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        }
    }
}
```

**Expected Output:**

```
Cannot divide by zero!
```

---

## 🧠 Java vs C++

|Feature|Java|C++|
|---|---|---|
|Memory Mgmt|Automatic (Garbage Collector)|Manual|
|Pointers|Not supported|Fully supported|
|Multiple Inheritance|Not supported directly|Supported|
|Platform-Independent|Yes (via JVM)|No|
|Syntax Similarity|Yes|Yes (Java borrows from C++)|

> 🎯 Java is NOT a simplified version of C++ — it's a separate language solving different problems.

---

## 🎓 Real-World Use Cases

- **Web Applications** – Spring Boot, JSP
    
- **Mobile Apps** – Android development
    
- **Enterprise Applications** – ERP, CRM tools
    
- **Games** – Minecraft was originally written in Java
    
- **Big Data** – Hadoop core components
    

---

## 📚 Further Reading

- [Java Documentation (Oracle)](https://docs.oracle.com/en/java/)
    
- [History of Java (Wikipedia)](https://en.wikipedia.org/wiki/Java_\(programming_language\))
    
- [Java Tutorials - W3Schools](https://www.w3schools.com/java/)
    
- [Java vs. C++ – GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-java-and-cpp/)
    

---

> 💥 "Java was to Internet programming what C was to system programming — a revolutionary force."