[00:00] A próxima métrica que eu apresento a você é a Precisão. A Precisão calcula quantos verdadeiros positivos foram classificados de forma correta, foram preditos de forma correta. Como se calcula isso?

[00:21] Sabemos que os verdadeiros positivos são aqueles que foram realmente preditos como verdadeiro sim, a precisão é calculada da seguinte forma: o total de verdadeiros positivos dividido pelos verdadeiros positivos mais os falsos positivos, "PS = TP/TP + FP".

[00:41] Estamos pegando os verdadeiros positivos e dividindo pelo total de positivos previstos, seja ele correto ou não. Essa é a precisão, cálculo dos positivos corretos.

[00:57] Vamos implementar essa métrica para aplicar aos dados. Novamente, vamos chamar a biblioteca SKLearn e o pacote _metrics_ e agora vamos chamar a função `precision_score` e chamamos da mesma forma que as outras bibliotecas: `from sklearn.metrics import precision_score`.

[01:24] Funções também importadas, tudo carregado no nosso _notebook_, vamos agora mandar ver nossas precisões de cada um dos modelos.

[01:34] O primeiro modelo é o KNN: `print(precision_score(y_teste, predito_knn`. Da mesma forma das outras métricas, quais dados aplicamos na função o primeiro é o real e o segundo dado é o predito, classificado pelo nosso modelo.

[01:59] Vamos ver os nossos resultados e aqui está, para o modelo KNN temos uma precisão de 0,07971, em porcentagem 79,71%. Parece que a precisão dos positivos está menor que a acurácia.

[02:20] Agora vamos verificar o modelo de Bernoulli de Naive Bayes. Novamente, vamos mandar imprimir o nosso _score_ da precisão, `print(precision_score(y_teste, predito_BNb))`. Vamos ver, a precisão do modelo de Bernoulli também deu 71,37%.

[02:49] Vamos ver a árvore de decisão. Até agora o modelo KNN é o mais preciso em relação aos positivos. O modelo da árvore de decisão é 79,73%. No caso de escolhermos a métrica de precisão para mostrar para a equipe de vendas, o modelo da árvore de decisão seria o melhor modelo a se apresentar como o relatório, como resultado da classificação.

[03:17] Olha que curioso, cada uma das métricas apresentaram um modelo como melhor. A acurácia apresentou o KNN, a precisão apresentou o modelo árvore de decisão. Atenção à isso, lembre-se disso.