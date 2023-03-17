[00:00] Agora vamos ver como usamos a loss em problemas de regressão. É exatamente a mesma coisa, inclusive mais rápido que o último. Vamos trabalhar com um dataset de diabetes, em que o objetivo é prever a progressão da diabetes em um paciente. Temos as especificações do dataset, dizendo que ele vai fazer essa regressão a partir da idade, sexo, índice de massa, pressão sanguínea. O objetivo é prever a progressão da doença por ano.

[00:44] Vamos fazer o import do sklearn, pegar o dataset. Podemos imprimir o shape. Quero mostrar a diferença entre o target agora. Não são mais classes 0, 1, 2. São valores contínuos. Temos 442 amostras, com 10 características cada e 442 rótulos, que são agora valores contínuos.

[02:24] O MLP podemos fazer igual o que fazemos anteriormente, com algumas pequenas modificações. Definimos os dados, estamos copiando o MLP do último caso, mas agora não temos mais número de classes. O outsize vai ser agora o número de variáveis que queremos fazer a regressão. No caso, vai ser uma, a progressão da regressão da diabetes. Se quiséssemos regressão da diabetes e pressão sanguínea, por exemplo, seriam duas.

[03:22] Posso manter o hidden size como 32 e o data shape 1 podemos manter. Vai funcionar igualzinho. Lembrando de importar. Para não ficar dando erro, temos que rodar o import dos pacotes e o dispositivo que vamos usar.

[04:10] Para solucionar problemas de regressão, as funções de perda pedem que ambos os rótulos e predição tenham a mesma dimensionalidade. Na aula anterior, vimos que a dimensionalidade da dimensão e do target devem ser diferentes. Neste caso, os dois têm que ter a mesma dimensionalidade.

[04:47] Vamos definir primeiro a função de perda. Nosso critério vai ser a MSE loss, que poderia ser a L1, porém tem outros critérios também. Depois, vamos fazer o cast na GPU das variáveis, porque nossos dados não estão na GPU. O xtensor vai ser torch.from_numpy(data) e o ytensor torch.from_numpy(target). Temos que converter para float e subir para a GPU. Eu vou fazer tudo de uma vez, mas vocês podem fazer separado se acharem melhor.

[06:21] Agora podemos fazer o forward da nossa rede. Teremos que a predição é dada pelo forward na rede com a entrada. Temos 442 por 1. Quando você passar no MSE loss, os dois valores têm que ter a mesma dimensionalidade, tanto a predição quanto o rótulo.

[06:51] Aqui temos duas opções. Ou adicionamos uma dimensão em um ou no outro. É só calcular critério entre predição .squeeze, para tirar aquela dimensão a mais, já que estamos prevendo só uma variável, e o rótulo.

[07:27] Ele pegou uma média da distância quadrática entre o rótulo e o dado. A loss está muito alta, e novamente, se eu tivesse passado um único valor ele ia me dar a loss para um único valor, mas como dei mais de um, ele vai me dar um único escalar, mas na verdade é a média das distâncias.

[07:57] Ele reclamou da dimensão implícita da softmax, mas não chega a dar erro. É basicamente isso, ele está calculando a loss com base no MSE, mas a forma de calcular é exatamente a mesma. Só preciso tomar cuidado porque o rótulo e o dado precisam ter a mesma dimensionalidade.

[08:34] Aqui tem a dimensão caso vocês queiram consultar outras funções de perda. Essa página sempre demora para abrir, mas vocês podem consultar por ela.