[00:00] Quando estamos trabalhando com probabilidade estatística é muito importante analisar e verificar a distribuição dos dados. A partir deles que conseguimos escolher os melhores testes estatísticos e também tirar _insights_ das nossas características, dos nossos atributos.

[00:20] A partir dessa distribuição dos dados vamos retomar o teorema de Bayes. O teorema de Bayes é a estrutura para todos esses classificadores de Naive Bayes. E onde que é alterado para cada um desses classificadores? Lembrando, que temos diversos tipos de classificadores de acordo com as distribuições dos dados.

[00:43] Seria Verossimilhança, que esse multinomial de Naive Bayes é colocado, é calculado. A Verossimilhança é a probabilidade de um conjunto de características X acontecer, sendo que a classe Y acontecer. Lembra do exemplo da Maria, qual que era a probabilidade dela não ser maior de 65 anos, sendo que ela tem um Churn igual a não. É isso que calcula a verossimilhança.

[01:15] Para cada uma das distribuições tem uma forma diferente de calcular. Na distribuição Multinomial de Bernoulli temos a seguinte fórmula: `p(xi\y) = P(i\y)xi + (1-p(i\y))(1-xi)`, que a probabilidade de Xi acontecer, o nosso conjunto de características dado que uma determinada classe aconteceu, ser igual a probabilidade de i dado a classe y vezes Xi mais 1 menos probabilidade de i dado y vezes um menos Xi.

[01:51] Vamos por partes. Primeiro vamos entender o que é Multinomial de Bernoulli. O Multinomial de Bernoulli é tipo de distribuição em que os dados estão apenas em variáveis binárias, ou seja, apenas dois valores dessa variável são possíveis, como no caso do nosso Churn, ou é sim ou é não.

[02:15] Esse tipo de distribuição, esse tipo de classificador é muito utilizado para classificações, tarefas de aprendizado de máquinas supervisionado. Agora vamos entender em partes como se calcula essa distribuição de Bernoulli.

[02:29] Começamos pela probabilidade de i dado que y aconteceu, essa etapa é conhecida como parâmetro P da distribuição de Bernoulli. Temos que lembrar o seguinte: o i pode ser um valor infinito de 1 até N, e o i é o número de características do nosso conjunto de variáveis. Lembrando da Maria, nós temos 38 variáveis, temos 38 Is, probabilidade de 1 dado que o y aconteceu. Lembrando que o Y é a classe.

[03:13] Vamos supor um Churn igual a não, qual a probabilidade dessa característica 1 acontecer sendo que o Churn não aconteceu, é esse parâmetro P da distribuição de Bernoulli. A próxima parte é o Xi que já é um velho conhecido, que é o conjunto de características. Vai ser aplicada essas informações para toda essa probabilidade, para todas as características. Temos um Xi como x1, x2, x3, x4 e assim por diante até o x38, como no caso da Maria.

[03:49] É assim que se calcula a verossimilhança, a probabilidade do conjunto i de características acontecer sendo que a classe y aconteceu.

[04:00] Vamos agora retomar o exemplo da Maria. Lembrando que a Maria não possui apenas valores binários de características, por exemplo, a cônjuge é sim ou não, só que a forma de pagamento é débito em conta, crédito, cheque, cheque digital, cheque em papel. Temos variáveis binárias e temos variáveis que não são binárias. Inclusive, o nosso Churn é uma variável binária, que só contém sim e não como possível.

[04:34] Como que trabalharíamos com classificador de Bernoulli nesse conjunto de dados? Vamos voltar ao Colab.