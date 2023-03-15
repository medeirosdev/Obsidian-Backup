[00:00] A última métrica que eu apresento a você é o _recall_. O _recall_ também é conhecido como revocação ou sensibilidade. Preste muita atenção, o _recall_ muitas vezes é confundido com a precisão, porque ele vai medir quão bom o nosso modelo está em classificar os resultados realmente positivos.

[00:29] Vamos ver a fórmula do _recall_. Verdadeiros positivos, que são aqueles que foram classificados como sim pelo nosso modelo e que são realmente sim, divididos pelos verdadeiros positivos mais os falsos negativos, "RC = TP/TP + FN". Entendeu a diferença?

[00:49] Aqui, os falsos negativos não deveriam ser positivos? Por isso que essa métrica é considerada aquela que calcula realmente quais os resultados verdadeiramente positivos. Vamos aplicar no nosso modelo e ver qual o resultado disso.

[01:06] Novamente vamos chamar a biblioteca _metrics_ e agora o `recall_store`, `from sklearn.metrics import recall_score`. Funções carregadas no _notebook_, vamos aplicar o nosso primeiro modelo o KNN: `print(recall_score(y_teste, predito_knn))`, tendo um resultado de 0,8391 ou em porcentagem 83,91%. É um valor muito alto, muito bom e quanto maior quer dizer que melhor está o modelo em classificar esses valores como sim, o nosso Churn sim.

[02:06] Vamos agora para o modelo Bernoulli de Naive Bayes. A mesma coisa, `print(recall_score(y_teste, predito_BNb))`. Já o nosso modelo de Bernoulli foi melhor, ele teve 84,24% de acertos. O nosso modelo está bom em acerta os sins.

[02:33] Lembrando, que o nosso Churn igual a sim é aquele cliente que realmente saiu da empresa, ele saiu, não faz mais parte, não tem mais contrato ativo, saiu da Alura Voz.

[02:48] Vamos agora para o modelo final, a árvore de decisão. A mesma coisa dos outros modelos, alterando somente para o `predito_ArvoreDecisao`. `print(recall_score(y_teste, predito_ArvoreDecisao))`, tendo o resultado de 81,96%.

[03:03] Olha que curioso, cada uma das métricas que apresentei para você mostrou que um modelo era melhor do que o outro. Tivemos a acurácia que trouxe o KNN como melhor modelo, tivemos a precisão que trouxe o modelo de árvore de decisão como melhor. E agora, na _recall_, na sensibilidade o melhor modelo é o Bernoulli de Naive Bayes.