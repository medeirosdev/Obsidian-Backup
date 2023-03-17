Para começarmos a criar nossa rede, vamos entender a estrutura disso que estamos falando; lembrando do curso de Machine Learning, tínhamos as imagens de porcos e cachorros, que também podemos classificar como sendo a nossa entrada, e quando usávamos o modelo e o algoritmo, fazíamos um processamento com elas, e depois classificávamos, o que poderíamos definir como sendo a saída.

Agora, no Deep Learning, faremos o mesmo: teremos as nossas imagens, que serão uma entrada, nossas funções serão o processamento e, no final, teremos uma saída. Mas qual a diferença de um para o outro? Agora, o nosso modelo considera tudo isso, essas três etapas. Então, vamos voltar ao Notebook para escrevermos isso.

Agora que já organizamos o código, vamos até o fim do Notebook e criar uma nova célula. O que é que sabemos? Que nosso modelo possui uma entrada, o processamento e a saída, essas três camadas acontecendo. Cada uma delas será em sequência, primeiro entra, depois processa, e então sai.

Podemos começar a escrever isso na linguagem do próprio Keras e do TensorFlow, então, pegaremos a palavra modelo e o faremos receber o que virá aqui. Sabemos que há uma sequencia, que em inglês é Sequential, então esta é a primeira coisa que escreveremos, que se encontra dentro do keras, então deixaremos keras.Sequential, utilizaremos este tipo de modelo dentro do Keras, algo que fará nossas camadas de entrada, processamento e saída acontecerem em sequência.

Como isso é uma função, vamos abrir e fechar parênteses, e como é isso que organiza o nosso modelo, colocaremos as nossas camadas dentro deles. E como temos mais de uma coisa acontecendo, iremos abrir e fechar os colchetes para agruparmos tudo isso, indentando para ficar mais legal.

Vamos começar pelo começo, então olharemos melhor nossa entrada comentando processamento e saida. Sabemos que nossa entrada são as imagens, então vamos pensar um pouco no que já exploramos e sabemos em relação às nossas imagens. Temos um exemplo que são um par de botas, e se formos pegar esta imagem, ao usarmos len ou shape, vimos que ela tinha 28 x 28, linhas e colunas. E que cada um desses espaços ocupava um número, isso será chamado de pixel, então as imagens são formadas por pixels.

Se considerarmos 1px deste tamanho para esta imagem que vemos, conseguimos incluir 4px dentro dela, então dividimos esta imagem em 4px. Mas do mesmo modo que tínhamos 28 x 28, podemos ler esses 4px de outra forma, que são 2px para a nossa linha, e 2x para a coluna.

Repare que quando chamamos esta imagem de 2 x 2px, estamos tendo uma imagem de 2 dimensões, linhas e colunas. O que podemos fazer nesta primeira camada que chamamos de camada 0 é pegar esses 2 x 2px e, por exemplo, ter uma função para lidar com cada pixel. Então, teríamos 4 unidades, 1 para cada pixel, e o que elas farão é reordenar e reagrupar estes pixels. Então, em vez de termos 2 dimensões, 2 linhas e 2 colunas, teremos 1 linha e 4 colunas, assim temos 1 dimensão com 4 pixels.

É isso que faremos em nossa primeira camada, que é a que chamamos de camada 0. Essa é a nossa entrada. Voltaremos ao Notebook, e sabemos que em nossa entrada iremos lidar com imagens que temos no dataset, e elas não tinham 2 x 2 pixels, e sim 28 x 28 px. Esses números, que iremos agrupar entre parênteses e com uma vírgula entre eles, são as dimensões que vimos na forma da nossa imagem.

Forma em inglês é shape, e até agora, quando falamos sobre entrada, estávamos falando sobre input, que é entrada em inglês. Ou seja, essa é nossa input_shape, ou a forma da entrada, imagens de 28 x 28px. Mas ainda temos que falar da tal da camada 0. Camada em inglês é layer, e o Keras possui várias camadas, então escreveremos layers.

Para transformarmos a nossa imagem de 28 x 28px em um array de 1 dimensão, com todos esses 28, 28 pixels, iremos fazer um achatamento para as dimensões vetoriais. Isso em inglês fica Flatten, então usaremos keras.layers.Flatten, e como é uma função, abriremos e fecharemos parênteses, passando as nossas imagens de entrada para dentro dessa primeira camada, ou camada 0.

Agora já temos um modelo, e sabemos que ele acontece em sequência, e temos a nossa primeira camada. Podemos rodar para ver o que acontece. Daremos Cmd + Enter, e obteremos um erro indicando que input_shape não foi definido, esquecemos de atribuir os 28, 28 no input_shape, basta acrescentarmos um sinal de igual em nosso código. Vamos rodar mais uma vez, legal, só que cadê o nosso modelo, criamos, mas onde ele está?

É a mesma coisa do curso de Machine Learning, apenas criamos, falamos que existe uma camada dentro de um modelo sequencial, então agora podemos começar a fazer os outros passos para começar a ver a saída desse modelo.

# As etapas do modelo

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/deep-learning-introducao-com-keras/task/46334/next)

-   [](https://cursos.alura.com.br/suggestions/new/deep-learning-introducao-com-keras/46334/question)

Ao olhar esse código de um modelo de deep learning:

```less
modelo.Sequential([
    keras.layers.Flatten(input_shape=(28,28))
])
```

Quais são as etapas do modelo que estão representadas nele?

Selecione uma alternativa

-   Entrada e processamento.
    
-   Entrada, processamento e saída.
    
-   Apenas a saída.
    
-   Apenas a entrada.

# Para saber mais

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/deep-learning-introducao-com-keras/task/46336/next)

-   [](https://cursos.alura.com.br/suggestions/new/deep-learning-introducao-com-keras/46336/question)

Trabalhando com imagens

Estamos trabalhando com um dataset que, além de ser interno ao Keras, é preparado para facilitar ao máximo o teste com nossos modelos. Como?

Imagine que você tenha que dizer qual o conteúdo das três imagens abaixo:

![imagens 1, 2, 3 com patos fotografados de maneiras diferentes](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image16.png)

Olhando, nós sabemos que as três têm patos.

Na imagem 1 o pato está bem contorcido e tem bastante azul, verde e marrom na imagem. Na imagem 2, é um pato de borracha, mas conseguimos ver a carinha dele, e tem bastante amarelo e laranja na imagem. Na imagem 3, o pato está distante e abrindo as asas, tem bastante verde na imagem. Repare como a imagem 1 é bem diferente da imagem 2 que também é bem diferente da imagem 3. Elas são pouco semelhantes.

E quanto mais dados diferentes tivermos, mais complexo vai ficar o nosso modelo. O que poderíamos fazer para simplificar? Poderíamos retirar algumas informações, como a cor.

![mesmas imagens em escala de cinza](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image14.png)

Deixando as imagens em uma escala de cinza, já criamos uma uniformidade entre elas que facilita e simplifica para que o nosso modelo reconheça as semelhanças e diferenças.

Além disso, o que mais poderíamos fazer? Podemos destacar os nossos patos do fundo, exagerando no contraste das imagens.

![mesmas imagens com alto contraste](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image1.png)

Ao fazermos isso, já percebemos que, por exemplo, o contorno da imagem 2 se perde, confundindo mais do que ajudando a reconhecer o contorno, então talvez seja mais interessante termos outra imagem desse tipo ou trabalhar com as outras duas.

Nós já retiramos a cor e aumentamos bastante o contraste entre as imagens, será que tem mais alguma coisa que podemos fazer? Sim, podemos deixar os patos no centro delas, redimensionando-as e centralizando a forma do pato, que é essencial.

![imagens 1 e 2 centralizadas e do mesmo tamanho](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image10.png)

Agora temos duas imagens simples, com pouca informação, centralizadas e com as formas dos patos em destaque, o que irá facilitar para que o nosso modelo as reconheça.

Este foi um exemplo do que é possível fazer para pré-processarmos um dataset, algo muito comum ao treinar modelos no dia a dia e que consome uma boa parte do tempo de quem trabalha com isso.

Para fazer essas transformações, precisamos explorar os dados como fazemos no curso com o **pyplot** do **matplotlib**, e usar também uma biblioteca como a **scipy** do Python que tem um módulo chamado **ndimage** apenas para lidar com imagens.

```javascript
from scipy import ndimage
```

Para ver os códigos, é possível dar uma olhada neste [tutorial](http://www.scipy-lectures.org/advanced/image_processing/) (site em inglês).