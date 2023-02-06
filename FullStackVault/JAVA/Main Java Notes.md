[[Java]]

- Os nomes das Classes são MUITO importantes, as Iniciais de cada palavra devem ser maiúsculas!
- exemplo:
```java
public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}
```
- Veja que a classe HelloWorld tem a propriedade dita acima
- a public class classe {} deve ser o mesmo nome do arquivo, ou seja, classe.java
- Podemos ter [[Múltiplas Classes no mesmo Arquivo]]
 - If the name you choose consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word. The names `gearRatio` and `currentGear` are prime examples of this convention. If your variable stores a constant value, such as static final int NUM_GEARS = 6, the convention changes slightly, capitalizing every letter and separating subsequent words with the underscore character. By convention, the underscore character is never used elsewhere.
- Every line of code that runs in Java must be inside a `class`. In our example, we named the class **Main**. A class should always start with an uppercase first letter.
- **Note:** Java is case-sensitive: "MyClass" and "myclass" has different meaning.
- Any code inside the `main()` method will be executed. Don't worry about the keywords before and after main. You will get to know them bit by bit while reading this tutorial.For now, just remember that every Java program has a `class` name which must match the filename, and that every program must contain the `main()` method.
- Ver [[System.out.println]]
- `System` is a built-in Java class that contains useful members, such as `out`, which is short for "output". The `println()` method, short for "print line", is used to print a value to the screen (or a file).
- Ver [[Coments]]
- The general rules for naming variables are:
-   Names can contain letters, digits, underscores, and dollar signs
-   Names must begin with a letter
-   Names should start with a lowercase letter and it cannot contain whitespace
-   Names can also begin with $ and _ (but we will not use it in this tutorial)
-   Names are case sensitive ("myVar" and "myvar" are different variables)
-   Reserved words (like Java keywords, such as `int` or `boolean`) cannot be used as names
- You will often see Java programs that have either `static` or `public` attributes and methods. In the example above, we created a `static` method, which means that it can be accessed without creating an object of the class, unlike `public`, which can only be accessed by objects:
-  the modifier `final` -Attributes and methods cannot be overridden/modified 
- Data **abstraction** is the process of hiding certain details and showing only essential information to the user.   Abstraction can be achieved with either **abstract classes** or [**interfaces**](https://www.w3schools.com/java/java_interface.asp) (which you will learn more about in the next chapter). The `abstract` keyword is a non-access modifier, used for classes and methods: -> **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class). -> **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).
- Another way to achieve [abstraction](https://www.w3schools.com/java/java_abstract.asp) in Java, is with interfaces. An `interface` is a completely "**abstract class**" that is used to group related methods with empty bodies: To access the interface methods, the interface must be "implemented" (kinda like inherited) by another class with the `implements` keyword (instead of `extends`). The body of the interface method is provided by the "implement" class:
- #### Why And When To Use Interfaces?

1) To achieve security - hide certain details and only show the important details of an object (interface).

2) Java does not support "multiple inheritance" (a class can only inherit from one superclass). However, it can be achieved with interfaces, because the class can **implement** multiple interfaces. **Note:** To implement multiple interfaces, separate them with a comma (see example below).
- The difference between a built-in array and an `ArrayList` in Java, is that the size of an array cannot be modified (if you want to add or remove elements to/from an array, you have to create a new one). While elements can be added and removed from an `ArrayList` whenever you want. The syntax is also slightly different:
- The `LinkedList` class is a collection which can contain many objects of the same type, just like the `ArrayList`. The `LinkedList` class has all of the same methods as the `ArrayList` class because they both implement the `List` interface. This means that you can add items, change items, remove items and clear the list in the same way. However, while the `ArrayList` class and the `LinkedList` class can be used in the same way, they are built very differently.
### How the ArrayList works

The `ArrayList` class has a regular array inside it. When an element is added, it is placed into the array. If the array is not big enough, a new, larger array is created to replace the old one and the old one is removed.

### How the LinkedList works

The `LinkedList` stores its items in "containers." The list has a link to the first container and each container has a link to the next container in the list. To add an element to the list, the element is placed into a new container and that container is linked to one of the other containers in the list.
### When To Use
Use an `ArrayList` for storing and accessing data, and `LinkedList` to manipulate data.

