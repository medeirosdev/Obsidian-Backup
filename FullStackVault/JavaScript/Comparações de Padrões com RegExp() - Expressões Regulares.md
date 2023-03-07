[[JS]]
# Expressões Regulares


Expressões regulares são padrões utilizados para selecionar combinações de caracteres em uma string. Em JavaScript, expressões regulares também são objetos. Elas podem ser utilizadas com os métodos [`exec`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec "exec") e [`test`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test "test") do objeto [`RegExp`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp "RegExp"), e com os métodos [`match`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match "match"), [`replace`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace "en-US/docs/JavaScript/Reference/Global_Objects/String/replace"), [`search`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/search "search"), e [`split`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split "split") do objeto [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String "String"). Este capítulo descreve o uso de expressões regulares em JavaScript.

## Criando uma Expressão Regular

Há duas maneiras de construir uma expressão regular:

Usando uma expressão literal, que consiste em um padrão fechado entre barras, como o exemplo a seguir:

```
const re = /ab+c/;
```

As expressões regulares na forma literal são compiladas quando o script é carregado. Esta forma de construção possui melhor performace quando a expressão regular utilizada é uma constante, ou seja, não muda durante a execução.

Ou chamando o construtor do objeto `[RegExp]'

```
let re = new RegExp("ab+c");
```

Usando o construtor, a compilação da expressão regular é realizada em tempo de execução. Use o construtor quando souber que o padrão da expressão regular irá mudar ou quando o padrão for desconhecido, oriundo de outra fonte, uma entrada de usuário por exemplo.

Nota: Se você já está familiarizado com as formas de uma expressão regular, também pode ler o [resumo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet)  para uma rápida pesquisa de um padrão específico.

## [](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions#escrevendo_um_padrão_de_expressão_regular "Permalink to Escrevendo um padrão de expressão regular")Escrevendo um padrão de expressão regular

Um padrão de expressão é composto por um conjunto de caracteres simples, como `/abc/`, ou uma combinação de caracteres simples e especiais, como `/ab*c/` ou `/Capitulo (\d+)\.\d*/`. O último exemplo contém parênteses, que são usados como um mecanismo de armazenamento. A correspondência feita por essa parte da expressão é armazenada para uso posterior, como descrito em: [Using Parenthesized Substring Matches](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions#using_parenthesized_substring_matches).

### [Uso de Padrões Simples](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions#uso_de_padrões_simples "Permalink to Uso de Padrões Simples")

Padrões simples são construídos utilizando os caracteres que você deseja encontrar correspondências diretas. Por exemplo, o padrão `/abc/` encontra combinações de caracteres em strings apenas quando os caracteres 'abc' forem encontrados juntos e na ordem especificada. Esse padrão será encontrado com sucesso nas strings "Olá, você conhece o abc?" e "Os mais recentes aviões evoluíram do slabcraft.". Em ambos os casos, a correspondência estará no subconjunto 'abc'. Porém, o padrão não será encontrado no texto "Grab crab" pois apesar de conter os mesmos caractes do padrão 'ab c', estes não aparecem na ordem especificada.

### [Uso dos Caracteres Especiais](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions#uso_dos_caracteres_especiais "Permalink to Uso dos Caracteres Especiais")

Quando for necessário buscar algo além de uma correspondência direta, como encontrar uma ou mais ocorrências da letra 'b', ou encontrar espaços em branco, será necessário adicionar caracteres especiais ao padrão. Por exemplo, para encontrar uma única correspondência de 'a' seguido de nenhum ou mais 'b's seguido de 'c', o padrão a utilizar seria `/ab*c/.` O caractere `*` seleciona zero ou mais ocorrências do item que o precede. Se aplicada ao texto 'cbbabbbbcdebc', essa expressão regular encontraria o subconjunto grifado no texto.

A tabela abaixo fornece uma lista completa dos caracteres especiais que podem ser utilizados nas expressões regulares, com sua respectiva descrição. Para testar os exemplos de expressão regular você pode usar o [regExr](http://regexr.com/).
