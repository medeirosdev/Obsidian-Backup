[[JS]]
## Linguagem orientada a objeto

## Programação orientada a objetos e programação estruturada
Como a maioria das atividades que fazemos no dia a dia, programar também possui modos diferentes de se fazer. Esses modos são chamados de **paradigmas de programação** e, entre eles, estão a **programação orientada a objetos** (POO) e a programação estruturada.

Na programação estruturada, um programa é composto por três tipos básicos de estruturas:

-   sequências: são os comandos a serem executados
-   condições: sequências que só devem ser executadas se uma condição for satisfeita (exemplos: `if-else`, `switch` e comandos parecidos)
-   repetições: sequências que devem ser executadas repetidamente até uma condição for satisfeita (`for`, `while`, `do-while` etc)

Essas estruturas são usadas para processar a entrada do programa, alterando os dados até que a saída esperada seja gerada. Até aí, nada que a programação orientada a objetos não faça, também, certo?

A diferença principal é que na programação estruturada, um programa é tipicamente escrito em uma única rotina (ou função) podendo, é claro, ser quebrado em subrotinas. Mas o fluxo do programa continua o mesmo, como se pudéssemos copiar e colar o código das subrotinas diretamente nas rotinas que as chamam, de tal forma que, no final, só haja uma grande rotina que execute todo o programa.
![[Pasted image 20220417220153.png]]

Além disso, o acesso às variáveis não possuem muitas restrições na programação estruturada. Em linguagens fortemente baseadas nesse paradigma, restringir o acesso à uma variável se limita a dizer se ela é visível ou não dentro de uma função (ou módulo, como no uso da palavra-chave `static`, na linguagem C), mas não se consegue dizer de forma nativa que uma variável pode ser acessada por apenas algumas rotinas do programa. O contorno para situações como essas envolve práticas de programação danosas ao desenvolvimento do sistema, como o uso excessivo de variáveis globais. Vale lembrar que variáveis globais são usadas tipicamente para manter estados no programa, marcando em qual parte dele a execução se encontra.

A **programação orientada a objetos** surgiu como uma alternativa a essas características da programação estruturada. O intuito da sua criação também foi o de aproximar o manuseio das estruturas de um programa ao manuseio das coisas do mundo real, daí o nome "objeto" como uma algo genérico, que pode representar qualquer coisa tangível.

Esse novo paradigma se baseia principalmente em dois conceitos chave: [[Classes e Objetos]]  Todos os outros conceitos, igualmente importantes, são construídos em cima desses dois.

