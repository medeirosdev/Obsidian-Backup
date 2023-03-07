
[[JS]]
Vamos engatar a próxima marcha e começar a pensar sobre as operações úteis que podemos fazer em strings com métodos embutidos, como encontrar o comprimento de um string, unir e dividir sequências de caracteres, substituindo um caracter em uma string por outro, e muito mais.

## Strings como objetos

Como dissemos antes e diremos novamente — _tudo_ é um objeto em JavaScript. Quando você cria um string, usando por exemplo

```
var string = 'This is my string';
```

sua variável torna-se uma instância do objeto string e, como resultado, tem um grande número de propriedades e métodos diponíveis para ela. Você pode ver isso se você for na página do objeto [`String`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String) e olhar para baixo na lista do lado da página!

**Agora, antes de seu cérebro começar a derreter, não se preocupe!** Você não precisa saber sobre a maioria deles no início da sua jornada de aprendizado

### Descobrindo o comprimento de uma string

Essa é fácil  — você simplesmente usa a propriedade [`length`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/length). Tente digitar as linhas a seguir:

```
var browserType = 'mozilla';
browserType.length;
```

Isso deve retornar o número 7, porque "mozilla"  tem 7 caracteres. Isso é útil por vários motivos; por exemplo, você pode querer encontrar os comprimentos de uma série de nomes para que você possa exibi-los em ordem de comprimento, ou deixar um usuário saber que um nome de usuário que ele informou em um campo de formulário é muito longo se este for maior do que um certo comprimento.
### Recuperando um caractere de string específico

Nota complementar: você pode retornar qualquer caractere dentro de uma string usando a **notação colchete** - isso significa que você inclui colchetes (`[]`) no final do nome da variável. Dentro dos colchetes, você inclui o número do caractere que deseja retornar, por exemplo, para recuperar a primeira letra, faça o seguinte:

```
browserType[0];
```

Computadores contam a partir de 0, não 1! Para recuperar o último caractere de _qualquer_ string, nós podemos usar a linha a seguir, combinando essa técnica com a propriedade `length` que vimos anteriormente:

```
browserType[browserType.length-1];
```

O comprimento de "mozilla" é 7, mas porque a contagem começa de 0, a posição do caractere é 6, daí precisamos usar `length-1`. Você pode usar isso para, por exemplo, encontrar a primeira letra de uma série de strings e ordená-los alfabeticamente.

### Encontrando uma substring dentro de uma string e extraindo-a

1.  Às vezes você quer saber se uma string menor está presente dentro de uma maior (geralmente dizemos _se uma substring está presente dentro de uma string_). Isso pode ser feito usando o método [`indexOf ()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf), que leva um único [parameter (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Parameter "Currently only available in English (US)") - a substring que deseja procurar. Experimente isso:
    
    ```
    browserType.indexOf('zilla');
    ```
    

-   Isso nos dá o resultado 2, porque a substring "zilla" se inicia na posição 2 (0, 1, 2  — então, 3 caraceteres) dentro de "mozilla". Esse código poderia ser usado para filtrar cadeias de caracteres. Por exemplo, podemos ter uma lista de endereços da web e apenas queremos imprimir aqueles que contenham "mozilla".
-   Isso pode ser feito de outro jeito, que é possivelmente mais eficaz. Experimente isso:
    
    ```
    browserType.indexOf('vanilla');
    ```
    

Isso deve lhe dar um resultado `-1` — isso é retornado quando a substring, neste caso 'vanilla', não é encontrada na string principal.  
  
Você pode usar isso para encontrar todas as instâncias de strings que **não contém** a substring 'mozilla', ou **contém**, se você usar o operador de negação, conforme mostrado abaixo. Você poderia fazer algo assim:

```
if(browserType.indexOf('mozilla') !== -1) {
  // faz coisas com a string
}
```

-   Quando você sabe onde uma substring começa dentro de uma string e você sabe em qual caractere você deseja que ela termine, [`slice ()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String/slice) pode ser usado para extrair isto. Tente o seguinte:
    
    ```
    browserType.slice(0,3);
    ```
    

Isso retorna "moz" — o primeiro parâmetro é a posição do caractere a partir da qual será iniciada a extração, e o segundo parâmetro é a posição seguinte do último caractere a ser extraído. Então, a fatia ocorre da primeira posição, até a última posição, mas não incluindo. Você também pode dizer que o segundo parâmetro é igual ao comprimento da string que está sendo retornada.