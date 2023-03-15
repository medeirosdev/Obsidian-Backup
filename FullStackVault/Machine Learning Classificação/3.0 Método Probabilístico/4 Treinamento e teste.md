[00:00] Estamos de volta ao Colab, nosso _notebook_. Para começarmos vamos relembrar o nosso conjunto de dados. Lembra que dividimos em treino e teste? Vamos rever o nosso conjunto de treino e de teste, como está dividido.

[00:21] "X_treino", vamos rodar e dar uma olhada. Temos valores -0,79024667, -0,5275638, -3, temos um 2,08, temos 1,89. Vamos ver agora o "y_treino", 0, 0, 1, ok. Tudo está certo, pré processado, dividido.

[00:53] Agora vamos, afinal de contas, aplicar nosso modelo, vamos implementar nosso modelo Bernoulli Naive Bayes. Para começar vamos fazer o seguinte, vamos importar a biblioteca do Scikit-learn, aquela biblioteca que falamos que íamos usar durante todo o projeto contendo diferentes modelos.

[01:19] Então, `from sklearn.naive_bayes import BernoulliNB`, vamos rodar e perfeito. Agora tínhamos uma questão que comentamos lá nos _slides_, o conjunto de dados que estamos trabalhando não contém somente variáveis binárias, porém a maior parte, incluindo a nossa variável classificadora, como você pode ver aqui no Y de treino, é binária, contém apenas dois valores possíveis.

[01:53] Algo muito interessante nesse modelo é que há um parâmetro chamado _binarize_. Nós definimos como se fosse um limite, um _trash route_, um limite para poder transformar aquela variável em binária ou não.

[02:19] Já que estamos trabalhando com probabilidade estatística, vamos utilizar a nossa mediana, que é o valor centra dos nossos dados ordenados. Vamos verificar qual é o valor da nossa mediana do nosso X de treino. Vamos escrever `np.median(X_treino)`, resultando um `-0,4461759755508453`, este é o nosso valor central.

[02:53] Eu optei, pensando em todas as probabilidades estatísticas, em utilizar a mediana, mas você pode utilizar diversas formas, a média dos seus dados, diversas formas estatísticas de se obter um valor central, de obter um valor ideal para dividir os nossos dados e definir como o limite.

[03:13] Agora vamos pegar esse -0,4461759755508453, colocar no nosso modelo que seria da seguinte forma, primeiro criamos a variável para receber o nosso modelo instanciado igual a Bernoulli, abre e fecha parênteses, chamamos o nosso parâmetro _binarize_ igual a -0.44, `bnb = BernoulliNB(binarize=-0,44)`.

[03:40] Vamos rodar e aqui está. Vamos entender melhor como _binarize_ funcionou, esse -0.44 definiu que acima desse valor vai transformar as variáveis que contém valores acima em 1, os valores abaixo em 0 e assim se torna uma variável binária.

[04:04] Agora que o nosso modelo está pronto para pegar todos os nossos dados e transformar em variáveis binárias, vamos pegar este modelo e aplicar no nosso conjunto de treino. Vamos começar treinando o nosso modelo.

[04:19] `bnb.fit(x_treino, y_treino)`, vamos rodar e pronto, aqui está o nosso modelo treinado. Vamos ver agora como ele está realmente funcionando, vamos testar a eficácia, a eficiência deste modelo.

[04:45] Primeiro criamos a variável `predito_Bnb = bnb.predict(X_teste)`, estamos aplicando o modelo no nosso conjunto de teste e vendo se ele consegue predizer o nosso y. Vamos ver o que resultou depois de rodar e temos o `predito_Bnb` e aqui está o nosso _array_ de resultados, `array([1, 0, ..., 1, 1, 1])`.