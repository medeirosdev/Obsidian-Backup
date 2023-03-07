## Modifiers
[[OOP]]
By now, you are quite familiar with the `public` keyword that appears in almost all of our examples:

```java
public class Main
```

The `public` keyword is an **access modifier**, meaning that it is used to set the access level for classes, attributes, methods and constructors.

We divide modifiers into two groups:

-   **Access Modifiers** - controls the access level
-   **Non-Access Modifiers** - do not control access level, but provides other functionality

---

## Access Modifiers
![[Pasted image 20230204105518.png]]
![[Pasted image 20230204105530.png]]
![[Pasted image 20230204105540.png]]
## Final

If you don't want the ability to override existing attribute values, declare attributes as `final`:

### Example

```java
public class Main {
  final int x = 10;
  final double PI = 3.14;

  public static void main(String[] args) {
    Main myObj = new Main();
    myObj.x = 50; // will generate an error: cannot assign a value to a final variable
    myObj.PI = 25; // will generate an error: cannot assign a value to a final variable
    System.out.println(myObj.x);
  }
}
 
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_mod_final2)

---

## Static

A `static` method means that it can be accessed without creating an object of the class, unlike `public`:

### Example

An example to demonstrate the differences between `static` and `public` methods:

```java
public class Main {
  // Static method
  static void myStaticMethod() {
    System.out.println("Static methods can be called without creating objects");
  }

  // Public method
  public void myPublicMethod() {
    System.out.println("Public methods must be called by creating objects");
  }

  // Main method
  public static void main(String[ ] args) {
    myStaticMethod(); // Call the static method
    // myPublicMethod(); This would output an error

    Main myObj = new Main(); // Create an object of Main
    myObj.myPublicMethod(); // Call the public method
  }
}
 
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_class_method_static)

---

## Abstract

An `abstract` method belongs to an `abstract` class, and it does not have a body. The body is provided by the subclass:

### Example

```java
// Code from filename: Main.java
// abstract classabstract class Main {
  public String fname = "John";
  public int age = 24;
  public abstract void study(); // abstract method
}

// Subclass (inherit from Main)
class Student extends Main {
  public int graduationYear = 2018;
  public void study() { // the body of the abstract method is provided here
    System.out.println("Studying all day long");
  }
}
// End code from filename: Main.java

// Code from filename: Second.java
class Second {
  public static void main(String[] args) {
    // create an object of the Student class (which inherits attributes and methods from Main)
    Student myObj = new Student();

    System.out.println("Name: " + myObj.fname);
    System.out.println("Age: " + myObj.age);
    System.out.println("Graduation Year: " + myObj.graduationYear);
    myObj.study(); // call abstract method  }
}
```
