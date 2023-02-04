[[Java]]

### Example

```java
Math.max(5, 10);
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_max)

---

## Math.min(_x,y_)

The `Math.min(_x_,_y_)` method can be used to find the lowest value of _x_ and _y_:

### Example

```java
Math.min(5, 10);
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_min)

---

## Math.sqrt(_x_)

The `Math.sqrt(_x_)` method returns the square root of _x_:

### Example

```java
Math.sqrt(64);
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_sqrt)

---

---

## Math.abs(_x_)

The `Math.abs(_x_)` method returns the absolute (positive) value of _x_:

### Example

```java
Math.abs(-4.7);
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_abs)

---

## Random Numbers

`Math.random()` returns a random number between 0.0 (inclusive), and 1.0 (exclusive):

### Example

```java
Math.random();
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_random)

To get more control over the random number, for example, if you only want a random number between 0 and 100, you can use the following formula:

### Example

```java
int randomNum = (int)(Math.random() * 101);  // 0 to 100
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_math_random2)