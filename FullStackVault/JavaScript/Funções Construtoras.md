# Funções Construtoras
[[JS]]
As funções construtoras em [JavaScript](https://blog.cod3r.com.br/tag/javascript/) são como as classes do Java, diferenciando apenas pela sintaxe. Em questão de funcionamento, tanto funções contrutoras no JavaScript quanto Classes no Java têm a mesma utilidade: **servir de molde para a criação de objetos.**

Para construir objetos, funções construtoras precisam ser instanciadas pelo **operador new**. O **this** dentro delas se referencia ao **objeto criado a partir delas.**

## É preciso um return para ser considerado uma função construtora?

Normalmente, os construtores não têm um return. Isso acontece porque tudo o que lhes é informado é simplesmente passado ao **this**.

Por outro lado, havendo um return os comportamentos esperados são dois:

-   Se o return for chamado com um objeto, ele irá retornar no lugar do **this**.

-   Se o return for vazio ou seguido de um valor primitivo, ele será ignorado.

**Qual a diferença entre retornar um objeto literal e um criado por função construtora?**  
Ao se criar objetos usando funções construtoras em JavaScript, estes seguirão o molde definido pela função, recebendo seus atributos e métodos.

Para criar objetos literais, é necessário um controle para garantir que os objetos tenham as mesmas propriedades. Uma solução é criá-los com uma função _factory_ (“fábrica”), que garante o retorno de objetos literais com características explícitas. As funções factory são semelhantes às construtoras, mas sem o uso do new.