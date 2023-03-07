File handling is an important part of any application.

Java has several methods for creating, reading, updating, and deleting files.

---

## Java File Handling

The `File` class from the `java.io` package, allows us to work with files.

To use the `File` class, create an object of the class, and specify the filename or directory name:

### Example

```java
import java.io.File;  // Import the File class

File myObj = new File("filename.txt"); // Specify the filename
```

If you don't know what a package is, read our [Java Packages Tutorial](https://www.w3schools.com/java/java_packages.asp).

The `File` class has many useful methods for creating and getting information about files. For example:
![[Pasted image 20230206195217.png]]
