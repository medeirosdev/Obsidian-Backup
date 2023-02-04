## Java Break

You have already seen the `break` statement used in an earlier chapter of this tutorial. It was used to "jump out" of a `switch` statement.

The `break` statement can also be used to jump out of a **loop**.

This example stops the loop when i is equal to 4:

### Example

```java
for (int i = 0; i < 10; i++) {
  if (i == 4) {
    break;
  }
  System.out.println(i);
}
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_break)

---

## Java Continue

The `continue` statement breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

This example skips the value of 4:

### Example

```java
for (int i = 0; i < 10; i++) {
  if (i == 4) {
    continue;
  }
  System.out.println(i);
}
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_continue)

---

---

## Break and Continue in While Loop

You can also use `break` and `continue` in while loops:

### Break Example

```java
int i = 0;
while (i < 10) {
  System.out.println(i);
  i++;
  if (i == 4) {
    break;
  }
}
 
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_break_while)

### Continue Example

```java
int i = 0;
while (i < 10) {
  if (i == 4) {
    i++;
    continue;
  }
  System.out.println(i);
  i++;
}
```