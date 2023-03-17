[00:00] Agora vamos treinar nossa regressão linear, eu vou importar aqui sklearning um biblioteca de regressão linear, então, sklearn.linear_model import LinearRegression, agora pode instanciar uma variável de regressão linear.

[00:29] Eu vou deixar instanciado dentro de uma variável chamada reg, para não ter que passar esse valor toda vez eu só vou chamar reg e ele vai resolver. Podemos treinar o nosso modelo, posso fazer reg.fit() e eu passo a minha base de treino.

[00:53] Então X_train e y_train, ele treina na base de treino reg.fit. Posso rodar, como a regressão linear é um modelo mais simples, por mais que a minha base seja complexa ele vai rodar um pouco mais rápido.

[01:15] Terminou de rodar, eu posso fazer o predict e vou armazenar esse predict –quanto que ele previu para cada um desses usuários que está na base treino em uma variável chamada reg_predict = reg.predict, dei fit agora predict.

[01:32] Dessa vez na base teste, assim, X_test, posso rodar, agora dentro de reg predict eu já tenho as predições para minha base de teste e com isso eu posso avaliar a performance do meu modelo.

[02:00] Como vimos lá no primeiro curso, você vai continuar usando o RMSE para avaliar a performance do modelo e a gente pode calcular ele com outro biblioteca do sklearn também, que vamos importar from sklearn.metrics import mean_squared_error.

[02:28] Importa e vamos importar o numpy também, vamos chamá-lo de np. Pode calcular o RMSE que será a raiz quadrada do mean_squared_error; Np.sqrt, para calcular a raiz quadrada do número que eu vou passar aqui dentro e o que eu vou passar aqui dentro vai ser o mean_squared_error.

[02:59] Que vai ser o y_test e o reg_predict tudo isso fizemos no primeiro curso, estou falando para ele calcula raiz quadrada entre o y teste e quanto eu previ que seria o valor do Y teste, então passa x teste para ele criar as predições.

[03:26] Estou comparando com y teste e calculando o erro quadrático médio e tirando a raiz, executar, ele está falando um valor de 175.39, um erro bem alto. No próximo vídeo e vamos treinar um gradient boosting para ver se consegue reduzir esse erro.