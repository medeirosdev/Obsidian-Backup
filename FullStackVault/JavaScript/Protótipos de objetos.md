[[JS]]
Protótipos são o mecanismo pelo qual objetos JavaScript herdam recursos uns dos outros. Neste artigo, explicamos como as cadeias de protótipos funcionam e observamos como a propriedade prototype pode ser usada para adicionar métodos aos construtores existentes.
## Uma linguagem baseada em protótipos?

O JavaScript é frequentemente descrito como uma **linguagem baseada em protótipos** — para fornecer herança, os objetos podem ter um **objeto de protótipo**, que atua como um objeto de modelo do qual herda métodos e propriedades. O objeto de protótipo de um objeto também pode ter um objeto de protótipo, do qual herda métodos e propriedades, e assim por diante. Isso geralmente é chamado de **cadeia de protótipos** e explica por que objetos diferentes têm propriedades e métodos definidos em outros objetos disponíveis para eles.

Bem, para ser exato, as propriedades e os métodos são definidos na propriedade `prototype` nas funções construtoras dos Objetos, não nas próprias instâncias do objeto.

Em JavaScript, é feito um link entre a instância do objeto e seu protótipo (sua propriedade  `__proto__`, que é derivada da propriedade `prototype` no construtor), e as propriedades e os métodos são encontrados percorrendo a cadeia de protótipos.


**Note:** É importante entender que há uma distinção entre o protótipo de um objeto (que está disponível por meio de `[Object.getPrototypeOf(obj)], ou por meio da propriedade `__proto__) e a propriedade `prototype` em funções construtoras. O primeiro é a propriedade em cada instância e o último é a propriedade no construtor. Ou seja, `Object.getPrototypeOf(new Foobar())` refere-se ao mesmo objeto que `Foobar.prototype`.

## Noções básicas sobre objetos de protótipo

Aqui voltaremos ao exemplo em que terminamos de escrever nosso construtor `Person()` — carregamos o exemplo em seu navegador.a
Neste exemplo, definimos uma função construtora, assim:

```
function Person(first, last, age, gender, interests) {

  // property and method definitions
  this.first = first;
  this.last = last;
//...
}
```

Nós criamos então uma instância de objeto como esta:

```
var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);
```

Se você digitar "`person1.`" em seu console JavaScript, você deve ver o navegador tentar concluir automaticamente isso com os nomes de membros disponíveis neste objeto:![[Pasted image 20220418132306.png]]
Nesta lista, você verá os membros definidos no construtor de `person1`'s constructor — `Person()` — `name`, `age`, `gender`, `interests`, `bio`, e `greeting`. No entanto, você também verá alguns outros membros — `watch`, `valueOf`, etc — estes estão definidos no objeto de protótipo do `Person()`, que é `[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)`.

O que acontece se você chamar um método em `person1`, que é realmente definido em `Object`? Por exemplo:

```
person1.valueOf()
```

Este método — `[Object.valueOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf)` é herdado por  `person1` porque seu construtor é `Person()`, e o protótipo de `Person()` é  `Object()`. `valueOf()` retorna o valor do objeto em que é chamado — experimente e veja! Nesse caso, o que acontece é:

-   O navegador verifica inicialmente se o objeto  `person1` tem um método  `valueOf()` disponível nele, conforme definido em seu construtor, `Person()`.
-   Se não tem, então o navegador verifica se o objeto (`Object()`) de protótipo do construtor `Person()` tem um método `valueOf()` disponível, então ele é chamado, e tudo está bem!