[00:00] Vamos treinar o gradient boosting para ver se conseguimos reduzir esse erro, do mesmo jeito dos outros testes vamos importar o gradient boosting do sklearn, ele está dentro da parte de ensemble, import GradientBoostingRegressor, da mesma forma da regressão linear instancia uma variável, faz o fit, faz o predict e avalia a performance.

[00:37] Então dessa vez eu vou chamar a variável de gb = GradientBoostingRegressor(), faço gb.fit(X_train, y_train) = como gradient boosting é uma biblioteca, um modelo um pouco mais complexo, então vai demorar um pouco mais para rodar, vamos esperar.

[01:20] Já terminou de rodar, meu modelo está treinado dentro da variável gb, posso fazer o predict assim como fiz para regressão linear, então, gb_predict = gb.predict(X_test).

[01:39] Ele vai fazer a predição e eu já posso fazer uma “coisinha” com esse predict, caso eu tenho uma predição com um valor menor do que zero, eu vou converter para zero, porque se entende que em condições normais não vai ter um usuário com o valor de compras negativo.

[02:02] Vou fazer gb.predict[gb_predict , ] menor que zero é igual a zero, então essa linha aqui vai selecionar todos os que tiveram a predição menor que zero e converter esse valor para zero.

[02:22] Vai ajudar o nosso modelo a ter uma performance melhor caso isso aconteça, podemos olhar de novo como ficou o RMSE, só que no lugar da regressão vou selecionar o gradient boosting.

[02:40] Eu tenho RMSE de 40.82, teve uma grande melhora entre a regressão linear e o gradient boosting. Lembrando que temos uma base bem complexa, provavelmente várias dessas colunas não fazem tanto sentido para o modelo e o que pode ser o motivo da nossa regressão linear estar com a performance assim.

[03:04] Ela precisava ter um trabalho um pouco mais cuidadoso, selecionando as variáveis, cuidando da distribuição, normalizando as variáveis, requerer um trabalho um pouco mais cauteloso para conseguir ter uma regressão linear melhor.

[03:18] No gradient boosting ele já conseguiu trabalhar com essa base um pouco mais confusa e trazer um resultado melhor, vamos avaliar igual fizemos no primeiro curso um Dataframe com as informações de um um só para dar uma olhada como que estão ficando essas predições.

[03:42] Vamos criar aqui um Dataframe chamado resultado que será igual pd.DataFrame ou simplesmente criar Dataframe nesse primeiro passo; a primeira coluna desse Dataframe vai ser o revenue - que é quanto que o usuário gastou mesmo.

[04:02] E ela vai ser o nosso y do teste que estávamos tentando prever, outra coluna que vai ser quanto que achou que esse usuário ia gastar predict vai ser igual gb_predict e o nosso erro que vai ser o predict menos o y teste.

[04:24] Vou molhar como ficou, nossas primeiras linhas eu estou vendo vários usuários que não gastaram nada, eu tive uma predição de 0.2 uma pressão bem baixa para usuários que não gastaram nada.

[05:00] O que pode fazer para melhorar a performance do nosso modelo é verificar o limite mínimo de usuários e o limite mínimo de valor gasto e citar abaixo desse limite, colocar para 0.

[05:13] Vamos testar outras coisas antes, mas é uma técnica que pode fazer também, vamos supor qualquer coisa menor que 1 é 0, ele pode errar em alguns casos. Mas pode ajudar a ter algo mais próximo da realidade.

[05:28] Pode olhar como ficou esse resultado para os usuários que gastaram alguma coisa. Resultados.revenue maior do que zero e dar uma olhada como é que ficaram as predições para os usuários que realmente gastaram alguma coisa.

[05:48] Alguns erros muito grandes como esse aqui que ele gastou 32 e previmos 516, outros bem próximos, então esse usuário que ele gastou 34,58 previmos 38. Para usuários que gastaram parece que está trabalhando, tentando prever em alguns casos acerta, em outros um erro um pouco maior.

[06:12] Então, vamos continuar trabalhando em cima desse modelo para tentar melhorar a nossa performance.