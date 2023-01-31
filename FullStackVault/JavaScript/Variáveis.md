[[JS]]
No JavaScript, instruções são chamadas de [declaração](https://developer.mozilla.org/pt-BR/docs/Glossary/Statement) e são separadas por um ponto e vírgula (;). Espaços, tabulação e uma nova linha são chamados de espaços em branco. O código fonte dos scripts em JavaScript são lidos da esquerda para a direita e são convertidos em uma sequência de elementos de entrada como simbolos, caracteres de controle, terminadores de linha, comentários ou espaço em branco. ECMAScript também define determinadas palavras-chave e literais, e tem regras para inserção automática de ponto e vírgula ([ASI](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Lexical_grammar#automatic_semicolon_insertion)) para terminar as declarações. No entanto, recomenda-se sempre adicionar ponto e vírgula no final de suas declarações; isso evitará alguns imprevistos. Para obter mais informações, consulte a referência detalhada sobre a [gramática léxica](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Lexical_grammar) do JavaScript.
## Declarações

Existem três tipos de declarações em JavaScript.

[`var`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var)

Declara uma variável, opcionalmente, inicializando-a com um valor.

Experimental [`let`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/let)

Declara uma variável local de escopo do bloco, opcionalmente, inicializando-a com um valor.

Experimental [`const`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/const)

Declara uma constante de escopo de bloco, apenas de leitura.

### Variáveis

Você usa variáveis como nomes simbólicos para os valores em sua aplicação. O nome das variáveis, chamados de [identificadores](https://developer.mozilla.org/pt-BR/docs/Glossary/Identifier), obedecem determinadas regras.

Um identificador JavaScript deve começar com uma letra, underline (`_`), ou cifrão (`$`); os caracteres subsequentes podem também ser números (0-9). Devido JavaScript ser case-sensitive, letras incluem caracteres de "A" a "Z" (maiúsculos) e caracteres de "a" a "z" (minúsculos).
### Declarando variáveis

Você pode declarar uma variável de três formas:

-   Com a palavra chave [`var`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var). Por exemplo, var `x = 42`. Esta sintaxe pode ser usada para declarar tanto variáveis locais como variáveis globais.
-   Por simples adição de valor. Por exemplo, `x = 42`. Isso declara uma variável global. Essa declaração gera um aviso de advertência no JavaScript. Você não deve usar essa variante.
-   Com a palavra chave [`let`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/let). Por exemplo, `let y = 13`. Essa sintaxe pode ser usada para declarar uma variável local de escopo de bloco. Veja [escopo de variável](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_Types#Variable_scope) abaixo.

### Classificando variáveis

Uma variável declarada usando a declaração `var` ou `let` sem especificar o valor inicial tem o valor  [`undefined`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/undefined).

Uma tentativa de acessar uma variável não declarada resultará no lançamento de uma exceção [`ReferenceError`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError)
### Escopo de variável

Quando você declara uma váriavel fora de qualquer função, ela é chamada de variável _global_, porque está disponível para qualquer outro código no documento atual. Quando você declara uma variável dentro de uma função, é chamada de variável _local_,  pois ela está disponível somente dentro dessa função.

JavaScript antes do ECMAScript 6 não possuía escopo de [declaração de bloco](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Control_flow_and_error_handling#block_statement); pelo contrário, uma variável declarada dentro de um bloco de uma _função_ é uma variável local (ou contexto _global_) do bloco que está inserido a função. Por exemplo o código a seguir exibirá 5, porque o escopo de `x` está na função (ou contexto global) no qual `x` é declarado, não o bloco, que neste caso é a declaração `if`.
### Variáveis Globais
Variáveis globais são propriedades do _objeto global_. Em páginas web o objeto global é a [`window`](https://developer.mozilla.org/pt-BR/docs/Web/API/Window), assim você pode configurar e acessar variáveis globais utilizando a sintaxe `window.variavel.` 

Consequentemente, você pode acessar variáveis globais declaradas em uma janela ou frame ou frame de outra janela. Por exemplo, se uma variável chamada phoneNumber é declarada em um documento, você pode consultar esta variável de um frame como `parent.phoneNumber`.

### [Constantes](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types#constantes "Permalink to Constantes")

Você pode criar uma constante apenas de leitura por meio da palavra-chave [`const`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/const). A sintaxe de um identificador de uma constante é semelhante ao identificador de uma variável: deve começar com uma letra, sublinhado ou cifrão e pode conter caractere alfabético, numérico ou sublinhado.

```
const PI = 3.14;
```

Uma constante não pode alterar seu valor por meio de uma atribuição ou ser declarada novamente enquanto o script está em execução. Deve ser inicializada com um valor.

As regras de escopo para as constantes são as mesmas para as váriaveis `let` de escopo de bloco. Se a palavra-chave `const` for omitida, presume-se que o identificador represente uma variável.

Você não pode declarar uma constante com o mesmo nome de uma função ou variável que estão no mesmo escopo.
## [Estrutura de dados e tipos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types#data_structures_and_types "Permalink to Estrutura de dados e tipos")

### [Tipos de dados](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types#tipos_de_dados "Permalink to Tipos de dados")

O mais recente padrão ECMAScript define sete tipos de dados:

-   Seis tipos de dados são os chamados [primitivos](https://developer.mozilla.org/pt-BR/docs/Glossary/Primitive):
    -   [Boolean](https://developer.mozilla.org/pt-BR/docs/Glossary/Boolean). `true` e `false`.
    -   [null](https://developer.mozilla.org/pt-BR/docs/Glossary/Null). Uma palavra-chave que indica valor nulo. Devido JavaScript ser case-sensitive, `null` não é o mesmo que `Null`, `NULL`, ou ainda outra variação.
    -   [undefined](https://developer.mozilla.org/pt-BR/docs/Glossary/undefined). Uma propriedade superior cujo valor é indefinido.
    -   [Number](https://developer.mozilla.org/pt-BR/docs/Glossary/Number). `42` ou `3.14159`.
    -   [String](https://developer.mozilla.org/pt-BR/docs/Glossary/String). "Howdy"
    -   [Symbol](https://developer.mozilla.org/pt-BR/docs/Glossary/Symbol) (novo em ECMAScript 6). Um tipo de dado cuja as instâncias são únicas e imutáveis.
-   e [Object](https://developer.mozilla.org/pt-BR/docs/Glossary/Object)



### var

Considerando o conceito de hoisting, vamos fazer um pequeno teste usando uma variável declarada com `var` antes mesmo dela ter sido declarada:

```

void function(){ 
    console.log(mensagem); 
}();
var mensagem;
```

No caso da palavra-chave `var`, além da variável ser içada (_hoisting_) ela é automaticamente inicializada com o valor undefined (caso não seja atribuído nenhum outro valor).

Ok, mas qual é o impacto que temos quando fazemos esse tipo de uso?

Imagine que nosso código contenha muitas linhas e que sua complexidade não seja algo tão trivial de compreender.

Às vezes, queremos declarar variáveis que serão utilizadas apenas dentro de um pequeno trecho do nosso código. Ter que lidar com o escopo de função das variáveis declaradas com `var` (escopo abrangente) pode confundir a cabeça até de programadores mais experientes.

Sabendo das "complicações" que as variáveis declaradas com `var` podem causar, o que podemos fazer para evitá-las?

### let

Foi pensando em trazer o escopo de bloco (tão conhecido em outras linguagens) que o ECMAScript 6 destinou-se a disponibilizar essa mesma flexibilidade (e uniformidade) para a linguagem.

Através da palavra-chave `let` podemos declarar variáveis com escopo de bloco. Vamos ver:

```

var exibeMensagem = function() {
     if(true) { 
         var escopoFuncao = 'Caelum'; 
         let escopoBloco = 'Alura';

        console.log(escopoBloco); // Alura 
    } 
    console.log(escopoFuncao); // Caelum 
    console.log(escopoBloco); 
}
```

Qual será a saída do código acima?

```

exibeMensagem(); // Imprime 'Alura', 'Caelum' e dá um erro
```

Veja que quando tentamos acessar uma variável que foi declarada através da palavra-chave `let` fora do seu escopo, o erro _Uncaught ReferenceError: escopoBloco is not defined_ foi apresentado.

Portanto, podemos usar tranquilamente o `let`, pois o escopo de bloco estará garantido.

### const

Embora o `let` garanta o escopo, ainda assim, existe a possibilidade de declararmos uma variável com `let` e ela ser _undefined_. Por exemplo:

```

void function(){ 
    let mensagem; 
    console.log(mensagem); // Imprime undefined 
}();
```

Supondo que temos uma variável que queremos garantir sua inicialização com um determinado valor, como podemos fazer isso no JavaScript sem causar uma inicialização _default_ com _undefined_?

Para termos esse tipo de comportamento em uma variável no JavaScript, podemos declarar constantes por meio da palavra-chave `const`. Vamos dar uma olhada no exemplo:

```

void function(){ 
    const mensagem = 'Alura'; 
    console.log(mensagem); // Alura
    mensagem = 'Caelum'; 
}();
```

O código acima gera um _Uncaught TypeError: Assignment to constant variable_, pois o comportamento fundamental de uma constante é que uma vez atribuído um valor a ela, este não pode ser alterado.

Assim como as variáveis declaradas com a palavra-chave `let`, constantes também tem escopo de bloco.