[00:00] E aqui estamos com a matemática de volta para nos ajudar a entender melhor como o algoritmo KNN funciona por trás dos panos.

[00:09] Você deve ter percebido que o algoritmo KNN é um algoritmo simples, é um método simples que pode trazer bons resultados, porém muitas vezes ele é incerto.

[00:22] O algoritmo KNN recebe um dado novo, calcula as suas distâncias, ou seja, esse dado novo com os demais dados do conjunto, do _dataset_. Vamos pensar na Maria, temos a Maria e vamos calcular a distância da Maria com os demais clientes do nosso conjunto de dados.

[00:39] A partir daí, a partir de K selecionado por você o algoritmo irá classificar a Maria, classificar esse dado novo. Como você pôde perceber, a classificação é interferida diretamente pelo valor de K e alguns problemas podem ocorrer como, por exemplo, caso o K seja muito pequeno pode ocorrer um _overfitting_ do modelo.

[01:11] Isso quer dizer que o modelo, o algoritmo KNN vai se ajustar perfeitamente aos dados de entrada, ao X dos nossos clientes. E quando chegar essa informação da Maria, esse dado novo não vai conseguir classificá-la de forma correta porque ele só vai conseguir classificar valores iguais a aqueles nossos dados que usou para treiná-lo.

[01:42] Agora, no caso de um K muito grande pode ocorrer um _underfitting_. O nosso modelo vai ver um número muito grande de vizinhos, muitas classes e não vai conseguir identificar a classe correta de cada variável, de cada cliente. Ele vai classificar de forma errada também.

[02:09] Já entendemos que o K influencia diretamente na nossa classificação, por isso é importante testarmos diferentes valores de K. Outro ponto muito importante é a questão da métrica de distância, também é importante testar diferentes métricas afim de obter a melhor classificação possível do seu modelo.

[02:34] Vamos retomar o conjunto de informações da Maria. O nosso vetor de características da Maria é o `Xmaria`, temos aqui o Xmaria contendo todas as informações que apresentamos ao nosso cientista que é você. Agora, nós não temos o Ymaria que é o que queremos saber.

[02:58] Vamos calcular a distância da Maria com o nosso conjunto de dados, a primeira etapa do algoritmo. A distância na Maria com todos os outros clientes. Primeiro, vamos dividir o nosso conjunto de dados em X e Y, nossos dados de entrada e os nossos dados de saída.

[03:21] Então, com `X = dados_final.drop('Churn', axis = 1)`, estamos dizendo que o nosso X são todas as características menos a nossa coluna Churn que é o Y, o nosso conjunto de dados de saída e o _axis_ quer dizer coluna. Agora o nosso `Y = dados_final['Churn']`, o Churn indica que o Y é a coluna Churn do nosso conjunto de dados final.

[04:04] Agora vamos calcular a distância da Maria com esses clientes. Antes de calcularmos a distância algo muito importante de se fazer por se tratar de uma métrica de distância é deixar todos os valores na mesma escala. Vamos fazer isso utilizando a biblioteca do Scikit-lern, que você verá durante todo o projeto na implementação dos modelos.

[04:32] Também utilizaremos o pacote _pré-processing_, que é uma etapa do pré-processamento e tratamento dos dados e a função _Standard Scaler_. Vamos carregar esse conjunto de funções para aplicarmos nos dados, `from sklearn.preprocessing import StandardScaler`.

[04:57] Agora vamos chamar a função. Essa função de normalização vai pegar cada um dos atributos do nosso conjunto X, por exemplo, X da Maria e o X dos clientes, vai pegar cada um dos atributos, subtrair a média desse conjunto e fazer a divisão pelo desvio padrão. Para realizarmos essa matemática nesse conjunto de funções no nosso X precisamos primeiro instanciar essa função.

[05:33] Criamos uma variável chamada `norm = StandardScaler()`, pronto, temos uma variável contendo a nossa função. Agora, vamos pegar essa função e aplicar no nosso conjunto X de clientes. Então x_normalizado, que irá armazenar esses dados normalizados é `x_normalizado = norm.fit_transform(x)`.

[06:02] Vamos ver se funcionou. Escrevemos o `x_normalizado` logo abaixo para ver o resultado. E aqui está, temos vários conjuntos de clientes, aqui o cliente 0, logo abaixo o cliente 1, cliente 2 e assim por diante. Funcionou.

[06:25] Vamos agora verificar um desses clientes, ver todas as informações dele e como foi normalizado. `X_normalizado[0]`, queremos o cliente 0, é o primeiro cliente do nosso conjunto. Vamos rodar novamente e aqui estão todas as características normalizadas, na mesma escala.

[06:51] Vamos agora normalizar a Maria porque normalizamos somente o X do nosso conjunto de dados dos clientes, vamos normalizar o X da Maria.

```ini
Xmaria_normalizado = norm.transform(pd.DataFrame(Xmaria, colums = X.colums))
```

Essa função tem uma pequena peculiaridade, ela só é clicada quando o nosso conjunto de dados está em formato de duas dimensões. Isso quer dizer que é um conjunto de informações formado de linhas e colunas, a Maria está um vetor de características.

[07:31] Vamos ter que transformar a Maria em um conjunto de linhas e colunas, definir as linhas e as colunas da Maria para então aplicar a função de normalização. E é isso que fazemos aqui, chamamos a função da biblioteca Pandas DataFrame, que aí vai transformar o vetor da Maria em um conjunto de linhas colunas contendo as mesmas colunas do nosso conjunto X.

[07:59] Vamos verificar se funcionou e perfeito, aqui está o nosso `Xmaria_normalizado`, com todos os dados na mesma escala, agora sim. Vamos utilizar como exemplo o cálculo da distância da Maria com o cliente 0. Existem várias métricas de distância, mas a que vamos utilizar hoje será a Euclidiana que funciona da seguinte forma, ela é a raiz quadrada do somatório da diferença de todos os atributos, todas as características elevada ao quadrado.

[08:43] Você deve estar imaginando que loucura é essa. Vamos ver passo a passo e vocês vão poder aplicar e entender melhor cada etapa da distância Euclidiana como é feita. Aqui utilizando a Maria e o cliente 0 da nossa base.

[09:00] Vamos chamar as funções da biblioteca Numpy para facilitar as nossas contas, `import numpy as np`, estamos apelidando np para facilitar chamar. Começamos criando um nome, vamos chamar esse A do conjunto normalizado de informações da Maria, o `a = Xmaria_normalizado` e o b da nossa fórmula é o `b = X_normalizado[0]`.

[09:40] A primeira etapa dessa função de distância Euclidiana vai ser subtração de cada uma das características da Maria com o cliente 0. Por exemplo, a Maria não tem cônjuge, o cliente 0 tem, vai ser `0 - 1`. Vamos começar assim, e ele vai fazer isso para todas as características. `a - b` e aqui está o nosso conjunto subtraído.

[10:11] Agora, depois da subtração de cada uma dessas características vai elevar ao quadrado. Vamos fazer a exponenciação dessa subtração e nós temos aqui esse conjunto de _array_. Depois da exponenciação vem a soma, ele vai pegar o somatório de todos esses resultados, o somatório dessa exponenciação é esse valor `84.07574038273466`.

[10:49] Vamos pegar esse valor, `Ctrl + C` copiar e vamos tirar a raiz desse valor e colocamos na seguinte função: `np.sqrt(84.07574038273466)`, pronto aqui está a distância da Maria com o cliente 0 da nossa base, é `9.169282435541762` e aqui temos a distância da Maria.

[11:23] A partir de então o algoritmo vai calcular a distância da Maria com o cliente 1, 2, 3 e assim por diante, até o último cliente da nossa base de dados. Depois a partir do K, que você definirá, ele vai poder classificar a Maria como uma possível cliente a deixar ou não a Alura Voz. Vamos implementar esse modelo agora.