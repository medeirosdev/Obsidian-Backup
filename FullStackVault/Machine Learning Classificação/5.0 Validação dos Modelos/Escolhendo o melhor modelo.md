[00:00] E agora, qual o modelo que nós escolheremos para apresentar para a equipe de vendas? Qual o modelo classifica melhor nossos clientes?

[00:10] Eu escolhi utilizar a precisão. A precisão vai medir quantos valores positivos foram previstos de forma correta com um todo no nosso modelo. Lembrando que os verdadeiros positivos são os sins, é aquele Churn igual a sim. É aquele Churn que precisamos dar atenção, é o Churn que temos que reduzir, são as pessoas que estão deixando a nossa empresa, estamos deixando de lucrar, a Alura Voz está perdendo com esses clientes saindo.

[00:44] É um valor que temos que estar atentos, o nosso modelo tem que saber prever bem esses valores para podermos criar ações, tomar decisões em cima desses clientes.

[00:57] Eu escolhi utilizar a precisão. Porém, outra métrica muito interessante seria a _recall_, sensibilidade porque agora sim, ele mede o verdadeiro positivo, seria até melhor que a precisão. Contudo, por escolha que eu achei mais interessante para vocês é a precisão.

[01:17] Com isso concluímos que para escolher a melhor métrica para aplicar ao nosso modelo, para obter o melhor resultado, até para apresentar em seus relatórios, nas suas entregas, depende do dado que você está trabalhando, depende do problema que você quer solucionar.

[01:38] Por isso, muita atenção. Entenda bem o seu problema, entenda bem a solução que você tem que correr atrás porque é a partir daí que você vai saber mudar todo o seu processo de modelagem, criação e validação de resultados.

[01:54] Vamos verificar e escolher o melhor modelo. Vamos fazer um _print_ de todos os resultados: `print()`, eu coloquei entre aspas `'Modelo KNN:'`, para indicar qual é cada um desses resultados, `print('Modelo KNN:', precision_score(y_teste, predito_knn))`.

[02:18] E aí fazemos um "Ctrl + C" "Ctrl + V" aqui e só muda também os modelos para `predito_BNb` e `predito_ArvoreDecisao` e os nomes também `Modelo Bernoulli de Naive Bayes` e `Modelo Árvore de Decisão`. Então:

```bash
print('Modelo KNN:', precision_score(y_teste, predito_knn))
print('Modelo Bernoulli de Naive Bayes:', precision_score(y_teste, predito_BNb))
print('Modelo Àrvore de Decisão:', precision_score(y_teste, predito_ArvoreDecisao))
```

[02:34] Rodamos. Se você estiver atento vai perceber que o melhor modelo para a nossa equipe de vendas é o modelo de Árvore de Decisão, que apresentou 79,73% de acerto. 79,73% é um valor muito bom, muito interessante, entre todos os outros foi o melhor.

[02:59] O KNN chegou bem perto, com 79,71% e o Bernoulli de Naive Bayes talvez precisamos melhorar um pouco mais, porque acerto 71,37%. Não é um resultado ruim, mas a Árvore de Decisão foi melhor.