 ## Encapsulation
[[OOP]]
The meaning of **Encapsulation**, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:

-   declare class variables/attributes as `private`
-   provide public **get** and **set** methods to access and update the value of a `private` variable

---

## Get and Set

You learned from the previous chapter that `private` variables can only be accessed within the same class (an outside class has no access to it). However, it is possible to access them if we provide public **get** and **set** methods.

The `get` method returns the variable value, and the `set` method sets the value.

Syntax for both is that they start with either `get` or `set`, followed by the name of the variable, with the first letter in upper case:

### Example

```java
public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String newName) {
    this.name = newName;
  }
}
 
 
```

#### Example explained

The `get` method returns the value of the variable `name`.

The `set` method takes a parameter (`newName`) and assigns it to the `name` variable. The `this` keyword is used to refer to the current object.

However, as the `name` variable is declared as `private`, we **cannot** access it from outside this class:

### Example

```java
public class Main {
  public static void main(String[] args) {
    Person myObj = new Person();
    myObj.name = "John";  // error
    System.out.println(myObj.name); // error 
  }
}
```

[Run Example »](https://www.w3schools.com/java/showjava_classes.asp?filename=demo_getset_error)

If the variable was declared as `public`, we would expect the following output:

`John`

However, as we try to access a `private` variable, we get an error:

`MyClass.java:4: error: name has private access in Person       myObj.name = "John";            ^   MyClass.java:5: error: name has private access in Person       System.out.println(myObj.name);                     ^   2 errors`

Instead, we use the `getName()` and `setName()` methods to access and update the variable:

### Example

```java
public class Main {
  public static void main(String[] args) {
    Person myObj = new Person();
    myObj.setName("John"); // Set the value of the name variable to "John"
    System.out.println(myObj.getName());
  }
}

// Outputs "John"
 
 
```

[Try it Yourself »](https://www.w3schools.com/java/showjava_classes.asp?filename=demo_getset)

---

## Why Encapsulation?

-   Better control of class attributes and methods
-   Class attributes can be made **read-only** (if you only use the `get` method), or **write-only** (if you only use the `set` method)
-   Flexible: the programmer can change one part of the code without affecting other parts
-   Increased security of data