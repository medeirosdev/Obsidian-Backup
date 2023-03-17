[00:00] Estamos chegando na reta final e vamos falar um pouco dos elementos do fluxo de treinamento, como organizar o treinamento da nossa rede. Temos três coisas extremamente importantes na forma como inteiramos para treinar nosso modelo.

[00:40] Começando pela iteração. O treinamento é um processo iterativo e se partimos de um modelo aleatório, com cerca de 100 iterações resolvemos o problema. Dependendo de como inicializamos o modelo aleatório, ele pode converter mais rápido ou mais devagar.

[01:14] Também vimos que tem os seguintes passos em cada iteração. Uma iteração é quando todo esse fluxo acontece. Operamos a entrada na rede, calculamos função de perda, calculamos o gradiente e atualizamos os pesos. Esse fluxo é uma iteração. Mas vocês também viram que conseguimos passar na rede vários dados de uma vez.

[01:51] A iteração consiste em um passo de otimização, que é o forward e o backpropagation. Mas quantas amostras devem ser vistas por iteração? Isso é um fator muito relevante dentro de uma solução usando deep learning.

[02:05] O batch é justamente a quantidade de amostras vistas numa iteração. Ele está fortemente relacionado com a iteração. Se formos otimizar um perceptron para resolver um problema linearmente separável, é um problema simples e fica visível como o tamanho do batcher vai influenciar na solução.

[02:50] Dado que temos o modelo inicial aleatório, se eu faço uma iteração com uma amostra ele já ajusta. Você pode pensar que se aumento o número de amostras consigo usar meu modelo com menos iterações. Talvez sim, talvez não. O tamanho do batch vai interferir no comportamento de convergência.

[03:35] Tem que existir um equilíbrio, porque se olharmos a descida do gradiente com diferentes tamanhos, temos três diferentes descidas do gradiente. A estocástica, que é com uma amostra. O mini batch, que é um subconjunto do treino, e o batch, que é com conjunto de treino completo.

[03:58] O estocástico vai consequentemente fazer mais iterações. Sua convergência para chegar no ponto mínimo vai convergir loucamente e você vai precisar de muitas iterações para conseguir enxergar se seu modelo está convergindo ou não.

[04:22] Com o mini batch já teria um comportamento mais conservador. Não iria ziguezaguear tanto. E vendo todo o conjunto de treino a cada iteração, ele vai bonitinho na direção do ponto mínimo.

[04:42] O que acontece quando você passa todo o conjunto de treino de uma vez? Você gasta minutos para uma iteração. Demora muito para chegar nula solução ótima. Mas vendo uma amostra de cada vez vai ser rápido, porém não tão interessante para entender se o modelo está convergindo bem ou não.

[05:21] Se a gente tem um dataset com 3 mil amostras, como podemos dividir? Primeiro, 2 mil para treino e 1 mil para teste. Dado que temos 2 mil amostras de treino, podemos dividir em 4 batches de 500, ou em 10 de tamanho 200. Para que a rede veja todo o conjunto de treino, vão ser necessárias 10 iterações.

[05:52] Essas dez iterações é o que vai completar uma época. A época é justamente quando todas as amostras do conjunto de treino foram vistas pelo modelo. Quando ele iterou o suficiente.

[06:14] Mas, se ao final de uma época o modelo viu todas as amostras de treino, por que precisamos de mais de uma época? O treinamento é um processo iterativo, e uma época só não é suficiente. Se são pequenos ajustes precisamos fazer várias vezes.

[06:40] A época n+1 tem como ponto de partida o modelo ajustado na época n. A cada nova época você vai refinando seu modelo.

[06:44] Em geral, o gráfico de convergência definido em termos das épocas é definido em termo das épocas.

[07:11] Isso é um fluxo de treinamento comum, que é o que iremos implementar no próximo vídeo, que basicamente você vai iterar o número de épocas, os batchs, e para cada época você vai fazer o forward e o back propagation, que já vimos. Vamos ter essa hierarquia dupla.

[07:52] Por enquanto é isso. Daqui para o final só vamos ver na prática, mão na massa.