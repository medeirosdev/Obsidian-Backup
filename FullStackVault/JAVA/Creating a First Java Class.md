The first step you need to know is that the [[Java]] code you are writing is saved in plain text files. In this tutorial, your application will be written in a single text file. Larger applications may require thousands of such files.

Java is an object-oriented language. [[Orientação a Objeto]] If this technical term does not mean anything to you, do not worry, all you need to remember at this point is that all the code you write must be held in a Java class.

A Java class is created by a special declaration in a text file. Just copy the following code and paste it in your text editor. Congratulation! You have created your first Java class!

```
public class MyFirstClass {
}

```
The name of this Java class is `MyFirstClass`. __You need to save this text in a file named `MyFirstClass.java`.__ A Java class must be saved in a file that has the same name as your class with the extension `.java`. This is mandatory and is in fact very convenient because you do not need to open a file to know what class is written in it.

You can give this class any name as long as it does not start with a number. There is a convention though: the name of a Java class starts with a capital letter. This is not mandatory but all Java developers follow this convention. When you become a seasoned Java developer, seeing a class that does not follow this convention will look weird to you.

If you are following this example to the letter, you should save the `MyFirstClass` class in a text file called `MyFirstClass.java`.

Just a word of warning: you should be using a plain text editor to create and save this file. Using a word processor will not work.

## Preparing the Compilation of your First Class 

Compiling is the second step you need to follow after the creation of your first class. It consists of transforming the Java code you wrote in your `MyFirstClass.java` file into another format that can be executed. The result of this transformation will be stored in another file created by the compiler. The name of this file will be `MyFirstClass.class`.

So far the only tool you have been using is a plain text editor. Compiling this class requires a compiler; something you may not have on your computer. Fortunately, you can download this compiler and use it for free. Let me guide you through this process.

As of now, downloading "Java" means downloading the Java Development Kit, also known as the JDK. The JDK contains many tools and among them are the ones you will be using to compile and run a Java application. It is officially distributed by the OpenJDK project and by Oracle.

You may have heard about some other elements, also called "Java".

The JRE stands for Java Runtime Environment. It is a subset of the JDK that is not distributed by the OpenJDK or Oracle anymore. It only contained the tools needed to run a Java application. You cannot compile your code with the tools provided in the JRE.

You may also have heard about J2EE, Java EE or Jakarta EE. All these acronyms refer to the Java Enterprise Edition. It is a set of tools and libraries to create enterprise-class applications. Java EE is different from the JDK and is outside the scope of this tutorial. You do not need Java EE to compile and run the simple application we are creating in this tutorial.

## Compiling your First Class
Once you have properly set up your JDK; the `JAVA_HOME` variable and the `PATH` variable, you are ready to compile your first class.

All the commands you will be typing now should be typed in the same prompt as the one you used to set up these two variables.

### Compiling and Running Your First Java Program

Whether you followed the Windows, the Linux or the macOS path, the remaining is the same.

1.  Change to the directory where you saved your first class `MyFirstClass.java`. You can check that you are in the right directory by typing `dir`. It will show you the files you have in this directory. You should see your `MyFirstClass.java` file.
2.  Check that your compiler is accessible from this directory by typing the following. This command is the same whether you are on Windows or Linux.

```shell
> java -version
```

Copy

It should tell you which version of the `javac` you are currently using. If it gives you an error message then you need to check your `JAVA_HOME` and `PATH` variables as there is most probably something wrong with them.

3.  Now you are all set to compile your first code. You can type the following.

```shell
> javac MyFirstClass.java
```

Copy

Two things may happen at this point. You may have error messages telling you that the compiler cannot compile your code because of errors in your Java code. You will need to fix them before being able to move on.

If the compiler remains silent and does not complain about anything: congratulations! It means that your Java code has been properly compiled. Checking the content of the directory again should show a new file in it: `MyFirstClass.class`


## Adding Code to Your Class to Run it

So far your [[Class]] is empty; there is no executable code in it. If you were able to compile it properly then you can advance to the next step and execute some code.

Just open your `MyFirstClass.java` file and copy the following code in it.

```java
public class MyFirstClass {

    public static void main(String... args) {
        System.out.println("Hello, World!");
    }
}
```

Copy

As you may know, there is a long-standing tradition in computer science, which is to write a program that prints "Hello, World!" on the console of your application. So let us do that!

There is technical code in this class that may not be very clear to you. Do not worry; all you need to do is to [[compile]] it following the steps described in the previous section.

Make sure that the compiler created the `MyFirstClass.class` for you. To run it, all you need to type is the following command:

```shell
> java MyFirstClass
```

Copy

This should print _Hello, World!_ on the console. If this is the case: congratulations! You have been able to run your first Java program!

## Running the Hello World Program as a Single File Application

Starting with Java SE 11, you can run a Java application without going through the compilation step, as long as the program is written in a single file. This is the case of this simple _Hello, World!_ application.

You can just type the following:

```shell
> java MyFirstClass.java
```

Copy

And it will print the _Hello, World!_ message on the console.