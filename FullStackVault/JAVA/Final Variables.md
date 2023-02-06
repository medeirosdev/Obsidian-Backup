## Final Variables
[[Java]]
If you don't want others (or yourself) to overwrite existing values, use the `final` keyword (this will declare the variable as "final" or "constant", which means unchangeable and read-only):

### Example

```java
final int myNum = 15;
myNum = 20;  // will generate an error: cannot assign a value to a final variable
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_variables_final)

---

## Other Types

A demonstration of how to declare variables of other types:

### Example

```java
int myNum = 5;
float myFloatNum = 5.99f;
char myLetter = 'D';
boolean myBool = true;
String myText = "Hello";
```

## Declare Many Variables

To declare more than one variable of the **same type**, you can use a comma-separated list:

### Example

Instead of writing:

```java
int x = 5;
int y = 6;
int z = 50;
System.out.println(x + y + z);
```

You can simply write:

```java
int x = 5, y = 6, z = 50;
System.out.println(x + y + z);
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_variables5)

---

## One Value to Multiple Variables

You can also assign the **same value** to multiple variables in one line:

### Example

```java
int x, y, z;
x = y = z = 50;
System.out.println(x + y + z);
```
