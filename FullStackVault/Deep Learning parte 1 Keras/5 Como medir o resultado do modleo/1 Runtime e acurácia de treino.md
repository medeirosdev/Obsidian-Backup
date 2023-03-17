Vimos que pode ser mais interessante mantermos uma única camada com 256 unidades do que três camadas, uma com 256, outra de 128, e outra de 64. Então, o que podemos fazer para voltar ao valor inicial da nossa perda, que era menor do que 2.30 que está aqui, é comentar essas duas camadas, a de 128 e a de 64.

Caso prefira, podemos apagar as duas linhas, e voltar ao estado inicial. Agora, vamos rodar mais uma vez, e ver se a perda irá diminuir. Vemos que demorou 9s, e a perda continua sendo de 2.30. O que será que aconteceu? Tiramos duas camadas que vimos que requeriam mais processamento, demoravam mais e davam uma perda alta, por que é que a perda continua grande?

Este é um detalhe do próprio Notebook que estamos usando; há mecanismos por baixo dele, que faz toda a execução, ou _Runtime_ em inglês, que vai guardando o estado, ou números de variáveis que estão rodando por debaixo dos panos em nosso modelo, pois quando ele erra algo, ele tem umas variáveis aleatórias por detrás dele, que vão mudando de acordo com o que ele vai aprendendo.

E aí nosso Notebook muitas vezes vai guardando estas variáveis, e fica parecendo que temos o mesmo resultado. Então, o que podemos fazer para mudar isso é clicar na flechinha para baixo para conseguirmos ver novamente o cabeçalho, clicar em Runtime > Restart runtime. Assim, restartamos o Notebook para termos todas essas variáveis que rodam por baixo dos panos resetadas, zeradas.

Confirmamos, e é possível acompanhar o status na parte superior do Notebook, que indica que ele está conectado, e agora, basta rodarmos o modelo novamente? Já vimos que não, certo? Se ficarmos um tempinho e o _Runtime_ desconecta, precisamos recomeçar lá de cima, com os importes. Vamos fazer isso.

Rodaremos o primeiro import, carregaremos o dataset, podemos pular a parte de exploração e exibição de dados, e viremos direto ao nosso modelo, que rodaremos. Ele está treinando, e agora daremos uma olhada na nossa perda, que está em 0.4825. Então, todas as vezes em que você for mexer nas camadas do modelo é legal dar um _Restart_ no _Runtime_ do Notebook que está sendo usado, e com calma, porque às vezes quando se diminuem camadas, comenta camadas, pode ser que o resultado não mude ou fique estranho.

Estávamos vendo estratégias para reduzir ainda mais esta perda. Reparem: quando treinamos para algo geralmente treinamos uma vez e fica bom? Vamos supor que você começasse a tocar piano, que não é algo trivial. Você vai treinar uma única vez? Você vai saber tocar tudo no piano, Beethoven? Difícil, não é, pessoal?

Uma coisa que está acontecendo aqui, repare que na linha de nossa perda, com os 60000 dados, a Epoch foi rodada uma vez apenas. Então, estamos treinando o nosso modelo com os nossos dados apenas uma vez. Podíamos aumentar este treinamento para ver se a perda diminui, e nosso modelo começa a entender mais informações.

Como fazemos isso? Muito simples, vamos a modelo.fit e, depois de identificacoes_treino, adicionaremos uma vírgula, e a mesma palavra de época, isto é, Epoch, colocamos epochs, no plural. Colocaremos também um operador de atribuição, ou =, e vamos treinar umas 5 vezes.

Vamos usar o Cmd + Enter, e demorará um pouco mais, porque vai rodar aquilo que rodou uma vez vezes 5. Após treinarmos 5 vezes o nosso modelo, conseguimos diminuir a nossa perda para 0.45. Então, podemos ir testando tanto quanto as camadas quanto quantas vezes treinamos para ver se isso está aumentando ou diminuindo.

Estamos vendo que estamos perdendo menos, mas como é que sabemos o quanto estamos ganhando?

Repare que não temos essa métrica, e para isso, na célula, quando compilamos o nosso modelo, depois de perda, ou loss, podemos passar que queremos sim saber o quanto a nossa rede, o nosso modelo, está acertando. Adicionaremos mais uma vírgula, um Enter, e como falamos, métrica em inglês é metric, e como pode ser mais de uma, usamos metrics. Incluiremos =, abriremos e fecharemos colchetes, pois pode ser mais de uma, e escolheremos uma, a principal métrica, usada na maior parte dos modelos.

Taxa de acerto, como visto no curso de Machine Learning, aqui é mais comumente chamado de acurácia, que em inglês fica accuracy, e o colocaremos entre aspas simples. Agora podemos rodar novamente e ver qual diferença isso vai fazer. Se formos observar a nossa perda e a acurácia, ela foi de 0.1 para 0.11, para 0.16, 0.20 e 0.23.

Isso é bom, pois o quanto acertamos está aumentando. E se observarmos nossa perda, que está naquele 2.30 um pouco estranho, talvez fosse bom restartar nosso _Runtime_, mas de todo modo ela está diminuindo, e fechamos com ela em 2.22. Este é um resultado muito legal para quando treinamos o modelo. Queremos sempre que a perda diminua e a acurácia aumente, que a nossa rede acerte mais e erre menos.

Treinamos o nosso modelo, fizemos o .fit. O que mais podemos fazer com ele?