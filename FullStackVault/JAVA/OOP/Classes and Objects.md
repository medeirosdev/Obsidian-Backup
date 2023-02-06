## Java Classes/Objects
[[OOP]]
Java is an object-oriented programming language.

Everything in Java is associated with classes and objects, along with its attributes and methods. For example: in real life, a car is an object. The car has **attributes**, such as weight and color, and **methods**, such as drive and brake.

A Class is like an object constructor, or a "blueprint" for creating objects.

---

## Create a Class

To create a class, use the keyword `class`:

### Main.java

Create a class named "`Main`" with a variable x:

```java
public class Main {
  int x = 5;
}
```

Remember from the [Java Syntax chapter](https://www.w3schools.com/java/java_syntax.asp) that a class should always start with an uppercase first letter, and that the name of the java file should match the class name.

---

## Create an Object

In Java, an object is created from a class. We have already created the class named `Main`, so now we can use this to create objects.

To create an object of `Main`, specify the class name, followed by the object name, and use the keyword `new`:

### Example

Create an object called "`myObj`" and print the value of x:

```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_class)

---

---

## Multiple Objects

You can create multiple objects of one class:

### Example

Create two objects of `Main`:

```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj1 = new Main();  // Object 1
    Main myObj2 = new Main();  // Object 2
    System.out.println(myObj1.x);
    System.out.println(myObj2.x);
  }
}
 
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_class_multi_obj)

---

## Using Multiple Classes

You can also create an object of a class and access it in another class. This is often used for better organization of classes (one class has all the attributes and methods, while the other class holds the `main()` method (code to be executed)).

Remember that the name of the java file should match the class name. In this example, we have created two files in the same directory/folder:

-   Main.java
-   Second.java

#### Main.java

```java
public class Main {
  int x = 5;
}
```

#### Second.java

```java
class Second {
  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

When both files have been compiled:

C:\Users\_Your Name_>javac Main.java  
C:\Users\_Your Name_>javac Second.java

Run the Second.java file:

C:\Users\_Your Name_>java Second

And the output will be:

`5`