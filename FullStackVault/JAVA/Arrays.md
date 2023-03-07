[[Java]]
## Java Arrays

Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

To declare an array, define the variable type with **square brackets**:

```java
String[] cars;
```

We have now declared a variable that holds an array of strings. To insert values to it, you can place the values in a comma-separated list, inside curly braces:

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
```

To create an array of integers, you could write:

```java
int[] myNum = {10, 20, 30, 40};
```

---

## Access the Elements of an Array

You can access an array element by referring to the index number.

This statement accesses the value of the first element in cars:

### Example

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
System.out.println(cars[0]);
// Outputs Volvo
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_array)

**Note:** Array indexes start with 0: [0] is the first element. [1] is the second element, etc.

---

## Change an Array Element

To change the value of a specific element, refer to the index number:

### Example

```java
cars[0] = "Opel";
```

### Example

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
cars[0] = "Opel";
System.out.println(cars[0]);
// Now outputs Opel instead of Volvo
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_array_change)

---

## Array Length

To find out how many elements an array has, use the `length` property:

### Example

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
System.out.println(cars.length);
// Outputs 4
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_array_length)