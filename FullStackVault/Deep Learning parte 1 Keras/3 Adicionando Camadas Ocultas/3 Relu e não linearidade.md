Já escrevemos mais uma camada de nossa Rede, e estamos usando a função chamada relu, mas não entendemos muito bem o que ela faz, então também fiz uma apresentação para visualizarmos isso. Começaremos com o gráfico, em que temos o eixo X, horizontal, o eixo Y, vertical, e o 0.

Agora, faremos pontos, e um ponto em X vale -4, enquanto em Y vale 0. Do mesmo modo, outro ponto em X vale -2, e em Y vale 0. E então traçaremos uma linha unindo estes pontos. Agora, faremos pontos do outro lado: em X, 1.5, e eu Y, 3, outro em X valendo 3.2, e em Y valendo 5. Vamos fazer uma linha para juntar estes dois pontos.

Se fizermos mais pontos supondo que -3 em X e 0 em Y, vamos considerar que tudo que se encontra em nosso X, como este -3, foi uma entrada. Temos as nossas camadas, vamos supor que a de Flatten tenha vindo -3. Observando esta linha, o que nosso -3 vira? Se Y for a saída, o -3 virará um 0, pois Y é 0.

Então, o que acontece na ReLU é que todos os números negativos se tornam 0. É por isto que esta função transforma. Mas o que acontece com os números positivos? Se fizermos outro ponto, 2, quando Y for 0, do mesmo modo que acabamos de ver, todos os números positivos se mantêm, ou seja, continuarão sendo positivos.

É isso que a ReLU faz por debaixo dos panos. Além disso, ela faz outra coisa muito importante em Redes Neurais, redes como Deep Learning, redes mais profundas. Reparem na ReLU, dá para chamar isso de linha? Se for uma linha, seria uma que quebrou no meio, no 0, certo?

O que podemos entender disso é que essa função não é uma linha, ou seja, trata-se de uma função não linear, então a ReLU introduz na nossa Rede Neural Profunda funções não lineares. Por que isso é importante? Explicarei isso com mais um gráfico para vocês. Aqui, temos o X e o Y, e as nossas imagens de porcos e cachorros. Reparem que do jeito que elas estão agrupadas, se traçarmos uma linha entre os grupos, conseguimos separar essas imagens.

Foi mais ou menos isso que fizemos com o MultinomialNB por debaixo dos panos. Mas vejamos com as nossas roupas, o que acontece? Temos a camisa perto da camiseta, da calça, da saia, do sapato. Elas estão juntas, mas você consegue enxergar uma linha acontecendo? Não tem como, então teremos que traçar essas separações por meio de curvas, resultando em mais ou menos 5 áreas.

Essa é uma função não linear, e é por isso que usamos a ReLU, porque não conseguiremos separar as nossas imagens com apenas uma linha, e foi por isso, também, que essas funções surgiram dentro de Machine Learning, de Redes Neurais, para conseguirmos classificar coisas como este conjunto de dados que não separaremos com uma linha.

Dito isso, poderemos voltar ao nosso Notebook para fazermos mais uma camada. Já fizemos a camada 0, que é Flatten, a segunda, que é Dense com relu, que para quem tiver curiosidade significa Unidade Linear Retificada. Agora precisamos fazer nossa camada de saída. Como sabemos, temos que pegar a saida, e usar keras.layers também. Continuaremos com uma camada densa, que é uma função, então abriremos e fecharemos parênteses.

E que número colocamos aqui? Temos a nossa entrada, o processamento e a saída. Quantas categorias tínhamos, mesmo? Se observarmos no próprio Notebook, temos que total_de_classificacoes é igual a 10, ou seja, temos 10 tipos de categorias. Então, o número da nossa camada de saída será 10. E para esta camada também precisamos que ela seja ativada, então escreveremos activation, e pegaremos algo do tensorflow.nn.

E o que mais?

Na primeira incluímos o input_shape, as dimensões de nossa imagem, na segunda, relu, que acabamos de entender o que é. E para essa saída, em 10 coisas? Como fazemos? Veremos daqui a pouquinho.