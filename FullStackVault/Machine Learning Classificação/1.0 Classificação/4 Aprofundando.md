Existem duas categorias de problemas que podem ser bem resolvidos com a utilização de Machine Learning: os de classificação e os de regressão.

## Classificação

Quando precisamos **prever a qual categoria pertence uma determinada amostra**, trata-se de um problema de **classificação**. Alguns exemplos que podemos citar são:

-   Prever se um(a) determinado(a) paciente está com Covid.
-   Se um(a) cliente está propenso(a) a desistir da compra.
-   Se algum(a) usuário(a) web está propenso(a) a clicar em um anúncio.

Nesses casos mencionados, a previsão se concentra em 0 ou 1 (Covid/não Covid, desistir/não desistir, clicar/não clicar) que é denominada de **classificação binária**, na qual existem somente duas classes. Há também casos em que a classificação se dá com mais duas classes, chamada de **classificação multiclasse**, como a filtragem dos e-mails em “principal”, “social”, “promoções”, “importantes” ou “fóruns”.

Entre os algoritmos de classificação podemos citar:

-   [K-Nearest Neighbors (KNN)](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)
-   [Support Vector Machine (SVM)](https://scikit-learn.org/stable/modules/svm.html)
-   [Decision Tree Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)
-   [Random Forest Classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)

## Regressão

Quando precisamos **prever um valor numérico específico**, isso indica que estamos lidando com um problema de **regressão**. Alguns exemplos desses problemas estão relacionados à previsão de:

-   preços/custos futuros;
-   estoque;
-   receita futura.

Nessas situações, podemos utilizar algum modelo de regressão para realizar essas previsões e apresentar como resposta algum valor contínuo relacionado ao problema. Existem diferentes tipos de algoritmos de machine learning utilizados para resolver esse tipo de problema:

-   [Linear Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html);
-   [Random Forest Regressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html);
-   [Support Vector Regression (SVR)](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVR.html).

Caso queira aprofundar e conhecer mais sobre algoritmos de regressão, deixamos aqui a indicação de dois cursos que abordam esse assunto:

-   [Regressão Linear: Testando Relações e Prevendo Resultados](https://cursos.alura.com.br/course/data-science-modelo-regressao-linear);
-   [Regressão Linear: Técnicas Avançadas de Modelagem](https://cursos.alura.com.br/course/data-science-modelo-regressao-linear-assimetria-statsmodel).Os algoritmos de machine learning possuem diferentes aplicações e devem ser utilizados de acordo com cada problema proposto. Existem dois tipos principais de problemas que podem ser resolvidos utilizando esses algoritmos, sendo eles: classificação e regressão.

Com base nisso, considere as situações abaixo:

1.  Realizar a previsão se determinado e-mail é spam;
2.  Realizar a previsão do preço da gasolina em determinada época;
3.  Realizar a previsão se o(a) paciente irá para a UTI.

Quais tipos de algoritmos de machine learning podem ser utilizados para realizar cada uma das tarefas listadas acima?

Selecione uma alternativa

-   Classificação, regressão e classificação
    
-   Classificação, classificação e classificação.
    
-   Classificação, regressão e regressão.
    
-   Regressão, classificação e regressão.