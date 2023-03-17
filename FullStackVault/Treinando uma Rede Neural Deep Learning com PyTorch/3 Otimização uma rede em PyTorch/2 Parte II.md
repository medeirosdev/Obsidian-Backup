 [00:00] Vamos então para a parte que interessa, que é fazer o fluxo de treinamento, incluindo o forward e a parte de otimização. Só lembrando que na aula anterior conhecemos o pacote optim, que é o pacote de otimização do Pytorch, e chamamos o otimizador stochastic gradient descent.

[00:30] Temos um problema em que temos 3 classes de vinho distribuídas no espaço e queremos classificar isso. Só que com nossa rede aleatória temos a situação em que nada faz sentido.

[00:47] Primeiro vamos transformar os dados para tensores e subir eles na GPU. Para converter, podemos usar o torch.floatTensor(data) e já subo na GPU. Com o y a mesma coisa. Só que ele vai ser um long e target.

[01:35] Agora vem a parte de conhecer as funções que vão nos ajudar no processo de otimização. Sabemos como alimentar os dados na rede. É só chamar como uma função. E sabemos que para calcular a função de custo é só chamar a variável critério que definimos, que é o calculador de loss, com a predição e o rótulo.

[02:02] O back propagation é composto do passo de calcular o gradiente, que é uma derivada. Para derivar qualquer coisa no Pytorch você chama o .backward. Ele já vai fazer a diferenciação automática. Se o que queremos é só uma derivada, só precisamos chamar o loss.backward.

[02:28] O passo de atualização de pesos vai ser o optimizer.step. Optimizer também é uma variável que definimos lá em cima. Nosso otimizador. A partir do gradiente calculado aqui, vamos dar um passo no otimizador. É tudo muito transparente, fica internamente no Pytorch, mas vamos devagar.

[03:02] O forward vai ser literalmente o que está lá em cima e a loss o critério da predição com rótulo. O backward é exatamente o que está ali também. Veja que não estou atribuindo esses valores a nada, pegando gradiente e passando para o otimizador, porque essas coisas já foram conectadas internamente. No momento em que calculei a loss em função do rótulo e da perda, ele já calculou a perda e quando derivo isso ele já cria um gradiente. Quando criei o otimizador, já associei minha rede. Quando dou um passo de otimização, sei que estou alterando esses parâmetros que coloquei.

[04:15] Aí vem a questão. Chamei todas essas funções, minha rede já mudou. Será que quando eu plotar a fronteira ela vai estar diferente? Ainda está idêntica, porque a otimização de redes neurais é um processo iterativo. São passos pequenos. Uma iteração de treinamento é quase imperceptível, você quase não muda nada. Por isso temos que fazer centenas, milhares de iterações. Aqui vamos fazer 100.

[05:30] A ideia de otimizar a rede neural, por mais que pareça esquisito, precisa ser feito, porque ele vai dar pequenos passos no espaço do erro. Ele precisa fazer isso para chegar numa solução útil. Eu vou plotar a cada 10 iterações para vermos como vai ficar.

[06:11] À medida em que ele vai dando passos de iteração, ele foi chegando no que acredita ser o ideal. O número de iterações também vai mudar de acordo com como ele inicializou a rede.

[07:12] Com 200 iterações conseguimos chegar da fronteira horrorosa que tínhamos para algo mais interessante. Com uma rede simples, poucas iterações, encontramos uma boa solução. A conclusão que quero que vocês tirem é que a otimização é um processo iterativo. Cada iteração tem um papel importantíssimo. Iremos conhecer nos próximos vídeos os conceitos de época, batch, extremamente importantes para treinar uma rede neural. O que vamos aprender tem tudo a ver com como organizamos essas iterações para fazer o aprendizado da forma correta.