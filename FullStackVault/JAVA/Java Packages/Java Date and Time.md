[[Java Packages]]
Java does not have a built-in Date class, but we can import the `java.time` package to work with the date and time API. The package includes many date and time classes. For example:
![[Pasted image 20230204131149.png]]
## Display Current Date

To display the current date, import the `java.time.LocalDate` class, and use its `now()` method:

### Example

```java
import java.time.LocalDate; // import the LocalDate class

public class Main {
  public static void main(String[] args) {
    LocalDate myObj = LocalDate.now(); // Create a date object
    System.out.println(myObj); // Display the current date
  }
}
```

The output will be:

`2023-02-04`

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_date_localdate)

---

## Display Current Time

To display the current time (hour, minute, second, and nanoseconds), import the `java.time.LocalTime` class, and use its `now()` method:

### Example

```java
import java.time.LocalTime; // import the LocalTime class

public class Main {
  public static void main(String[] args) {
    LocalTime myObj = LocalTime.now();
    System.out.println(myObj);
  }
}
```

The output will be:

`13:10:26.203818`

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_date_localtime)

---

---

## Display Current Date and Time

To display the current date and time, import the `java.time.LocalDateTime` class, and use its `now()` method:

### Example

```java
import java.time.LocalDateTime; // import the LocalDateTime class

public class Main {
  public static void main(String[] args) {
    LocalDateTime myObj = LocalDateTime.now();
    System.out.println(myObj);
  }
}
```

The output will be:

`2023-02-04T13:10:26.203127`

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_date_localdatetime)

---

## Formatting Date and Time

The "T" in the example above is used to separate the date from the time. You can use the `DateTimeFormatter` class with the `ofPattern()` method in the same package to format or parse date-time objects. The following example will remove both the "T" and nanoseconds from the date-time:

### Example

```java
import java.time.LocalDateTime; // Import the LocalDateTime class
import java.time.format.DateTimeFormatter; // Import the DateTimeFormatter class

public class Main {
  public static void main(String[] args) {
    LocalDateTime myDateObj = LocalDateTime.now();
    System.out.println("Before formatting: " + myDateObj);
    DateTimeFormatter myFormatObj = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm:ss");

    String formattedDate = myDateObj.format(myFormatObj);
    System.out.println("After formatting: " + formattedDate);
  }
}
```

The output will be:

`Before Formatting: 2023-02-04T13:10:26.203480   After Formatting: 04-02-2023 13:10:26`

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_date_format)

The `ofPattern()` method accepts all sorts of values, if you want to display the date and time in a different format. For example:
![[Pasted image 20230204131235.png]]
