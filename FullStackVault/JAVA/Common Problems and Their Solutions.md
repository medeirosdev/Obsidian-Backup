### Compiler Problems
[[Java]]
#### Common Error Messages on Microsoft Windows Systems

```shell
javac is not recognized as an internal or external command, operable program or batch file
```

Copy

If you receive this error, Windows cannot find the compiler [`javac`](https://docs.oracle.com/en/java/javase/19/docs/specs/man/javac.html).

Here's one way to tell Windows where to find `javac`. Suppose you installed the JDK in `C:\jdk19`. At the prompt you would type the following command and press Enter:

```shell
C:\jdk19\bin\javac HelloWorldApp.java
```

Copy

If you choose this option, you'll have to precede your `javac` and `java` commands with `C:\jdk19\bin\` each time you compile or run a program. To avoid this extra typing, consult the section Updating the `PATH` variable in the JDK 19 installation instructions.

```shell
Class names, HelloWorldApp, are only accepted if annotation processing is explicitly requested
```

Copy

If you receive this error, you forgot to include the `.java` suffix when compiling the program. Remember, the command is `javac HelloWorldApp.java` not `javac HelloWorldApp`.

#### Common Error Messages on UNIX Systems

```shell
javac: Command not found
```

Copy

If you receive this error, UNIX cannot find the compiler, [`javac`](https://docs.oracle.com/en/java/javase/19/docs/specs/man/javac.html).

Here's one way to tell UNIX where to find javac. Suppose you installed the JDK in `/usr/local/jdk19`. At the prompt you would type the following command and press Return:

```shell
/usr/local/jdk19/javac HelloWorldApp.java
```

Copy

Note: If you choose this option, each time you compile or run a program, you'll have to precede your `javac` and `java` commands with `/usr/local/jdk19/`. To avoid this extra typing, you could add this information to your `PATH` variable. The steps for doing so will vary depending on which shell you are currently running.

```shell
Class names, 'HelloWorldApp', are only accepted if annotation processing is explicitly requested
```

Copy

If you receive this error, you forgot to include the `.java` suffix when compiling the program. Remember, the command is `javac HelloWorldApp.java` not `javac HelloWorldApp`.

#### Syntax Errors (All Platforms)

If you mistype part of a program, the compiler may issue a syntax error. The message usually displays the type of the error, the line number where the error was detected, the code on that line, and the position of the error within the code. Here's an error caused by omitting a semicolon (`;`) at the end of a statement:

```shell
Testing.java:8: error: ';' expected
count++
^
1 error
```

Copy

If you see any compiler errors, then your program did not successfully compile, and the compiler did not create a `.class` file. Carefully verify the program, fix any errors that you detect, and try again.

#### Semantic Errors

In addition to verifying that your program is syntactically correct, the compiler checks for other basic correctness. For example, the compiler warns you each time you use a variable that has not been initialized:

```shell
Testing.java:8: error: variable count might not have been initialized
count++;
^
Testing.java:9: error: variable count might not have been initialized
System.out.println("Input has " + count + " chars.");
^
2 errors
```

Copy

Again, your program did not successfully compile, and the compiler did not create a `.class` file. Fix the error and try again.

### Runtime Problems

#### Error Messages on Microsoft Windows Systems

If you receive this error, `java` cannot find your bytecode file, `HelloWorldApp.class`.

One of the places `java` tries to find your `.class` file is your current directory. So if your `.class` file is in `C:\java`, you should change your current directory to that. To change your directory, type the following command at the prompt and press Enter:

```shell
cd c:\java
```

Copy

The prompt should change to `C:\java>`. If you enter `dir` at the prompt, you should see your `.java` and `.class` files. Now enter `java HelloWorldApp` again.

If you still have problems, you might have to change your `CLASSPATH` variable. To see if this is necessary, try clobbering the classpath with the following command.

```shell
set CLASSPATH=
```

Copy

Now enter `java HelloWorldApp` again. If the program works now, you'll have to change your `CLASSPATH` variable. To set this variable, consult the _Updating the PATH variable_ section in the JDK installation instructions. The `CLASSPATH` variable is set in the same manner.

```shell
Could not find or load main class HelloWorldApp.class
```

Copy

A common mistake made by beginner programmers is to try and run the `java` launcher on the `.class` file that was created by the compiler. For example, you'll get this error if you try to run your program with `java HelloWorldApp.class` instead of `java HelloWorldApp`. Remember, the argument is the name of the class that you want to use, not the filename.

```shell
Exception in thread "main" java.lang.NoSuchMethodError: main
```

Copy

The Java VM requires that the class you execute with it have a `main` method at which to begin execution of your application. A Closer Look at the [Adding Code to Your Class to Run it](https://dev.java/learn/getting-started/#anchor_7) section discusses the main method in detail.

#### Error Messages on UNIX Systems

```shell
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp
```

Copy

If you receive this error, `java` cannot find your bytecode file, `HelloWorldApp.class`.

One of the places java tries to find your bytecode file is your current directory. So, for example, if your bytecode file is in `/home/jdoe/java`, you should change your current directory to that. To change your directory, type the following command at the prompt and press Return:

```shell
cd /home/jdoe/java
```

Copy

If you enter `pwd` at the prompt, you should see `/home/jdoe/java`. If you enter `ls` at the prompt, you should see your `.java` and `.class` files. Now enter `java HelloWorldApp` again.

If you still have problems, you might have to change your `CLASSPATH` environment variable. To see if this is necessary, try clobbering the classpath with the following command.

```shell
unset CLASSPATH
```

Copy

Now enter `java HelloWorldApp` again. If the program works now, you'll have to change your `CLASSPATH` variable in the same manner as the `PATH` variable above.

```shell
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp/class
```

Copy

A common mistake made by beginner programmers is to try and run the java launcher on the `.class` file that was created by the compiler. For example, you'll get this error if you try to run your program with `java HelloWorldApp.class` instead of `java HelloWorldApp`. Remember, the argument is the name of the class that you want to use, not the filename.

```shell
Exception in thread "main" java.lang.NoSuchMethodError: main
```

Copy

The Java VM requires that the class you execute with it have a main method at which to begin execution of your application. A Closer Look at the [Adding Code to Your Class to Run it](https://dev.java/learn/getting-started/#anchor_7) section discusses the main method in detail.