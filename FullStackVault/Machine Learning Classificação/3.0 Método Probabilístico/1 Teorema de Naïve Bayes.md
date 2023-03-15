[00:00] Vamos relembrar alguns passos dados até o momento no nosso projeto. Primeiro você, cientista de dados, sugeriu para a equipe de vendas em uma primeira reunião classificar os novos clientes em potenciais pessoas a deixarem ou não a Alura Voz, a partir das informações que já temos. Já sabemos quais clientes saíram, quais continuam.

[00:20] Nesse processo de classificação recebemos o conjunto de dados da empresa, nós entendemos essas variáveis, fizemos tratamento, balanceamento e recebemos as informações da Maria, a nova cliente que ainda não sabemos o seu possível Churn.

[00:38] Para poder classificar a Maria precisamos entender melhor o que é classificação, como funciona a classificação por trás dos panos, a matemática por trás, as funções aplicadas ao Machine Learning e vemos o modelo KNN.

[00:55] Vamos supor que a Maria foi classificada com um Churn igual a não, ela não saiu da empresa ela continua cliente. Isso significa que as características da Maria contribuíram de forma independente para esse resultado, esse Churn, essa classificação.

[01:25] Eu acabo de apresentar para você o princípio da independência condicional que rege o teorema de Byes. A sua base diz que cada uma das características utilizadas por uma determinada classe contribuíram de forma independente entre si, para que essa classe fosse determinada.

[01:52] É a partir desse teorema que o nosso modele Bernoulli Naïve Bayes, que veremos agora, é estruturado. Além disso, é um modelo utilizado em tarefas de aprendizado de máquinas supervisionado como, por exemplo, a classificação.

[02:12] Como calculamos esse teorema? Aqui temos a fórmula do teorema: "P(y/x) = P(X/y) * P(y)/P(X)". Vamos ver a fórmula por partes que você vai perceber que não é nada complicado e o modelo fica claro ainda como ele funciona.

[02:31] Vamos para o primeiro, a probabilidade de X dado que Y aconteceu, também conhecida como Verossimilhança. A Verossimilhança mede a probabilidade de uma determinada característica acontecer, sendo que a classe aconteceu.

[02:51] Vamos ao exemplo da Maria, vamos fazer a probabilidade para uma característica. Lembrando, que a probabilidade é feita para todas as características que influenciam na classe. Vamos supor que queremos saber a probabilidade de não ter dependentes sendo que foi classificado com um Churn igual a não, é isso que Verossimilhança irá medir, irá prever, calcular.

[03:21] Com esse resultado nós multiplicamos pela probabilidade de Y, também chamada de probabilidade a priori da classe. Ou seja, qual a probabilidade de uma determinada classe ocorrer em toda a amostra, é a prevalência daquela classe sobre toda a amostra.

[03:40] Qual a probabilidade de ter um Churn igual a não no nosso conjunto de clientes? O resultado dessa multiplicação iremos dividir pela probabilidade de X, o nosso conjunto de características que também é chamado de probabilidade a priori da evidência.

[04:01] Isso quer dizer que queremos agora saber a prevalência dessa característica sobre a amostra. Qual a probabilidade de não se ter dependentes em toda a nossa base de clientes.

[04:16] Agora, o resultado dessa divisão é o que o teorema quer calcular, quer prever que a probabilidade a posteriori, ou seja, a probabilidade de uma determinada classe ocorrer sendo que um conjunto de características ocorreu. Qual a probabilidade da Maria ser classificada com um Churn igual a não, sendo que ela não tem dependentes. Essa característica dela ocorreu, ela não tem dependentes. Qual a probabilidade dela ter um Churn igual a não? É isso que o Teorema de Bayes calcula.

[04:59] Vamos ver no exemplo prático da Maria a fórmula como funciona, como que é calculada com valores. Vamos supor que a probabilidade de X da Maria, a probabilidade da característica dependente ser igual a não é de "P(X) = 0.015", a probabilidade de um Churn igual a não é de "P(Y) = 0.14", vamos supor para o exemplo da Maria.

[05:25] E a probabilidade X dado que Y ocorreu, ou seja, a probabilidade de ser ter dependentes igual a não sendo que o Churn dela é igual a não é igual a "P(X|Y) = 0.006". Qual que é a nossa probabilidade a posteriori, "P(Y|X) = ?". Qual que é a nossa probabilidade se ter um Churn igual a não sendo que ela tem dependentes igual a não. Novamente, estamos calculando apenas por uma característica a exemplo de estudar melhor o calculo do teorema.

[05:56] Agora a sugiro você que dê uma pausa no vídeo, realize essas contas, entenda melhor como funciona a fórmula, escreva em um papel com lápis, caneta e depois volte aqui para ver o resultado.

[06:13] Vamos continuar, agora vamos ver qual é o resultado dessa probabilidade da Maria. Vamos colocar os valores na fórmula, temos que a probabilidade de Y dado que X ocorreu ou probabilidade a posteriori é igual a "P(Y|X) = 0.006 * 0.14/0.015" , resultando em uma probabilidade de "P(Y|X) = 0056" ou melhor, multiplicando por 100 temos: "P(Y|X) = 5,6%". A probabilidade da Maria ter um Churn igual a não sendo que ela tem a característica dependentes igual a não é de 5,6%.

[06:59] Nós entendemos a base do nosso modelo Bernoulli Naïve Bayes, mas onde que entra o Bernoulli no Teorema de Bayes?