## Java Iterator
[[Java Packages]]
An `Iterator` is an object that can be used to loop through collections, like [ArrayList](https://www.w3schools.com/java/java_arraylist.asp) and [HashSet](https://www.w3schools.com/java/java_hashset.asp). It is called an "iterator" because "iterating" is the technical term for looping.

To use an Iterator, you must import it from the `java.util` package.

---

## Getting an Iterator

The `iterator()` method can be used to get an `Iterator` for any collection:

### Example

```java
// Import the ArrayList class and the Iterator class
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {

    // Make a collection
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");

    // Get the iterator
    Iterator<String> it = cars.iterator();

    // Print the first item
    System.out.println(it.next());
  }
}
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_iterator)

---

## Looping Through a Collection

To loop through a collection, use the `hasNext()` and `next()` methods of the `Iterator`:

### Example

```java
while(it.hasNext()) {
  System.out.println(it.next());
}
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_iterator_loop)

---

---

## Removing Items from a Collection

Iterators are designed to easily change the collections that they loop through. The `remove()` method can remove items from a collection while looping.

### Example

Use an iterator to remove numbers less than 10 from a collection:

```java
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {
    ArrayList<Integer> numbers = new ArrayList<Integer>();
    numbers.add(12);
    numbers.add(8);
    numbers.add(2);
    numbers.add(23);
    Iterator<Integer> it = numbers.iterator();
    while(it.hasNext()) {
      Integer i = it.next();
      if(i < 10) {
        it.remove();
      }
    }
    System.out.println(numbers);
  }
}
```

[Try it Yourself »](https://www.w3schools.com/java/tryjava.asp?filename=demo_iterator_remove)

**Note:** Trying to remove items using a **for loop** or a **for-each loop** would not work correctly because the collection is changing size at the same time that the code is trying to loop.