[[JS]]
Cria uma instância JavaScript de **`Date`** que representa um único momento no tempo. Objetos Date são baseados no valor de tempo que é o número de milisegundos desde 1º de Janeiro de 1970 (UTC).

##  Construtor

```
new Date();
new Date(valor);
new Date(dataString);
new Date(ano, mês, dia, hora, minuto, segundo, milissegundo);
```
### Parâmetros para o constructor Date

Nota: Quando Date for chamado como um construtor com mais de um argumento, se os valores forem maiores do que seu limite lógico (e.g. se 13 for fornecido como um valor para mês ou 70 for o valor para minuto), o valor adjacente será ajustado. E.g. new Date(2013, 13, 1) é equivalente a new Date(2014, 1, 1), ambos criam uma data para 2014-02-01 (note que o mês começa em 0). Similarmente para outros valores: new Date(2013, 2, 1, 0, 70) é equivalente a new Date(2013, 2, 1, 1, 10), pois ambos criam uma data para 2013-03-01T01:10:00.

_`value`_

Um valor inteiro representando o número de milisegundos desde 1 de Janeiro de 1970 00:00:00 UTC (Era Unix ou Marco Zero).

_`dataString`_

Um valor do tipo String que representa uma data. A string deverá estar uma formato reconhecido pelo método [`Date.parse()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/parse) ([IETF-compliant RFC 2822 timestamps](https://tools.ietf.org/html/rfc2822#page-14) e também uma [versão da ISO8601](https://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15)).

_`year`_

Um valor inteiro que representa o ano. Valores de 0 a 99 correspondem aos anos de 1900 a 1999. Veja o [exemplo abaixo](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date#two digit years).

_`month`_

Um valor inteiro que representa o mês, começando com 0 para Janeiro até 11 para Dezembro.

_`day`_

Um valor inteiro que representa o dia do mês.

_`hour`_

Um valor inteiro que representa a hora do dia.

_`minute`_

Um valor inteiro que representa o segmento de um minuto de tempo.

_`second`_

Um valor inteiro que representa o segmento de segundo do tempo.

_`millisecond`_

Um valor inteiro que representa o segmento de milisegundo do tempo.

### Definições

-   Se nenhum argumento for fornecido, o construtor criará um objeto JavaScript Date com a data e hora corrente de acordo com as configurações do sistema.
-   Se ao menos 2 argumentos forem fornecidos, os argumentos ausentes serão configurados como 1 (se o dia estiver ausente) ou 0 para todos os outros.
-   A data do JavaScript é baseada no valor de tempo em milisegundos desde a meia noite de 01 de Janeiro de 1970, UTC. Um dia corresponde a 86.400,000 milisegundos. O intervalo do objeto Date no JavaScript é de -100.000,000 dias a 100.000,000 dias relativo a 01 de Janeiro de 1970, UTC.
-   O objeto Date no JavaScript tem um comportamento uniforme nas plataformas. O valor do tempo pode ser transmitido entre sistemas para representar o mesmo instante no tempo e se for usado para criar um objeto de data local, ele refletirá o tempo local equivalente.
-   O objeto Date JavaScript suporta vários métodos UTC (universal), assim como métodos de tempo locais. UTC, também conhecido como Tempo Médio de Greenwich (Greenwich Mean Time, GMT), refere-se ao tempo como definido pelo Padrão de Tempo Mundial (World Time Standard). O tempo local é o tempo conhecido pelo computador onde o JavaScript é executado.
-   Invocar o objeto Date no JavaScript como uma função (i.e., sem o operador [new](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)) retornatá uma string representando a data e hora corrente.


## Propriedades
[`Date.prototype` 
Permite adicionar propriedades a um objeto javaScript Date.

Date.length

O valor de `Date.length` é 7. Esse é o número de argumentos manipulados pelo construtor
## [Métodos](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date#methods "Permalink to Métodos")

[`Date.now()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/now)

Retorna o valor numérico correspondente ao tempo corrente - o número de milisegundos passados desde 1 de Janeiro de 1970 00:00:00 UTC.

[`Date.parse()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/parse)

Analisa uma string que representa uma data e retorna o número de milisegundos desde 1 de Janeiro, 1970, 00:00:00, hora local.

[`Date.UTC()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date/UTC)

Aceita os mesmos parâmetros como a forma mais longa do construtor (i.e. 2 até 7) e retorna o número de milisegundos desde 1 de Janeiro, 1970, 00:00:00 UTC.

## [Instâncias JavaScript de `Date`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date#date_instances "Permalink to Instâncias JavaScript de Date") 

Todas as instâncias `Date` são herdadas de [`Date.prototype` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date "Currently only available in English (US)"). O objeto protótipo do construtor `Date` pode ser modificado para afetar todas as instâncias de `Date`.