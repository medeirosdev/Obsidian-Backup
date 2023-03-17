[00:00] Treinamos a regressão linear, gradient boosting e verificamos a performance desse modelo, mas uma dúvida que sempre surge é se o modelo está bom o suficiente.

[00:11] Tem várias formas de avaliar isso, talvez a forma mais recomendada é você olhar para o negócio se faz sentido aquele modelo que você desenvolveu, modelos de machine learning. Mas como também está muito fácil fazer modelo de machine learning, às vezes se faz modelos para coisas que não precisam.

[00:26] Para vermos esse resultado que tivemos, vamos colocar um ponto head para diminuir o tamanho desse out put que tem, se esse resultado de 40.82 ele faz sentido, se é um resultado que emula “fazer um modelo de machine learning está compensando para treinar esse modelo”.

[00:49] Uma forma interessante de verificar isso é fazer um domínio regresso, por exemplo, eu posso pegar dentro do sklearning da parte de dummy import dummy regress - que é quando você tenta fazer um chute.

[01:15] O seu modelo ele tem que ser no mínimo melhor do que um chute. Se eu chutar sempre a média do meu modelo, por exemplo, é melhor do que o modelo que eu construí? É isso que vamos testar aqui com o dummy.

[01:28] São tipos de chutes bem prováveis sempre o mesmo valor, se estão sempre a média, coisas desse tipo. O legal é que tem várias das bibliotecas dentro, vários dos módulos, seguem a mesma lógica fit.

[01:51] Para instanciar faz dummy regressor é igual DummyRegressor() faço Dummy ponto fit, sobre a mesma base y_train. Posso fazer o predict também, dr_predict = dr.predict(X_test).

[02:28] Note que eu fiz o fit e a estratégia que ele usou é mean, a média, então ele fez calcular média e previu a média para todo mundo. O nosso modelo tem de ser no mínimo melhor do que isso, eu posso fazer dr predict e copiar esse código onde vai calcular o RMSE.

[02:48] Dessa do dr comparando com o que aconteceu, vamos ver se previsse sempre a média o que iria acontecer, 43, bem próximo do que consegui, mas já está melhor do que sempre ver a média.

[03:15] Estamos falando de um modelo para prever quanto que um usuário que entrou no site vai gastar, essa é uma informação que pode ser bem difícil de prever e simplesmente selecionei algumas variáveis e fiz o nosso primeiro teste em uma base que ainda está um pouco confusa.

[03:33] Já está melhor do que a média mas precisa melhorar ainda um pouco mais o modelo, nos próximos módulos vamos ver algumas estratégias novas para conseguir melhorar como esse modelo está atuando diante do negócio.

# DummyRegressor

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/59712/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/59712/question)

Após treinarmos o modelo é necessário avaliar a performance das predições. Além das métricas utilizadas para calcular a diferença entre a previsão e o resultado real, precisamos de um critério de comparação, para entender se vale a pena usar o modelo.

Selecione a resposta que contém as estratégias de predições usadas pelo dummy regressor do scikit learn:

Selecione uma alternativa

-   Média, mediana, quartil e valor constante.
    
-   Redes neurais.
    
-   Gradient Boosting e Linear Regression.
    
-   XGBoost.
    

 [DISC](https://cursos.alura.com.br/forum/curso-data-analytics-google-cloud/exercicio-dummyregressor/59712/novo)