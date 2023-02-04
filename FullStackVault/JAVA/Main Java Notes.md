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
- 