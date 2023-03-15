[00:00] Estamos de volta ao Colab e agora vamos começar importando as bibliotecas que iremos utilizar para poder criar nosso modelo.

[00:11] Começamos importando o pacote _Tree_ da biblioteca SKLearn.

```javascript
from sklearn tree import DecisionTreeClassifier
```

Vamos rodar e ok. Após importarmos essas funções, importarmos o nosso modelo, precisamos criar o modelo de fato, instanciar esse modelo.

[00:38] Novamente, criamos uma variável para armazenar este modelo, eu vou criar o `dtc =`, chamamos a `DecisionTreeClassifier`, abre e fecha parênteses. Como vocês puderam ver nas aulas anteriores, a árvore de decisão possui diversos parâmetros, parâmetros de crescimento, parâmetros de critério de divisão, temos também a questão do _random state_, de possibilitar a reprodutibilidade dos resultados.

[01:19] Aqui, eu escolhi mostrar para você apenas o critério e o _random state_, porque o que eu rodar aqui você vai conseguir rodar aí e ter o mesmo resultado. Vamos definir o critério, `dtc = DecisionTreeClassifier(criterion ='entropy'`, eu escolhi _entropy_, vamos como funciona e se adequa ao nosso modelo.

[01:45] Lembrando, que quando estamos trabalhando com a árvore de decisão e qualquer outro modelo, o ideal é nós tentarmos e avaliarmos diferentes parâmetros para este modelo e ver aquele que obtém o melhor resultado, a melhor classificação.

[02:03] Vamos definir vírgula `random_state=42`, que esse é o nosso estado de aleatoriedade para poder reproduzir os resultados. Rodamos a célula e o modelo foi criado e instanciado e podemos partir para o treino.

```ini
dtc = DecisionTreeClassifier(criterion='entropy', random_state=42)
```

[02:21] `dtc.fit` e chamamos nossos conjuntos de treino `dtc.fit(x_treino, y_treino)`. O modelo está treinado.

[02:35] Algo muito interessante que temos, uma função muito interessante que tem na pasta, no pacote da _Decision Tree_, é a função de verificar a importância da _features_, a importância dos atributos nesse modelo, na árvore.

[02:54] Eu trouxe para mostrar a vocês, claro que depois você pode pesquisar, olhe com calma, mas é muito interessante verificar. `dtc.feature_importances_`, vamos rodar. Como você ver e relembrar que quanto menor o valor mais homogêneo é, de acordo com a entropia, maior ganho de informação.

[03:20] Vamos olhar aqui. Temos a primeira variável que é a questão de ser maior de 65 anos ou não e assim por diante. Temos aqui 0.021, tem 0.01, 0.006, dá para ver as diferenças. Têm valores de atributos mais importantes do que outros para classificar os nossos clientes.

[03:51] Agora vamos aplicar no teste para realmente ver a eficácia do nosso modelo. Vamos criar a variável para armazenar esse resultado: `predito_ArvoreDecisao = dtc.predict(x_teste)`. Pronto, funcionou, modelo testado. Vamos ver os resultados, `predito_ArvoreDecisao` e aqui está um pequeno trecho do nosso resultado do nosso Churn.

[04:30] Agora, vamos verificar como escolher o nosso melhor modelo a apresentar para a equipe de vendas.O DecisionTreeClassifier é um modelo de machine learning utilizado em problemas de classificação. Ele é inspirado na forma que os seres humanos tomam as decisões e tem uma alta explicabilidade.

Assinale as alternativas que apresentam problemas que podem ser resolvidos utilizando o `DecisionTreeClassifier`:

Selecione 2 alternativas

-   Previsão de valores de imóveis residenciais.
    
-   Identificar se um(a) paciente ficará doente a partir de exames anteriores.
    
-   Previsão do valor de empréstimo que pode ser concedido à clientes de um banco.
    
-   Predição de saídas de pessoas colaboradoras de uma empresa.