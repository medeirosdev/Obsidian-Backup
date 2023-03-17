[00:00] Temos o desafio de conseguir melhorar o nosso modelo, esse é o desafio do cotidiano quando se leva um modelo desse para a vida real, para uma solução de negócio mesmo.

[00:14] Uma opção que temos quando estamos tentando melhorar o modelo, talvez voltar na pergunta que estamos tentando responder e verificar se não existe outro tipo de pergunta, se não pode mudar um pouco o problema que estamos tentando solucionar para de repente com um approach diferente para o problema conseguir ter um modelo que vai resolver melhor o nosso caso.

[00:38] Pode notar quando estávamos sempre avaliando a performance do modelo que tanto nesse curso quanto no outro que muitas vezes o modelo perfumou para os usuários que gastaram e para os que não gastaram. Ficou essa dúvida, como que está funcionando para o usuário que gastou?

[01:01] Talvez para o usuário que gastou ele está funcionando melhor porque eu tenho mais informações sobre esse usuário, então provavelmente um usuário que gastou mais, ele pode ter entrado no site mais vezes e assim por diante.

[01:11] Talvez uma informação importante para esse modelo vai ser mudar a resposta que tem, ao invés de tentar prever quanto que o usuário gastou o revenue, eu vou prever simplesmente se esse usuário gastou ou não. Dependendo do problema de negócio talvez essa pergunta resolva o problema do dia a dia.

[01:35] Primeiro tem que mudar a variável resposta para gastou ou não gastou - se o revenue for maior do que zero, gastou. Então vou colocar um. Se revenue for menor que zero usuário não gastou então eu vou colocar zero.

[01:55] Como que faz? y_train.values, y_train < 0 isso retorna todos os valores menor do que zero no Y train, como não há valores menores do que zero eu tenho que colocar aqui menor ou igual a zero. Todos os valores menor igual a zero eu só vou garantir que esses valores sejam zero mesmo, isso aqui talvez seja uma boa prática para esse código entrar em produção.

[02:31] A diferença para os valores que forem maior do que zero eu vou colocar 1, então se eu tiver alguma coisa maior do que 0, simplesmente coloque 1. Assim estou mudando o meu problema para tentar prever quanto que esse usuário gastou para simplesmente se gastou ou não.

[02:52] Faz a mesma coisa para y teste, quando noto o y teste eu vou ter um monte de usuários que não gastaram e no meio alguns usuários que gastaram apenas como 1. E agora você pode treinar novamente o nosso modelo só que ao invés de modelo de regressão tem um modelo de classificação onde vou tentar prever a classe se é 0 ou se é 1.

[03:38] Vou importar de novo do from sklearn.ensemble vamos fazer diretamente o gradient boosting e ter um resultado melhor, import GradientBoostingClassifier, enter, já importei e você vai fazer do mesmo jeito que fez nos outros casos.

[04:15] Vamos chamar de clf_gb só para separar que é classifier do gb, pode fazer igual esse para instanciar a variável, podemos fazer o fit: clf_gb.fit(X_train, Y_train), podemos fazer o predict. Vou falar clf_gb.predict(), vou armazenar esse valor dentro de clf predict é igual clf_gb.predict(X_test), ele está treinando ainda, lembrando que o gradient boosting pode demorar um pouco, mas já vou fazer o predict também.

[05:15] Pediu para executar, assim que terminar de rodar esse, vamos esperar ele rodar. Bom, já terminou de rodar agora você pode olhar como ficou a performance desse modelo. No modelo de regressão estávamos usando o RMSE para analisar a performance agora é um modelo de classificação, não pode mais usar o RMSE – que é para modelo de regressão.

[05:41] Precisa de outras métricas para validar um modelo de classificação, por sorte dentro sklearning tem vários algoritmos para gente calcular isso. Então, from sklearn.metrics import confusion_matrix, dentro dela passo o y teste e clf_gb_predict.

[06:23] Eu tenho como que o meu modelo se comportou para os usuários que gastaram e os usuários que não gastaram, entenda essa matriz como usuários que não gastaram, zero, e eu previ que não gastariam zero e zero. Aqui são os usuários que gastaram e eu previ que gastariam, acertei esses usuários mais esses usuários.

[06:57] Errei esses outros dois aqui, 132 desses usuários eu previ que eles não gastariam e eles gastaram e 61 desses usuários eu previ que eles não gastariam e eles gastaram.

[07:14] A confusion_matrix mostra como que ficou a performance entre o que foi previsto e o que aconteceu, entre zeros e uns. Podemos olhar para um algumas outras métricas também e existe uma outra biblioteca dentro do sklearn que ajuda com isso.

[07:40] Vamos importar aqui ou classification report, então com várias métricas para avaliar modelos de classificação e vai chamar ele passando os mesmos valores que passou aqui dentro. Em classification report preciso dar esse print.

[08:10] Todas essas métricas estão falando, são várias métricas para avaliar como um modelo de classificação está funcionando e pode olhar para uma especificamente que é mais simples; que a precisão. Quanto o nosso modelo acertou dessa faixa da label 0 e 1.

[08:35] Notem que acertamos 99% das vezes quando o usuário não gastou, que é array 15.649, só que os usuários que gastaram acertamos apenas 54% das vezes, significa que estamos acertando muito pouco para os usuários que gastaram, talvez até por isso que a performance do nosso modelo de regressão não foi tão bom.

[09:03] Notem que vamos ter de resolver esse problema e por que ele está acontecendo? Dentro da nossa base tem muito mais usuários que não gastaram comparados com usuários que gastaram, nossa base é muito desbalanceada.

[09:18] Se eu prever que todo mundo não gastou eu vou acertar 99% das vezes, vamos no próximo vídeo um Dawnsample que é uma técnica para trabalhar com bases desbalanceadas para tentar melhorar a nossa performance para os usuários que gastaram, mesmo que erre um pouco mais para os usuários que não gastaram. Até o próximo vídeo.