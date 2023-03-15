[00:00] A primeira métrica que eu apresento a você extraída da matriz de confusão é a acurácia. No nosso modelo a acurácia mede o quanto o nosso modelo acertou do total, do total de resultados o quanto que ela acertou.

[00:27] Temos a seguinte conta: a acurácia vai ser igual aos verdadeiros positivos mais os verdadeiros negativos. Você lembra da matriz de confusão? São os valores realmente corretos, os verdadeiros sins e os verdadeiros nãos no nosso Churn. Dividido por todos os resultados, os verdadeiros positivos mais os falsos positivos, mais os verdadeiros negativos mais os falsos negativos, resultando no total de valores inferidos de forma correta, classificados previstos de forma correta, "ACC = TP + TN/TP + FP + TN + FN".

[01:03] Para fazer o cálculo da acurácia vamos chamar o pacote métrico da biblioteca SKLearn e a função _accuracy_. `from sklearn,metrics import accuracy_score`. Vamos rodar e ok, as funções estão carregadas. Vamos ver a acurácia do nosso primeiro modelo, o quanto o nosso modelo realmente previu certo, classificou certo no total de resultados. Em todos os valores classificados o quanto ele realmente acertou.

[01:43] `print(accuracy_score(y_teste, predito_knn))`, o primeiro modelo é o KNN. Novamente, os primeiros dados a serem colocados na função da acurácia, do _score_ da acurácia é o conjunto Y teste, é o valor real. E o segundo valor é o predito pelo nosso modelo.

[02:09] Vamos verificar e obtivemos um resultado de 0.8148, se multiplicarmos por 100 temos 81,48% de acerto. É um valor alto, muito interessante.

[02:27] Vamos ver os outros modelos, qual entre eles está acertando mais. Agora o Bernoulli, da mesma forma que o modelo KNN vamos mandar imprimir: `print(accuracy_score(y_teste, predito_bnb))`, vamos verificar. O modelo Bernoulli teve um resultado de acurácia de 0,7549. Novamente, 75,49%, o modelo KNN até agora está ganhando.

[03:07] Se considerarmos a métrica da acurácia o modelo que apresentaríamos para a equipe de vendas seria o modelo KNN. Agora vamos verificar a árvore de decisão, a mesma coisa que os outros modelos, a única coisa que vamos alterar é o modelo, vamos colocar `predito_ArvoreDecisao`. Vamos mandar imprimir.

[03:36] O resultado do nosso modelo da árvore de decisão é de 80,77%. Se considerarmos o quanto o nossos modelos acertaram o melhor modelo para classificar os verdadeiros positivos e os verdadeiros negativos é o KNN. 81,48% e é esse modelo que apresentaríamos para a equipe de vendas.