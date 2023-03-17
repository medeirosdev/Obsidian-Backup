[00:00] Vamos ver como funciona no Pytorch o cálculo da função de perda. Só que para isso vamos simular um problema inteiro, vamos repetir todo o processo que já conhecemos.

[00:13] Primeiro vamos fazer os imports de sempre, não iremos precisar de nada diferente, as funções de perda também estão no pacote NN. E vamos relembrar que precisamos verificar qual dispositivo está disponível, se temos GPU disponível para definir qual dispositivo vamos usar para colocar os dados.

[01:00] Tivemos o cuda, porque antes de começar a gravar eu mudei as configurações para usarmos a GPU. Iremos trabalhar com um dataset de classificação de vinhos. Ele tem três classes e treze características para fazer a classificação, além de 178 amostras.

[01:27] Se pegamos o pacote de datasets do sklearn, conseguimos ter acesso ao dataset de vinhos. Ele vai dar para nós tanto os dados quanto os rótulos. Podemos imprimir tanto a dimensão dessas coisas como os nomes das nossas features, nossos dados, e o nome das classes.

[02:17] Temos 178 amostras, cada uma com treze características e 178 rótulos. As características são nível alcoólico, acidez, alcalinidade, etc. Também temos os nomes das classes. Os dados em si, se imprimirmos um target, são valores inteiros. E o dado é uma sequência de floats que são dados das características.

[03:22] Vamos fazer o que já sabemos e instanciar um MLP, uma camada escondida e uma camada de saída para resolver um problema de classificação. Temos que fazer nossa classe, que vai ser o wine classifier, é uma classe módulo, que cria módulos de redes neurais, e temos duas funções obrigatórias que precisamos implementar. A init e a forward, que recebe não só o self, indicando que ela pertence à classe, mas também a entrada.

[04:00] Lembra que no init é obrigatório inicializar a super classe. Agora podemos fazer o que quisermos, que no caso do init é a definição da nossa arquitetura. Quero uma camada escondida, que vai ser linear, quero uma ativação relu e uma camada de saída, que também é uma linear.

[04:43] Como estamos tratando de um problema de classificação de três classes, posso também querer uma softmax que vai transformar minhas saídas em distribuições de probabilidade. Aqui defini minha arquitetura.

[05:00] Para definir esses valores, já sei que a primeira camada, que é a camada escondida, vai receber o dado original. O input size vai ser o tamanho da feature. E ela vai sair com features latentes, que vai ter uma quantidade de dimensões que o próprio programador vai definir. Eu vou definir o tamanho da camada escondida, porque ela não está relacionada ao problema. Ela é minha forma de solucionar o problema.

[05:30] Na camada de saída, ela vai receber a saída da camada anterior e vai ter um outsize que vai ser o número de classes do meu problema. Vou receber isso como parâmetro da minha classe, e está definida a arquitetura.

[05:57] Na hora de fazer o folder, vou definir minha feature intermediária, que vai ser a ativação da camada intermediária, e minha saída vai ser a ativação softmax da minha camada output, que vai receber como entrada a feature que acabei de criar ali em cima. Retorno esse output e posso definir minha rede.

[06:33] Primeiro vou definir os valores. O input size é a quantidade de features que eu tenho. Essa informação vimos que está no shape. Se eu olhar o shape, a segunda dimensão é o número de características. O meu hidden size é uma escolha minha, posso colocar, por exemplo, 32, porque estou definindo que 32 neurônios é o suficiente para resolver o problema. E meu outsize é o número de classes. Posso pegar, por exemplo, target names. Pego o comprimento dele.

[07:25] Com isso, posso mudar esses dados a qualquer momento, posso mudar o dataset e não vou precisar implementar nada, porque estou pegando informação do próprio dado, não definindo valores na mão.

[07:44] Preciso criar a rede. Coloco o to device, porque estou fazendo o cast na GPU. Agora, posso imprimir a rede para ver exatamente o que fizemos.

[08:25] Vamos instanciar uma função de perda, que é o motivo de estarmos aqui. Posso chamar em geral a variável de loss de critério, e posso colocar NN.crossentropyloss, porque sei que é um problema de classificação. Quero calcular a entropia cruzada entre a distribuição que vai ser predita e a distribuição do rótulo. Aqui também tenho que fazer cast na GPU.

[09:14] Precisamos agora transformar os dados em tensores, porque por enquanto são arrays, e passar na rede. Uma vez feito isso, podemos calcular a loss entre o rótulo e a predição da rede. Vamos transformar os dados em tensores. Vou ter o xtensor, que vai ser torch.from_numpy(data) e o ytensor, que vai ser torch.from_numpy(target).

[10:18] Por padrão, o que usamos não é o double na rede, a menos que disséssemos explicitamente que nossa rede é double, tenho que converter para float para ficar de acordo com a rede. No caso do rótulo, é long mesmo. Só que também temos que fazer cast na GPU.

[11:08] Posso passar na rede. Minha predição vai ser a saída na rede, dada a entrada. O shape disso é 138 por 3, porque o x são 178 amostras, com 13 características. E a saída são 138 amostras com 3 probabilidades. Se eu passasse uma única amostra, eu teria que arrumar as dimensões, e o que eu teria é que passei uma única amostra com 13 características e ele predisse uma única amostra com 3 probabilidades.

[12:24] Como transformamos numa distribuição, ele vai prever valores cuja soma vai dar 1. É uma distribuição de probabilidades. Isso é aleatório, porque não treinamos. E agora que já fizemos a previsão, podemos comparar com a função de perda.

[12:55] Vou fazer a predição de tudo e vou comparar as dimensionalidades da predição com as do rótulo. Elas não batem. Minha predição tem 3 dimensões de classe e meu rótulo só uma. Não tem problema, porque no caso específico da cross entropy ele aceita dessa forma. Podemos passar os dados assim.

[13:45] Dado que nossa predição é uma distribuição de probabilidade e o rótulo um único valor, não tem problema, porque é assim que a cross entropy aceita os dados. Posso simplesmente chamar a loss, falando o critério e mandando como parâmetro a predição e o rótulo. Ele vai calcular a perda média entre todos os valores. Se eu pegar só o rótulo de uma classe ele não vai conseguir por causa da dimensionalidade.

[15:22] Posso por exemplo pegar um range, da amostra 1 até a 30. Ele vai dar a média das perdas para esses valores. Basicamente, é isso. É dessa forma que vamos usar a loss. Depois vamos aprender a utilidade disso no processo de otimização, mas por hora só estamos vendo como calcula.

[15:47] Relembrando que a loss vai ser sempre um valor escalar, independente do número de amostras. Ela vai indicar o erro naquele conjunto de dados. No próximo vídeo vamos ver um problema de regressão.