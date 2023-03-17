Neste curso iremos trabalhar com um e-commerce, uma loja de roupas, e toda vez que subirmos uma imagem para a plataforma, teremos que escrever se ela é uma camiseta, bota, saia, ou seja, precisamos classificar esta imagem quando a colocamos no site. O que eles pediram foi que automatizássemos este processo, então, a partir do momento em que alguém coloca uma imagem nova no site, já tenhamos algo na máquina que entenda e classifique-a automaticamente.

Então, resolveremos um problema de classificação automática de imagens; já tínhamos algo parecido no curso de Machine Learning, em que pegávamos imagens de porcos e cachorros e, com base em 3 perguntas, se era gordinho, se tinha pernas curtas e se fazia óinc, a gente escrevia os dados e marcações, treinava o modelo chamado Multinomial NB, que fazia a classificação dessas imagens entre porco e cachorro.

Essa foi uma solução que demos ao problema de classificação de imagens. Mas agora, se pensarmos nas nossas roupas, como diferenciaremos uma camiseta de uma camisa, por exemplo? Porque as duas possuem gola, mangas, e podem ter botões. Entender quais perguntas fazer para o nosso conjunto de dados, não está tão simples, sem pensarmos em outros exemplos, saias, botas, tênis, calça, vestido.

Além disso, temos outro problema: agora teremos 70 mil imagens, então imagine escrever dados e marcações para essa quantidade de imagens com base nestas perguntas que já não estão fáceis de serem definidas. Usaremos, portanto, uma outra técnica, porque o que acontece é que o aprendizado de máquina é uma área grande, geral, que abrange tudo isso que ensinamos para uma máquina, e usaremos uma subcategoria dela para resolvermos este problema, que é o Deep Learning, que seria o aprendizado profundo de máquina.

Então, neste caso, pegaremos as imagens e, em vez de indicarmos as características delas, como fizemos no outro curso, usaremos funções que entenderão essas imagens e extrairão essas características, então não mais nomearemos, pois essas funções é que terão que entender o que se encontra nas imagens.

Essas funções, que também são uma rede de unidades, ou rede neural, irão classificar as nossas imagens também, do mesmo modo que fizemos com Machine Learning, também poderíamos classificá-las em duas ou mais categorias. A principal diferença, aqui, é que agora iremos extrair as características das próprias imagens, entendendo o que existe dentro delas com funções, não iremos mais ensinar um modelo.

Agora que já entendemos isso, e como iremos utilizar o Deep Learning para resolver este problema da nossa loja de roupas, podemos começar a fazer nosso código. Para facilitar e não temos que ficar instalando o Tensor Flow ou o Keras, vamos utilizar o notebook da própria Google, que se chama Colaboratory, escreverendo o código em Python 3.

Então, a primeira coisa a se fazer é criar o notebook em Python 3, em "File > New Python 3 notebook". Nosso notebook começará a ser carregado, e começaremos dando um título ao nosso arquivo, que neste caso será "classificacao_roupas.ipynb". Começaremos a escrever o código no centro de onde está o Play.

Para começar a classificar nossas imagens, precisamos das nossas imagens que, como vimos, têm o nome `fashion_mnist`. Usaremos este conjunto de dados, que se encontra no `keras`, que fica em cima do TensorFlow. Dentro do Keras, ele está em uma parte de conjunto de dados, ou `datasets`. É assim que acessamos um dataset dentro do Keras.

```undefined
keras.datasets.fashion_mnist
```

Já sabemos que estamos identificando o caminho do `fashion_mnist`, podemos guardar isto em uma variável denominada `datasets`.

```ini
dataset = keras.datasets.fashion_mnist
```

Para começarmos a carregar estes dados, será que basta executar este pedaço de código? Vamos fazê-lo para ver o que acontece. Podemos clicar neste Play. Muitas vezes, esta primeira célula demora um pouco para executar, depois as próximas serão mais rápidas.

Executamos, e recebemos a mensagem de erro dizendo que keras não está definido. O que acontece é que estamos acessando uma coisa que não importamos. Para resolvermos este erro, daremos um Enter no código e faremos o importe do Keras. Mas vimos anteriormente que o Keras está acima do `tensorflow`, isto é, dentro dele.

Sendo assim, antes deste import temos que falar que o Keras está vindo do `tensorflow`, e assim temos nosso dataset.

```javascript
from tensorflow import keras
```

Só que agora temos outro problema, porque onde está o `tensorflow`? Escreveremos mais uma linha para importá-lo também.

```cpp
import tensorflow
```

Assim, importamos `tensorflow`, de que importamos keras, e dele pegamos nosso dataset chamado `fashion_mnist`.

Vamos executar novamente nosso código, para vermos o que acontece. Para fazê-lo sem que tenhamos que clicar no botão de Play, podemos usar Cmd + Enter ou Ctrl + Enter. Desta vez nosso código roda bem, mas nada é exibido. Do mesmo modo que só chamávamos o modelo no Machine Learning, aqui só falamos mais ou menos onde está o dataset, e precisaremos carregá-lo em nosso notebook.

Para isso, daremos um Enter no código e escreveremos `dataset` e chamaremos uma função do keras chamado carregar dados, que em inglês fica `load_data`.

```scss
dataset.load_data()
```

Executaremos novamente, agora sim, tivemos algum retorno, dois arrays dentro de parênteses. A função `load_data` devolve duas tuplas no Python, dois conjuntos de dados que não podem ser modificados. É uma lista que não sofre alterações.

Então podemos pegar estas duas tuplas, que são exatamente os nossos dados de treino e teste, e guardar em nossos dados de treino e teste. Para isso, na frente de dataset, abriremos e fecharemos parênteses, acrescentaremos uma vírgula, abrir e fechar parênteses novamente, e pedir para que a primeira tupla seja salva como `imagens_treino`, `identificacoes_treino`.

Colocaremos mais uma tupla, para testes, então imagens_teste, identificacoes_teste. Aqui, se você quiser manter o padrão visto, e `imagens_treino` e `identificacoes_treino` ficar como x, e `imagens_teste` e `identificacoes_teste` chamar de y, sem problemas. O importante é que você saiba que load_data está devolvendo uma tupla, e que agora salvamos isso dentro dela, basta incluirmos um operador de atribuição.

Vamos executar mais uma vez com Cmd + Enter, e nosso código está certo. Agora, se clicarmos na célula e dermos Enter, e se escrevermos `imagens_treino`, podemos rodar mais uma vez, e teremos que nosso array está dentro, certinho e bonitinho.

Continuaremos explorando e entendendo o que vem dentro de `imagens_treino`, `identificacoes_treino`, `imagens_teste` e `identificacoes_teste`, que imagens são essas.

# Diferença entre Deep Leaning e Machine Learning

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/deep-learning-introducao-com-keras/task/46326/next)

-   [](https://cursos.alura.com.br/suggestions/new/deep-learning-introducao-com-keras/46326/question)

Como o Deep Learning é diferente de Machine Learning?

Selecione uma alternativa

-   O Deep Learning usa uma quantidade reduzida de imagens.
    
-   O Deep Learning tem funções que extraem características das imagens.
    
-   O Deep Learning usa informações que fornecemos sobre cada imagem.
    
-   O Deep Learning classifica imagens de acordo com categorias.


O Deep Learning tem funções que extraem características das imagens.

Correto! Enquanto o modelo de Machine Learning aprende com as características que nomeamos, as funções de Deep Learning extraem essas características, pois entendem quais características são essas, como vimos no exemplo do vídeo. Lembrando que essa extração não precisa ser apenas para imagens ou problemas de classificação, podemos aplicar essa técnica para outros tipos de dados e problemas.