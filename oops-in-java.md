# Object Oriented Programming

## 1. Features of Object Oriented Programming

- **Encapsulation**: Wrapping data and methods into a single unit (class) to protect from outside interference.  
- **Abstraction**: Hiding implementation details and showing only essential features.  
- **Inheritance**: Acquiring properties and behaviors of one class in another (parent → child).  
- **Polymorphism**: Performing a single action in different ways (compile-time and run-time).  
- **Reusability**: Using existing code to build new functionalities without rewriting.  
- **Modularity**: Dividing a program into smaller, manageable, independent modules.

---

## 2. Overloading vs Overriding

| Aspect            | Overloading                                  | Overriding                                |
|-------------------|----------------------------------------------|--------------------------------------------|
| Definition        | Defining multiple methods with the same name but different parameters. | Defining a method in child class with same name and parameters as parent class. |
| Occurs At         | Compile-time (static polymorphism).          | Run-time (dynamic polymorphism).           |
| Parameters        | Must be different in number or type.          | Must remain exactly the same as parent.    |
| Return Type       | Can be different (if compatible).             | Must be same or subclass (covariant).      |
| Inheritance Need  | Not necessary.                               | Always requires inheritance.               |
| Example           | `area(int r)` and `area(int l, int b)`       | Child class redefines `toString()` method. |

# Java: Questions and Answers

## 3. Five Characteristics of Java

- Platform Independent: Java runs on any operating system due to its bytecode and JVM[web:2][web:5][web:17].
- Object-Oriented: Everything in Java is structured around objects and classes[web:2][web:17].
- Simple: Java removes many complexities found in other languages like C++[web:2][web:11].
- Secure: Has built-in security features for safe code execution[web:2][web:5].
- Robust: Strong error checking and memory management[web:2][web:5][web:11].

---

## 4. Difference Between JDK, JRE, JVM, and JIT

| Component | Purpose                                         | Includes                          | Usage                   |
|-----------|-------------------------------------------------|-----------------------------------|-------------------------|
| JDK       | Develop and run Java applications               | JRE, development tools            | Required for development|
| JRE       | Run Java applications                           | JVM, core libraries               | Needed to execute code  |
| JVM       | Executes Java bytecode                          | -                                 | Platform independence   |
| JIT       | Converts bytecode to machine code at runtime    | Part of JVM                       | Improves performance    |[web:6][web:12][web:18]

---

## 5. What Are Tokens And Its Types

- Tokens: Basic building blocks recognized by Java compiler[web:13][web:19].
- Types:
  - Keywords: Reserved words like `class`, `if`, `else`
  - Identifiers: Names for variables, classes, methods
  - Literals/Constants: Fixed values (numbers, strings)
  - Operators: Symbols like `+`, `-`, `*`, `/`
  - Separators: Punctuation (`,`, `;`, `()`, `{}`)
  
---

## 6. What Are Control Flow Statements

- Control flow statements: Direct the execution order of instructions in a program[web:8][web:20][web:14].
- Types:
  - Conditional: `if`, `if-else`, `switch`
  - Looping: `for`, `while`, `do-while`
  - Jump: `break`, `continue`, `return`

---

## 7. What Is Exception Handling In Java

- Exception handling: Mechanism for managing runtime errors to maintain regular program flow[web:9][web:15].
- Uses blocks/keywords: `try`, `catch`, `finally`, `throw`, `throws` to catch and handle exceptions gracefully.

---

## 8. What Are Constructors and Destructors

- Constructor: Special method with the class name, used to initialize objects when created[web:10][web:16].
- Destructor: Java does not have explicit destructors; cleanup is done automatically by the garbage collector when objects are no longer in use[web:10].

# 9. Upcasting and Downcasting
`````markdown
## Upcasting
- Upcasting is converting a child class reference/object into a parent class reference.
- It is safe and implicit.
- It allows access only to the parent class methods and variables.

### Example:
````java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog(); // Upcasting
        a.sound(); // Calls Dog's sound() due to runtime polymorphism
    }
}
`````

---

## Downcasting

* Downcasting is converting a parent class reference back to a child class reference.
* It requires explicit casting.
* It may throw `ClassCastException` if the object is not actually of the child type.

### Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();  // Upcasting
        Dog d = (Dog) a;       // Downcasting
        d.bark();              // Child-specific method
    }
}
```

---

# 10. Difference Between Association, Aggregation, and Composition

## Association

* Association represents a general relationship between two classes.
* Both classes can exist independently.

### Example:

```java
class Teacher {
    String name;
    Teacher(String name) {
        this.name = name;
    }
}

class Student {
    String name;
    Student(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Teacher t = new Teacher("Mr. John");
        Student s = new Student("Anshuman");
        System.out.println(t.name + " teaches " + s.name);
    }
}
```

---

## Aggregation

* Aggregation is a "Has-a" relationship.
* The child object can exist independently of the parent object.
* It is a weaker form of association.

### Example:

```java
class Book {
    String title;
    Book(String title) {
        this.title = title;
    }
}

class Library {
    Book book;
    Library(Book book) {
        this.book = book;
    }
}

public class Main {
    public static void main(String[] args) {
        Book b = new Book("Java Basics");
        Library lib = new Library(b);
        System.out.println("Library has a book: " + lib.book.title);
    }
}
```

---

## Composition

* Composition is a stronger form of aggregation.
* The child object cannot exist without the parent object.
* If the parent is destroyed, the child is also destroyed.

### Example:

```java
class Room {
    String name;
    Room(String name) {
        this.name = name;
    }
}

class House {
    Room room;
    House(String roomName) {
        this.room = new Room(roomName);
    }
}

public class Main {
    public static void main(String[] args) {
        House h = new House("Living Room");
        System.out.println("House has a room: " + h.room.name);
    }
}
```

---

# 11. Scanner Class in Java

* Scanner is a utility class in the `java.util` package.
* It is used to take input from the user.
* It can read different types of input such as `int`, `double`, `String`, etc.

### Example:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        System.out.println("Hello " + name + ", you are " + age + " years old.");

        sc.close();
    }
}
```

---

# 12. Arrays in Java

* An array is a collection of elements of the same data type.
* Arrays are stored in contiguous memory locations.
* The index of an array starts from 0.
* Once created, the size of an array is fixed.

## Syntax

```java
dataType[] arrayName = new dataType[size];
```

---

## Example (1D Array)

```java
public class Main {
    public static void main(String[] args) {
        int[] numbers = new int[5];   // array of size 5
        numbers[0] = 10;
        numbers[1] = 20;
        numbers[2] = 30;

        System.out.println("Array elements:");
        for(int i=0; i<numbers.length; i++) {
            System.out.println(numbers[i]);
        }
    }
}
```

---

## Example (2D Array)

```java
public class Main {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println("2D Array elements:");
        for(int i=0; i<matrix.length; i++) {
            for(int j=0; j<matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

---

## Key Points

* Arrays can be single-dimensional or multi-dimensional.
* Size of the array is fixed once declared.
* Useful for storing multiple values under one variable.

---
## Integer Literals
Integer literals in Java are numeric values representing whole numbers without any fractional or exponential part. They are types of literals used to assign fixed values directly in the source code. Integer literals can be expressed in four types based on different number systems:

(i) Decimal literals (Base 10): Digits from 0 to 9; e.g., int x = 101;

(ii) Octal literals (Base 8): Digits from 0 to 7, prefixed with 0; e.g., int x = 0146;

(iii) Hexadecimal literals (Base 16): Digits 0-9 and letters a-f (case-insensitive), prefixed with 0x or 0X; e.g., int x = 0xFace;

(iv) Binary literals (Base 2): Digits 0 and 1, prefixed with 0b or 0B (available from Java 7 onwards); e.g., int x = 0b1111;

---

## Sum of Array
```java
// Java code to calculate the sum of an array
public class SumOfArray {
    public static void main(String[] args) {
        int[] arr = {5, 10, 15, 20, 25};
        int sum = 0;
        for (int num : arr) {
            sum += num;
        }
        System.out.println("Sum of array elements: " + sum);
    }
}
```

--- 
 ## Maximum Element in Array
 ```java
 // Java code to find the maximum element in an array
public class MaxOfArray {
    public static void main(String[] args) {
        int[] arr = {5, 10, 15, 20, 25};
        int max = arr[0];
        for (int num : arr) {
            if (num > max) {
                max = num;
            }
        }
        System.out.println("Maximum element in the array: " + max);
    }
}
```
