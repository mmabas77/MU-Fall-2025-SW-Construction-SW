# Software Construction - Lab 2: Java Collections, Arrays, Loops & Classes

**Mansoura University - Faculty of Computers and Information**  
**Course**: CS Software Construction (Grade 4)  

---

## 🎯 Lab Objectives

This lab builds upon fundamental Java concepts to explore:
- Understanding primitive vs object values and how Java manages memory
- Mastering loops (`for`, `while`) and iteration patterns
- Working with Arrays and understanding array indexing
- **Defining and using Classes and Objects (Object-Oriented Programming)**
- **Understanding References vs Values**
- **Working with Constructors and Methods**
- **Using the `static` keyword effectively**
- Distinguishing between mutating values and reassigning variables
- Working with immutable references using the `final` keyword
- Mastering Java Collections Framework (List, Set, Map)
- Applying debugging techniques and best practices
- Solving real-world programming problems

---

## 📋 Lab Structure

- **Part 0**: Good Programming Style
- **Part 1**: Loops and Iteration
- **Part 2**: Arrays
- **Part 3**: Debugging Techniques
- **Part 4**: Classes and Objects (OOP)
- **Part 5**: Primitive vs Object Values and References
- **Part 6**: The `static` Keyword
- **Part 7**: Mutation vs Reassignment
- **Part 8**: Immutable References with `final`
- **Part 9**: Java Collections Framework
- **Part 10**: Practice Projects

---

## 🎨 Part 0: Good Programming Style

### Rule #1: Use Meaningful Variable Names

```java
// ❌ BAD - Cryptic names
String a1;
int a2;
double b;

// ✅ GOOD - Descriptive names
String firstName;
String lastName;
int temperature;
double salary;
```

### Rule #2: Use Proper Indentation

```java
// ❌ BAD - No indentation
public static void main(String[] args) {
int x = 5;
x = x * x;
if (x > 20) {
System.out.println(x + " is greater than 20");
}
}

// ✅ GOOD - Proper indentation
public static void main(String[] args) {
    int x = 5;
    x = x * x;
    
    if (x > 20) {
        System.out.println(x + " is greater than 20");
    }
}
```

**Eclipse Tip**: Press `Ctrl+Shift+F` to auto-format your code!

### Rule #3: Use Whitespaces for Readability

```java
// ❌ BAD - Cramped
double cel=fahr*42.0/(13.0-7.0);

// ✅ GOOD - Breathing room
double cel = fahr * 42.0 / (13.0 - 7.0);
```

### Rule #4: Don't Duplicate Logic

```java
// ❌ BAD - Redundant tests
if (basePay < 8.0) {
    System.out.println("Error: Pay too low");
} else if (hours > 60) {
    System.out.println("Error: Too many hours");
} else if (basePay >= 8.0 && hours <= 60) {  // Redundant!
    // Calculate pay
}

// ✅ GOOD - Simple else
if (basePay < 8.0) {
    System.out.println("Error: Pay too low");
} else if (hours > 60) {
    System.out.println("Error: Too many hours");
} else {
    // Calculate pay - we know it's valid here!
}
```

### Rule #5: Always Use Curly Braces

```java
// ❌ DANGEROUS - Easy to make mistakes
for (int i = 0; i < 5; i++)
    System.out.println("Hi");
    System.out.println("Bye");  // This is NOT in the loop!

// ✅ GOOD - Clear intent
for (int i = 0; i < 5; i++) {
    System.out.println("Hi");
    System.out.println("Bye");
}
```

---

## 🔁 Part 1: Loops and Iteration

### Why Loops?

```java
// ❌ Without loops - repetitive and limited
System.out.println("Student #1");
System.out.println("Student #2");
System.out.println("Student #3");
// What if you want 200 students?

// ✅ With loops - flexible and scalable
for (int i = 1; i <= 200; i++) {
    System.out.println("Student #" + i);
}
```

### Exercise 1.1: The `while` Loop

**Syntax:**
```java
while (condition) {
    statements
}
```

**Example:**
```java
public class WhileExample {
    public static void main(String[] args) {
        int i = 0;
        while (i < 3) {
            System.out.println("Count: " + i);
            i = i + 1;  // CRITICAL: Must change i or loop runs forever!
        }
    }
}
```

### Exercise 1.2: The `for` Loop

**Syntax:**
```java
for (initialization; condition; update) {
    statements
}
```

**Example:**
```java
public class ForExample {
    public static void main(String[] args) {
        for (int i = 0; i < 3; i++) {
            System.out.println("Count: " + i);
        }
    }
}
```

### Exercise 1.3: Loop Control Statements

**`break` - Exit the loop immediately:**
```java
public class BreakExample {
    public static void main(String[] args) {
        for (int i = 0; i < 100; i++) {
            System.out.println("Number: " + i);
            if (i == 50) {
                break;  // Stop at 50
            }
        }
        System.out.println("Done!");
    }
}
```

**`continue` - Skip to next iteration:**
```java
public class ContinueExample {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {
            if (i == 5) {
                continue;  // Skip printing for i = 5
            }
            System.out.println("Number: " + i);
        }
    }
}
```

---

## 📊 Part 2: Arrays

### What is an Array?

An **array** is an indexed list of values of the **same type**.

```
Array: [5.0, 2.44, 9.01, 1.0, -9.5]
Index:  0    1     2     3     4
```

### Exercise 2.1: Creating and Using Arrays

```java
// Method 1: Declare size, then assign values
int[] values = new int[5];
values[0] = 12;
values[1] = 24;
values[2] = -23;
values[3] = 47;
values[4] = 100;

// Method 2: Initialize with values
int[] numbers = {12, 24, -23, 47, 100};

// Method 3: Variable size
int size = 10;
double[] data = new double[size];
```

### Exercise 2.2: Array Index vs Array Value ⚠️

**CRITICAL CONCEPT:**
```java
public class ArrayIndexVsValue {
    public static void main(String[] args) {
        int[] values = {99, 100, 101};
        
        System.out.println(values[0]);  // 99 (VALUE at index 0)
        System.out.println(0);          // 0 (just the number 0)
        
        // Visual representation:
        // Values:  99  100  101
        // Indexes:  0    1    2
    }
}
```

### Exercise 2.3: Common Array Algorithms

**Algorithm 1: Find Minimum Index**
```java
public class FindMinIndex {
    public static int getMinIndex(int[] values) {
        int minValue = Integer.MAX_VALUE;
        int minIndex = -1;
        
        for (int i = 0; i < values.length; i++) {
            if (values[i] < minValue) {
                minValue = values[i];
                minIndex = i;
            }
        }
        return minIndex;
    }
    
    public static void main(String[] args) {
        int[] times = {152, 148, 156, 145, 150};  // Marathon times
        int fastestRunner = getMinIndex(times);
        
        System.out.println("Fastest runner: #" + fastestRunner);
        System.out.println("Time: " + times[fastestRunner] + " minutes");
    }
}
```

**Algorithm 2: Find Second Minimum Index**
```java
public class FindSecondMin {
    public static int getMinIndex(int[] values) {
        int minValue = Integer.MAX_VALUE;
        int minIndex = -1;
        for (int i = 0; i < values.length; i++) {
            if (values[i] < minValue) {
                minValue = values[i];
                minIndex = i;
            }
        }
        return minIndex;
    }
    
    public static int getSecondMinIndex(int[] values) {
        int secondIdx = -1;
        int minIdx = getMinIndex(values);
        
        for (int i = 0; i < values.length; i++) {
            if (i == minIdx) {
                continue;  // Skip the minimum
            }
            
            if (secondIdx == -1 || values[i] < values[secondIdx]) {
                secondIdx = i;
            }
        }
        return secondIdx;
    }
}
```

---

## 🐛 Part 3: Debugging Techniques

### Technique 1: Strategic Print Statements

```java
public class DebugExample {
    public static int findMin(int[] vals) {
        int minVal = Integer.MAX_VALUE;
        
        System.out.println("Starting search...");
        
        for (int i = 0; i < vals.length; i++) {
            System.out.println("Checking index " + i + ": " + vals[i]);
            
            if (vals[i] < minVal) {
                System.out.println("  New minimum found!");
                minVal = vals[i];
            }
        }
        return minVal;
    }
}
```

### Technique 2: Format Your Code

**Remember: `Ctrl+Shift+F` in Eclipse auto-formats!**

---

## 🏗️ Part 4: Classes and Objects

### Why Object-Oriented Programming?

```java
// ❌ BAD - Managing 500 students with primitives
String nameAhmed;
int ageAhmed;
double gradeAhmed;

String nameFatima;
int ageFatima;
double gradeFatima;
// ... 498 more? Impractical!

// ✅ GOOD - Use a class
public class Student {
    String name;
    int age;
    double grade;
}

Student[] classroom = new Student[500];
```

### Exercise 4.1: Defining a Class

```java
public class Student {
    // FIELDS (data)
    String name;
    int age;
    double gpa;
    String major;
    int creditHours;
    
    // CONSTRUCTOR
    Student(String studentName, int studentAge, String studentMajor) {
        name = studentName;
        age = studentAge;
        major = studentMajor;
        gpa = 0.0;
        creditHours = 0;
    }
    
    // METHODS (behaviors)
    void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Major: " + major);
        System.out.println("GPA: " + gpa);
    }
    
    void updateGPA(double newGPA) {
        if (newGPA >= 0.0 && newGPA <= 4.0) {
            gpa = newGPA;
            System.out.println(name + "'s GPA updated to " + gpa);
        }
    }
    
    void enrollCourse(int credits) {
        creditHours += credits;
        System.out.println(name + " enrolled in " + credits + " credit hours");
    }
}
```

### Exercise 4.2: Creating Objects

```java
public class University {
    public static void main(String[] args) {
        // Create Student objects
        Student ahmed = new Student("Ahmed Ali", 20, "Computer Science");
        Student fatima = new Student("Fatima Hassan", 19, "Engineering");
        
        // Access fields
        System.out.println(ahmed.name);   // "Ahmed Ali"
        System.out.println(fatima.major); // "Engineering"
        
        // Call methods
        ahmed.displayInfo();
        ahmed.updateGPA(3.8);
        fatima.enrollCourse(15);
    }
}
```

---

## 🔗 Part 5: References vs Values

### How Java Stores Data

**Primitives** = Stored directly
```java
int x = 5;
int y = x;  // y gets a COPY
x = 10;

System.out.println(x);  // 10
System.out.println(y);  // 5 (unchanged)
```

**Objects** = Stored as references
```java
Student s1 = new Student("Ahmed", 20, "CS");
Student s2 = s1;  // s2 points to SAME object

s1.gpa = 3.8;

System.out.println(s1.gpa);  // 3.8
System.out.println(s2.gpa);  // 3.8 (same object!)
```

### Exercise 5.1: The == Operator

```java
Student s1 = new Student("Ahmed", 20, "CS");
Student s2 = new Student("Ahmed", 20, "CS");

System.out.println(s1 == s2);  // false! (different objects)

Student s3 = s1;
System.out.println(s1 == s3);  // true! (same object)
```

### Exercise 5.2: Method Parameters

```java
public class ReferenceTest {
    public static void modifyPrimitive(int x) {
        x = 99;  // Only changes local copy
    }
    
    public static void modifyObject(Student s) {
        s.gpa = 4.0;  // Modifies the actual object!
    }
    
    public static void main(String[] args) {
        int num = 5;
        modifyPrimitive(num);
        System.out.println(num);  // 5 (unchanged)
        
        Student ahmed = new Student("Ahmed", 20, "CS");
        modifyObject(ahmed);
        System.out.println(ahmed.gpa);  // 4.0 (changed!)
    }
}
```

---

## 🔒 Part 6: The `static` Keyword

### Static Fields (Shared by All Instances)

```java
public class Student {
    static int totalStudents = 0;  // SHARED by all
    String name;                    // UNIQUE to each
    
    Student(String studentName) {
        name = studentName;
        totalStudents++;
    }
}

public class TestStatic {
    public static void main(String[] args) {
        System.out.println(Student.totalStudents);  // 0
        
        Student s1 = new Student("Ahmed");
        System.out.println(Student.totalStudents);  // 1
        
        Student s2 = new Student("Fatima");
        System.out.println(Student.totalStudents);  // 2
        
        System.out.println(s1.totalStudents);  // 2
        System.out.println(s2.totalStudents);  // 2 (shared!)
    }
}
```

### Static Methods

```java
public class MathHelper {
    // Static method - can call without creating object
    static int add(int a, int b) {
        return a + b;
    }
}

public class Test {
    public static void main(String[] args) {
        int result = MathHelper.add(5, 3);  // No object needed!
        System.out.println(result);  // 8
    }
}
```

### Why is `main` static?

```java
public class Program {
    public static void main(String[] args) {
        // main is static because Java needs to call it
        // BEFORE any objects are created!
        System.out.println("Program started");
    }
}
```

---

## 🔄 Part 7: Mutation vs Reassignment

### Reassignment = Changing What Variable Points To

```java
int x = 5;
x = 10;  // REASSIGNMENT: x now points to 10
```

### Mutation = Changing Object Contents

```java
Student ahmed = new Student("Ahmed", 20, "CS");
ahmed.gpa = 3.8;  // MUTATION: changing object's state

// ahmed still points to same Student object
```

---

## 🔐 Part 8: The `final` Keyword

```java
public class FinalExample {
    public static void main(String[] args) {
        // final with primitive
        final int MAX_STUDENTS = 100;
        // MAX_STUDENTS = 200;  // ERROR!
        
        // final with array
        final int[] scores = {85, 90, 78};
        scores[0] = 95;  // ✅ OK: mutating contents
        // scores = new int[]{1, 2, 3};  // ❌ ERROR: reassignment
        
        // final with object
        final Student ahmed = new Student("Ahmed", 20, "CS");
        ahmed.gpa = 3.8;  // ✅ OK: mutating object
        // ahmed = new Student(...);  // ❌ ERROR: reassignment
    }
}
```

---

## 📦 Part 9: Java Collections

### Lists

```java
import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        List<String> courses = new ArrayList<>();
        
        courses.add("Math");
        courses.add("Physics");
        courses.add("Programming");
        
        System.out.println(courses.size());  // 3
        System.out.println(courses.get(0));  // "Math"
        
        for (String course : courses) {
            System.out.println(course);
        }
    }
}
```

### Sets

```java
import java.util.*;

public class SetExample {
    public static void main(String[] args) {
        Set<Integer> ids = new HashSet<>();
        
        ids.add(101);
        ids.add(102);
        ids.add(101);  // Duplicate - won't be added
        
        System.out.println(ids.size());  // 2, not 3!
        System.out.println(ids.contains(101));  // true
    }
}
```

### Maps

```java
import java.util.*;

public class MapExample {
    public static void main(String[] args) {
        Map<String, Double> grades = new HashMap<>();
        
        grades.put("Ahmed", 3.8);
        grades.put("Fatima", 3.9);
        grades.put("Omar", 3.7);
        
        System.out.println(grades.get("Ahmed"));  // 3.8
        
        for (Map.Entry<String, Double> entry : grades.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```

---

## 🚀 Practice Project: Student Management System

```java
import java.util.*;

public class Student {
    String name;
    int id;
    double gpa;
    
    Student(String name, int id, double gpa) {
        this.name = name;
        this.id = id;
        this.gpa = gpa;
    }
}

public class StudentManagementSystem {
    private List<Student> students;
    private Map<Integer, Student> studentMap;
    
    public StudentManagementSystem() {
        students = new ArrayList<>();
        studentMap = new HashMap<>();
    }
    
    public void addStudent(Student student) {
        students.add(student);
        studentMap.put(student.id, student);
        System.out.println("Added: " + student.name);
    }
    
    public Student findStudent(int id) {
        return studentMap.get(id);
    }
    
    public double getAverageGPA() {
        double sum = 0;
        for (Student student : students) {
            sum += student.gpa;
        }
        return sum / students.size();
    }
    
    public Student getTopStudent() {
        Student top = students.get(0);
        for (Student student : students) {
            if (student.gpa > top.gpa) {
                top = student;
            }
        }
        return top;
    }
    
    public void displayAll() {
        System.out.println("\n=== Student Report ===");
        System.out.println("Total students: " + students.size());
        for (Student student : students) {
            System.out.println(student.id + ": " + student.name + 
                             " (GPA: " + student.gpa + ")");
        }
        System.out.println("Average GPA: " + getAverageGPA());
        Student top = getTopStudent();
        System.out.println("Top student: " + top.name);
    }
    
    public static void main(String[] args) {
        StudentManagementSystem sms = new StudentManagementSystem();
        
        sms.addStudent(new Student("Ahmed Ali", 101, 3.8));
        sms.addStudent(new Student("Fatima Hassan", 102, 3.9));
        sms.addStudent(new Student("Omar Ibrahim", 103, 3.7));
        sms.addStudent(new Student("Mona Khalil", 104, 3.95));
        
        sms.displayAll();
        
        Student found = sms.findStudent(102);
        if (found != null) {
            System.out.println("\nFound student: " + found.name);
        }
    }
}
```

---

## ✅ Lab Checklist

### Part 1-3: Basics
- [ ] Write `for` and `while` loops correctly
- [ ] Create and manipulate arrays
- [ ] Implement array algorithms (find min, find second min)
- [ ] Use debugging techniques

### Part 4-6: OOP
- [ ] Define classes with fields, constructors, and methods
- [ ] Create and use objects
- [ ] Understand references vs values
- [ ] Use `static` keyword appropriately

### Part 7-9: Advanced
- [ ] Differentiate mutation vs reassignment
- [ ] Use `final` keyword correctly
- [ ] Work with Lists, Sets, and Maps
- [ ] Choose appropriate collection types

### Projects
- [ ] Complete Student Management System
- [ ] Test thoroughly with edge cases
- [ ] Apply good coding style

---

## 📝 Assignment: Library System

Create classes `Book` and `Library` where:
- Books can be checked out and returned
- Library tracks all books
- Library displays available books

**Requirements:**
1. `Book` class with title, author, and checkout status
2. `Library` class with collection of books
3. Methods to add, checkout, and return books
4. Proper error handling

---

**Happy Coding! 🎉**
