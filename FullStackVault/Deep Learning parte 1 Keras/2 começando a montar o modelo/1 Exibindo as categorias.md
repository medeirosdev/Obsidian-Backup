Conseguimos visualizar nossa primeira imagem de treino, mas poderíamos dar um título, colocar um nome para ela. Inclusive, se olharmos, parece que é algo que se usa no pé, um tênis, uma bota, não sei. Vamos ver como é esse nome. Daremos um espaço e, para colocarmos um título para a nossa imagem, escreveremos plt.title, abrindo e fechando parênteses.

E do mesmo modo como mostramos imagens_treino, pegaremos a primeira posição de identificacoes_treino, abrindo e fechando colchetes e colocando o 0. Vamos executar, e teremos como título da imagem o número 9. O que está acontecendo com essas identificações de treino? Vamos imprimi-las para ver o que é isso, por quê veio um número e não uma palavra?

Se escrevermos identificacoes_treino e executarmos, teremos como retorno um array com números indicando quais são as _labels_, identificações dessas imagens. Podemos descobrir os maiores e menores números para saber quais são as categorias que temos, primeiro com min, que executamos. O valor mínimo é 0, e comentaremos o que foi feito com o matplotlib para focarmos só nisso.

Copiaremos a linha, daremos Enter e colaremos logo embaixo, para sabermos o valor máximo, com max, que será 9. Então, temos um array que vai de 0 a 9, ou seja, temos 10 posições, então podemos criar uma variável chamada total_de_classificacoes, com valor 10, representando 10 classificações de imagens.

E para visualizarmos as imagens com estas classificações, como faremos?

Do mesmo modo, podemos usar plt.imshow, abrir e fechar parênteses e pegar imagens_treino e, ao invés do 0, passar uma imagem genérica, imagem. Da mesma forma, para darmos um título, usamos plt.title, passando identificacoes_treino, para o qual passamos algo genérico, imagem também. Assim, vamos iterando sobre uma quantidade de imagens, 10, com for.

Mas se formos mostrar tudo isso, como é mais de uma imagem, lá para o pyplot, temos que criar algo chamado de subgráfico, um gráfico menor. Daremos um Enter e escreveremos plt.subplot. Abriremos e fecharemos parênteses, pois nesse subplot temos que passar o número de linhas, colunas, e o que queremos fazer com estas imagens.

No caso, queremos 2 linhas, 5 colunas e que ele itere sobre as imagens, para que todas sejam mostradas para nós, ou seja, imagem+1. Vamos executar para ver o que temos de retorno. Agora, temos 10 imagens, cada uma com suas respectivas _labels_ de identificação, mas isso não fica tão legal, poderíamos dar um nome de verdade para elas.

Como fazemos para saber que nomes são esses? Explorando os dados deste modo, conseguimos concluir que este nome não veio em nosso dataset; temos as identificações de 0 a 9, mas não o que isso quer dizer em uma palavra, aqui dentro. Então, o que fazemos é acessar a documentação do fashion-mnist, e o grupo de pesquisa, que criou e limpou esse dataset antes do Keras nos fornecê-lo, dirá em algum momento o que temos.

Por exemplo, a _label_ 0 representa uma camiseta, 1, uma calça, 2, pullôver, e assim por diante. Então, pessoal, podemos criar um vetor com estas coisas, e exibi-los para as nossas roupas. Vamos fazer isso! Copiaremos essa classificação do próprio GitHub deles, voltaremos ao nosso notebook, e colaremos esta classificação com Ctrl + V.

Agora vamos criar uma nova variável que irá abrigar tudo isso: nomes_de_classificacoes. Assim, sabemos que na primeira posição temos uma camiseta, e seguimos: calça, pullover, vestido, casaco, sandália, camisa, tênis, bolsa, bota. Temos o vetor com todas as classificações que vimos no GitHub do pessoal que criou esse dataset.

Agora, alteraremos as identificacoes_treino para mostrar nomes_de_classificacoes, e na posição destas identificações de treino, quero que ele exiba a nossa imagem, entre colchetes. Vamos ver o resultado?

Desta vez visualizamos o dataset de maneira muito mais interessante, sabendo que o primeiro elemento de treino é a bota, camiseta, camiseta, vestido, camiseta, pullover, tênis, pullover e sandálias. Também já sabemos que temos 10 categorias, e que os nomes delas não estão inclusos no nosso dataset. Agora podemos continuar a partir daqui.

# Identificações estranhas das imagens
Ao visualizar as imagens de treino com as identificações, você esperava ver cada imagem com a classificação no título e teve o resultado abaixo:

![imagens com números como título](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image5.png)

O que pode ter acontecido?

Selecione uma alternativa

-   O array de `imagens_treino` possui números para indexar cada uma das imagens.
    
-   O array de `identificacoes_treino` possui números para as identificações ao invés de palavras.
    
-   Um problema na função `load_data()` que fez com que o dataset ficasse incompleto.
    
-   A linha `plt.title()` retornou os números de acordo com a ordem de cada imagem.