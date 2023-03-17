[00:00] Agora vamos ver na prática todo o processo de otimização usando as funções do Pytorch. Vimos só a teoria, mas ainda não vimos as funções que usamos para fazer os passos de otimização.

[00:12] Vamos fazer todo o problema do começo. Iremos usar o dataset wine de novo. Vou importar e carregar, com a única diferença que para podermos visualizar o modelo otimizando vou selecionar só duas características dele. Vão ser teor alcoólico e intensidade da cor.

[02:55] Uma coisa que eu vou fazer aqui e que é importante fazer a depender do problema é normalizar os dados. Vou pegar da biblioteca do sklearn.preprocessing o standart scaler, porque os dados que eu escolhi são intervalos numéricos diferentes, o que pode prejudicar a convergência do modelo. Eu recomendo você tentar rodar sem o processo de normalização para ver o impacto disso.

[04:12] Agora eles estão em um intervalo numérico mais parecido. Temos nossos dados normalizados e podemos instanciar nossa rede. Também é algo que devemos saber fazer de olhos fechados. Vou fazer com as bibliotecas de sempre, nada de novo, bem rápido, para chegar na parte que nos interessa. É a rede que sempre fazemos.

[06:40] Lembrando de passar para a GPU e rodar tudo de novo, porque ele vai reiniciar. A parte de visualizar a fronteira de decisão vou copiar de um código do get hub que eu tenho, porque é um código suplementar. Quem quiser acessar, o link está aí. É só um artifício para visualizarmos o modelo.

[07:32] Temos uma rede mais complexa e queremos visualizar as fronteiras de decisão desse modelo. Vou só trocar o mapa para BRG, também quero o scatter com color map BRG. Quero plotar meus dados. Lembrando que minha rede é aleatória. Importo o numpy.

[08:50] Não vemos a região vermelha porque ela não está nem próxima de onde os dados estão, mas temos a fronteira entre o verde, o azul, completamente aleatório. Se continuarmos instanciando novos modelos vamos enxergar novas fronteiras de decisão. É por isso que vamos otimizar essa fronteira para separar esses grupos de dado, fazendo a otimização.

[09:37] Vamos definir a função de perda e o otimizador. Nossa função de perda, como é uma classificação vai ser de novo o cross entropy loss. E nosso otimizador pode ser algo bem simples, que é a descida do gradiente, que em inglês se chama gradient descent. Nosso otimizador agora vai ser da biblioteca torch optim. Estamos usando pela primeira vez. Ela que possui a implementação dos otimizadores. É só colocar optim.SGD e ela vai trazer o otimizador.

[10:53] Para isso, precisamos associar os parâmetros do nosso modelo e passar a taxa de aprendizado. Esse é o momento em que vocês vão ter que interferir diretamente com um valor. Podemos colocar um bem pequeno, como 1-3, e criar o otimizador. Ele não precisa subir na GPU, mas já definimos o critério de perda e o otimizador. É só passar os primeiros da rede e a taxa de aprendizado, que não pode ser muito alta ou muito baixa.

[11:55] Deixei uma discussão para vocês lerem com calma. A taxa de aprendizado é o que chamamos de hiper parâmetro. Um parâmetro definido pelo programador. A escolha desses valores é importantíssima e pode ser feita de forma empírica ou experimental. O que vamos fazer neste curso é tudo empírico. Iremos experimentar valores e ver como fica o resultado. É a abordagem do panda, porque ele tem poucos filhos. Você vai pegar um único modelo e modificando os hiper parâmetros, prestando atenção em como ele evolui.

[12:51] O modo experimental é definir milhares de modelos, testar todos em paralelo, e escolher o que tem desempenho melhor. É totalmente baseado em métricas. Toda vez que você escolhe quantos neurônios vai ter na sua rede, qual a taxa de aprendizado e outros que ainda vamos conhecer, isso é um ajuste que estamos fazendo de forma empírica, mas que idealmente deve ser feito de forma experimental.

[13:23] Agora vamos passar na rede e otimizar, que é o passo mais importante. Vou deixar para o próximo vídeo como fazemos o treinamento do modelo para explicar em maiores detalhes. Até agora, definimos o problema, que conseguimos visualizar a fronteira de decisão e como instanciamos o otimizador. No próximo vídeo, veremos como usar isso em um processo completo de treinamento.

 [DISCUTIR NO FORUM](https://cursos.alura.com.br/forum/curso-treinando-rede-neural-pytorch/exercicio-parte-i/68608/novo)[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/68608/next)