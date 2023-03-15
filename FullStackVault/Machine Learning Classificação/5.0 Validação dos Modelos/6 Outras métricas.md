## F1 score

Além da acurácia, precisão e recall, podemos extrair da matriz de confusão uma outra métrica conhecida como **f1 score**, que é uma média harmônica entre o recall e a precisão.O recall e a precisão são grandezas inversamente proporcionais, ou seja, à medida que vai aumentando o recall, por consequência irá diminuir a precisão e vice-versa.

O f1 score é uma métrica para identificar se algum dos valores de recall ou precisão estão baixos, uma vez que não é muito interessante ter um modelo com um alto recall e pouca precisão, ou vice versa. Então, caso sua intenção seja obter um valor equilibrado entre o recall e a precisão, a métrica que precisamos maximizar é o f1 score.

Para calcular, devemos utilizar a fórmula:

![alt text: Fórmula: f1 igual a 2 vezes o quociente entre dois termos. O numerador é o produto de precisão e recall. O denominador é a soma entre precisão e recall.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/05/Aula5-img2%281%29.png)

## Curva ROC e AUC

Existe ainda uma métrica conhecida como AUC (Area Under the Curve), ou área sob a curva, que pode ser extraída da curva ROC. Essa métrica tem valor máximo de 1 e quanto maior o número mais bem avaliado será o modelo de classificação. Para a construção da curva ROC, precisamos utilizar diferentes pontos de corte para avaliação do modelo de classificação.

É possível criar diferentes matrizes de confusão a partir dos diversos pontos de corte e extrair as métricas de recall (taxa de verdadeiros positivos) e taxa de falsos positivos. Sendo esta última, o valor de falsos positivos dividido pela soma de todos os valores negativos reais. Essas métricas podem ser sumarizadas em uma tabela e serão as coordenadas da curva ROC. Vamos entender como funcionam esses pontos de corte.

Na construção de um modelo de classificação, a predição de uma classe está atrelada a uma probabilidade. Imagine que temos uma variável alvo com duas possibilidades (0 ou 1). Se um modelo classifica uma observação como 1, significa que há uma probabilidade de x% de que aquela observação seja da classe 1.

O ponto de corte é um valor de probabilidade no qual, se a probabilidade de predição for maior que esse valor, atribui-se a observação à classe 1. Se for menor, atribui-se a observação à classe 0. À medida que o ponto de corte varia, os resultados obtidos na classificação se tornam diferentes, fazendo com que o modelo acerte mais de uma classe em troca de errar mais em outra.

Através de um exemplo, ficará evidente como os pontos de corte modificam as métricas da matriz de confusão. Na imagem abaixo estão representados a precisão e o recall. Nela estão definidos 3 pontos de corte em 25%, 50% e 75%, representados pelas setas verticais. Os zeros e uns são os valores reais das classes e a classificação será feita através dos pontos de corte. Os valores à esquerda da seta serão classificados como 0 e os valores à direita serão classificados como 1 pelo modelo.

![alt text: Sequência de zeros e uns na ordem: 001010110101. Esta sequência está demarcada por 3 setas, de cima para baixo, dividindo a sequência em 4 partes: 001, 010, 110, 101. Essas setas se conectam a outras 3 setas tracejadas localizadas abaixo da sequência de zeros e uns. As setas tracejadas partem da frase “Diferentes pontos de corte”, localizada na parte inferior. Na parte superior, há 3 valores de precisão e 3 valores de recall para cada ponto de corte na sequência. Sendo o primeiro valor de precisão: 5/9 = 55,5% e recall 5/6 = 83%; o segundo de precisão 4/6 = 66,6% e recall 4/6 = 66,6%; e o terceiro de precisão 2/3 = 66,6% e recall 2/6 = 33,3%.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/05/Aula5-img3.png)

No primeiro ponto de corte temos 3 valores classificados como 0, à esquerda; e 9 valores como 1, à direita. A precisão é dada por 5/(5+4) = 55,5%, mostrando que 5 valores foram classificados corretamente como 1, dentre 9 valores totais classificados como 1. O recall é dado por 5/(5+1) = 83%, indicando que 5 valores foram classificados corretamente como 1, dentre 6 valores reais 1 no conjunto de dados.

No segundo ponto de corte temos 6 valores classificados como 0 à esquerda; e 6 valores classificados como 1, à direita. A precisão é dada por 4/(4+2) = 66,6%, apontando que 4 valores foram classificados corretamente como 1, dentre 6 valores totais classificados como 1. O recall é dado por 4/(4+2) = 66,6%, demonstrando que 4 valores foram classificados corretamente como 1, dentre 6 valores reais 1 no conjunto de dados. O mesmo raciocínio pode ser aplicado para o último ponto de corte, resultando em valores diferentes para as métricas.

Para cada ponto de corte, uma matriz de confusão pode ser criada e as métricas podem ser extraídas em uma tabela, na qual cada linha representa um ponto de corte com suas respectivas métricas. Desta tabela, pode ser construído o gráfico da curva ROC. Esta curva mostra como o classificador se comporta para diferentes valores de pontos de corte, de acordo com a relação de verdadeiros positivos e falsos positivos.

![alt text: Gráfico de linhas. O eixo x representa o False Positive Rate com valores decimais 0.0 a 1.0, de 2.0 em 2.0. O eixo y representa a True Positive Rate, com valores decimais de 0.0 a 1.0, de 2.0 em 2.0. A legenda do gráfico contém uma linha azul representando RandomForestClassifier (AUC: 0.979), uma linha laranja representando DecisionTreeClassifier (AUC: 0.914) e uma estrela representando Youden’s J Statistic. Ambas as linhas iniciam no ponto (0, 0). A linha azul atinge aproximadamente o ponto (0.07, 1) enquanto a laranja atinge aproximadamente o ponto (0.17, 1). Ambas permanecem nos pontos mencionados anteriormente em linha reta até atingir o ponto (1, 1). Nesse ponto, encontram uma linha preta tracejada na diagonal.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/05/Aula5-img4.png)

Existe uma linha de referência na diagonal do gráfico que corresponde à uma linha de base e representa o caso no qual o classificador identifica aleatoriamente as classes. Mas como podemos interpretar esse gráfico?

Percebemos que a linha representando o classificador RandomForestClassifier cresce rapidamente até atingir o valor máximo de True Positive Rate (o recall). Isso significa que o modelo atinge 100% de classificação correta dos positivos e permanece até atingir o ponto (1, 1) do gráfico. Esse ponto nos diz que o modelo tem 100% de True Positive Rate e 100% de False Positive Rate (taxa de falso negativos), indicando que ele classifica todas as amostras positivas corretamente e todas as amostras que não são positivas foram incorretamente classificadas.

Então, quando o modelo chega no 100% de True Positive Rate e lá permanece até atingir o 100% do False Positive Rate, ele consegue classificar todas as amostras positivas de forma correta independentemente do threshold adotado. Por outro lado, a linha representando o classificador DecisionTreeClassifier demora mais para chegar no 100% de True Positive Rate. Porém, quando chega no valor máximo, permanece igual à do classificador anterior.

Esse pequeno atraso do DecisionTreeClassifier em relação ao RandomForestClassifier resulta em áreas diferentes, que são as AUCs para cada classificador. O primeiro teve uma AUC de 0.914 e o segundo 0.979. Portanto, esse último é o melhor classificador.