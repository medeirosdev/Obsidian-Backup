[00:00] Vamos agora retomar alguns pontos importantes antes de ver a nossa primeira função desconhecida.

[00:06] Primeiro, o objetivo é classificar a nossa base de clientes em potenciais pessoas a deixarem ou não a nossa empresa, a Alura Voz.

[00:18] Durante esse processo de classificar as pessoas nós recebemos a informação de uma nova cliente, a Maria, e novos dados foram inseridos na nossa base. Porém, não sabemos ainda o seu Churn, mas devemos lembrar a Maria não é a única cliente, temos outros clientes na nossa base como, por exemplo, o Pedro, a Júlia e o João.

[00:43] Vamos agora pensar em suas características. Podemos pensar nesse conjunto de características e colocar em um gráfico distribuído da seguinte forma: logo acima, próximo ao eixo vertical X2 que é a característica 2, temos o Pedro. E logo acima a Júlia.

[01:09] No nosso eixo horizontal, X1, temos o João bem próximo desse eixo X1 que é a característica 1. Podemos perceber que a Júlia está mais próxima das características do Pedro do que das características do João.

[01:29] Podemos dizer que o Pedro e a Júlia, pela sua proximidade, pertencem ao mesmo grupo, ou seja, a mesma classe. Vamos supor aqui potenciais clientes a não deixar a Alura Voz.

[01:44] Agora o João apesar de se encontrar sozinho ele também possui um conjunto próprio de características e pertence a uma classe. Podemos dizer aqui no exemplo que o João pertence a classe dos potenciais clientes a deixarem a Alura Voz. E a Maria? Sabemos as informações da Maria, mas não sabemos o seu Churn, onde que ela seria classificada.

[02:09] E aí que entra a nossa função desconhecida, o método KNN, ou melhor, o K-vizinhos mais próximos. É um algoritmo de Machine Learning supervisionado, que pode ser usado tanto para tarefas de classificação quanto regressão. E funciona da seguinte forma: primeiro, o algoritmos vai receber as informações da Maria, menos o Churn que ainda não sabe, que vai querer calcular.

[02:39] Depois ele vai pegar as informações da Maria e calcular as suas distâncias da Maria com cada um dos clientes existentes na nossa base. Aqui no caso, Pedro, Júlia e João. Depois de calcular essas distâncias ele vai ordenar da menor distância até a maior e fazer uma contagem de quantas classes aparecem em cada uma dessas distâncias ordenadas.

[03:08] Depois disso vai classificar a partir de um número K-vizinhos, um número K desconhecido de vizinhos, definidos pela pessoa que está arrumando o algoritmo por nós, cientista de dados, qual é a quantidade de vizinhos que devemos classificar a Maria. E, assim, definir o seu Churn.

[03:30] Vamos ver na prática, no exemplo como que funcionaria isso. Temos aqui a Maria e recebemos o conjunto de informações da Maria, o algoritmo está aqui trabalhando, KNN, e trabalhando com os dados novos da Maria.

[03:46] Primeiro, ele vai receber esses dados e calcular a distância de todas as características da Maria com as características de todos os clientes da base. A característica do Pedro, da Júlia e do João, depois vai calcular essas distâncias. No caso aqui vamos supor que calculou através do método Euclidiano de distância.

[04:12] Obtemos a seguinte conta: 5 de distância até o Pedro, 8 de distância até a Júlia e 3 de distância até o João. Depois de calcular essas distâncias ele vai ordenar da menor distância até a maior, depois calcular quantas classes aparecem de cada um a partir de um número K definido de vizinhos.

[04:42] Vamos supor um vizinho mais próximo, `K = 11`, sabemos que o João é da classe que deixaria a Alura Voz, o Pedro e Júlia não deixariam a Alura Voz. Só que queremos o um vizinho mais próximo entre todos os calculados da distância da Maria. Que possuem a menor distância o 1 vizinho é o João, que possui distância 3 e pertence à classe dos que deixariam a Alura Voz.

[05:15] A Maria é classificada como uma potencial cliente a deixar a Alura Voz, o Churn é igual a 5. Agora, e se colocássemos outro valor de K como, por exemplo, um K=3, como funcionaria? Já temos tudo calculado, agora o algoritmo vai verificar os três vizinhos mais próximos, as três menores distâncias da Maria. Temos o João, Pedro e a Júlia.

[05:48] Temos três vizinhos mais próximos que pertencem a classes diferentes, qual que é a classe que mais aparece entre os três vizinhos mais próximos? É o do Pedro e da Júlia, porque temos apenas o João com uma pessoa potencial a deixar a Alura Voz e o Pedro e a Júlia como potenciais clientes a não deixarem.

[06:09] Como essa classe está em maior evidência quer dizer que a Maria possui mais características em comum com o Pedro e a Júlia do que com o João, e ela é classificada dessa forma. É assim que o algoritmo KNN vai funcionando, conforme for escolhendo novos valores para o K ele vai ajustando a sua classificação.

[06:30] Entendemos como funciona, vamos conferir na prática, no código. Vamos voltar ao Colab.O k-nearest neighbors (KNN) é um algoritmo de machine learning que pode ser utilizado para classificação. Para se chegar à previsão final, o KNN segue alguns passos em uma ordem específica.

Marque a alternativa que apresenta a ordem correta da implementação do algoritmo (KNN) de acordo com a numeração abaixo:

1.  Receber as características da amostra.
2.  A partir do número de K vizinhos desejados, escolher quais as características que mais se assemelham.
3.  Ordenar as distâncias obtidas da menor para a maior.
4.  Calcular a distância da amostra nova com as amostras já existentes.

Selecione uma alternativa

-   1, 2, 3 e 4
    
-   1, 4, 3 e 2
    
-   1, 3, 4 e 2
    
-   2, 1, 4 e 3
-

Separar o conjunto de dados em **treino** e **teste** é uma parte importante para conseguirmos medir o desempenho real de um modelo de machine learning. Essa etapa consiste em dedicar parte do conjunto de dados para treinar o modelo e uma outra parte para teste. Mas qual o motivo de fazer isso?

Imagine que você vai fazer uma prova e o(a) professor(a) passa uma atividade de revisão antes para treinar em casa. Chegando na prova, você percebe que as questões são exatamente iguais à revisão passada pelo(a) professor(a). Como você já sabia as questões, tirou 10! Isso é exatamente o que acontece quando utilizamos os mesmos dados para treinar e testar.

Como os dados são conhecidos pelo modelo, ele simplesmente vai acertar tudo (ou quase tudo) na etapa de teste, pois são os mesmos dados. Para resolver isso, dividimos o conjunto de dados em treino e teste, sendo este último para simular dados nunca antes vistos pelo modelo.

## Dados de treino

Os dados de treino são aqueles utilizados para a criação e treinamento do modelo. Normalmente a maioria dos dados, cerca de 70%, são utilizados para treinamento.

## Dados de teste

Os dados de teste são utilizados para comprovar que o modelo realmente funciona. Eles não são utilizados no treinamento do modelo e normalmente representam 30% da totalidade dos dados.

Além disso, no momento de realizar a separação desses dados é importante que ela seja feita de forma aleatória, para garantirmos que não haverá nenhum padrão no momento de divisão dos dados. Assim, cada amostra terá a mesma probabilidade de ser selecionada.