# Function.prototype.call()
[[JS]]
## Introdução

O método `**call()**` invoca uma função com um dado valor `this`  e argumentos passados individualmente.

**Nota:** Apesar de a sintaxe desta função ser quase idêntica à de [`apply()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/apply), a principal diferença é que `call()` aceita uma **lista de argumentos**, enquanto `apply()` aceita **um único array de argumentos.**

## Sintaxe

```
fun.call(thisArg[, arg1[, arg2[, ...]]])
```

### Parâmetros

`thisArg`

O valor de  `this`  proveu a chamada para _`fun`_. Note que `this` pode não ser o valor atual visto pelo método: se esse método é uma função em [non-strict mode (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode "Currently only available in English (US)") code, [`null`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/null) e [`undefined`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/undefined) serão reescritos com o objeto global, e valores primitivos serão encaixados.

`arg1, arg2, ...`

Argumentos para  o objeto.

## [Descrição](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/call#descrição "Permalink to Descrição")

Você pode atribuir um objeto `this` diferente quando executar uma função existente. `this` refere-se ao objeto atual, o objeto em execução. Com `call`, você pode escrever um método uma vez e então herdá-lo em outro objeto, sem ter que reescrever o método para o novo objeto.

## [Exemplos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/call#exemplos "Permalink to Exemplos")

### [Exemplo: Usando `call` para encadear construtores para um objeto](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/call#exemplo_usando_call_para_encadear_construtores_para_um_objeto "Permalink to Exemplo: Usando call para encadear construtores para um objeto")

Você pode usar `call` para encadear construtores para um objeto, similar ao  Java. No seguinte exemplo, o construtor do  objeto `Product` é definido com dois parâmetros, `name` e `price`. Outras duas funções `Food` e `Toy` executam `Product` passando `this,` `name` e `price`. O Produto inicializa as propriedades `name` e `price`,  ambos definem o `category`.

```
function Product(name, price) {
  this.name = name;
  this.price = price;

  if (price < 0) {
    throw RangeError('Cannot create product ' +
                      this.name + ' with a negative price');
  }

  return this;
}

function Food(name, price) {
  Product.call(this, name, price);
  this.category = 'food';
}

Food.prototype = Object.create(Product.prototype);

function Toy(name, price) {
  Product.call(this, name, price);
  this.category = 'toy';
}

Toy.prototype = Object.create(Product.prototype);

var cheese = new Food('feta', 5);
var fun = new Toy('robot', 40);
```

### [Exemplo: Usando o `call` para chamar funções anônimas](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/call#exemplo_usando_o_call_para_chamar_funções_anônimas "Permalink to Exemplo: Usando o call para chamar funções anônimas")

Neste exemplo, criamos uma função anônima que usa o `call` para executá-lo em todos os objetos em um array(vetor). O principal propósito da função anônima aqui é adicionar uma função print para todo o objeto, que está disponível para imprimir o índice correto do objeto no array. Não foi necessário passar o valor do objeto como `this` , mas isso foi feito apenas para explicação.

```
var animais = [
  { especie: 'Lion', nome: 'King' },
  { especie: 'Whale', nome: 'Fail' }
];

for (var i = 0; i < animais.length; i++) {
  (function(i) {
    this.print = function() {
      console.log('#' + i + ' ' + this.especie
                  + ': ' + this.nome);
    }
    this.print();
  }).call(animais[i], i);
}
```

### [Usando `call` para chamar a função e especificar o contexto de 'this'](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/call#usando_call_para_chamar_a_função_e_especificar_o_contexto_de_'this' "Permalink to Usando call para chamar a função e especificar o contexto de 'this'")

No exemplo abaixo, quando vamos chamar a apresentação, o valor de this será associado ao objeto i.  
 

```
function apresentacao() {
  var resposta = [this.pessoa, 'é um excelente', this.funcao].join(' ');
  console.log(resposta);
}

var i = {
  pessoa: 'Douglas Crockford', funcao: 'Desenvolvedor Javascript'
};

apresentacao.call(i); // Douglas Crockford é um excelente Desenvolvedor Javascript
```