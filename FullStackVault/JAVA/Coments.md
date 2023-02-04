[[Java]]
## Java Comments

Comments can be used to explain Java code, and to make it more readable. It can also be used to prevent execution when testing alternative code.

---

## Single-line Comments

Single-line comments start with two forward slashes (`//`).

Any text between `//` and the end of the line is ignored by Java (will not be executed).

This example uses a single-line comment before a line of code:

### Example

```java
// This is a comment
System.out.println("Hello World");
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_single_comment)

This example uses a single-line comment at the end of a line of code:

### Example

```java
System.out.println("Hello World"); // This is a comment
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_single_comment_end)

---

---

## Java Multi-line Comments

Multi-line comments start with `/*` and ends with `*/`.

Any text between `/*` and `*/` will be ignored by Java.

This example uses a multi-line comment (a comment block) to explain the code:

### Example

```java
/* The code below will print the words Hello World
to the screen, and it is amazing */
System.out.println("Hello World");
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_multi_comment)

#### Single or multi-line comments?

It is up to you which you want to use. Normally, we use `//` for short comments, and `/* */` for longer.