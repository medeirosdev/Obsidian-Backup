Vimos como está o nosso gráfico de acurácia por épocas, e percebemos que os dados de treino estão mal, e os de validação estão piores ainda. Então vamos dar uma olhada, também, na perda da nossa rede para entendermos o que está acontecendo. Para isso scrollaremos para baixo e clicaremos em + Code para termos uma nova célula.

Plotaremos este gráfico com a mesma estrutura deste gráfico de acurácia, então na primeira linha temos acc, e em vez disso deixaremos a perda de treino, que é loss, e na segunda, no lugar de val_acc, teremos a perda de validação, val_loss. No título, teremos "Perda por épocas", no eixo X teremos épocas também, porque manteremos esta linearidade, e depois no nome do eixo Y teremos perda em vez de acurácia. E na legenda, que é para identificar qual linha é do quê, também teremos treino e validação.

Acabei de perceber que escrevemos avaliação, então alteraremos para validação o título da legenda. Como é a mesma estrutura, para ganharmos tempo, copiaremos todo o pedaço da célula e colaremos aqui embaixo, e alteraremos estas partes que acabamos de falar. E então podemos executar esta célula para vermos qual gráfico se formará em relação à nossa perda.

No nosso gráfico de perda por épocas, podemos ver que a nossa perda de validação parece ter decaído, enquanto a perda de treino está bem alta. Então, o que parece pelo gráfico de perda e acurácia é que a nossa rede não está se adequando bem aos nossos dados de treino, porque ainda está muito baixa a acurácia, enquanto a perda está muito alta.

Se repararem bem, este gráfico não está em 0.0, existe este +2.302. O que podemos entender destes plots de treino e acurácia é que nossa rede precisa fazer um ajuste no treinamento, parece que ela está servindo tão pouco para o treino, que está _underfitting_, como diríamos, encaixando pouco nos dados de treino, então como é que ela vai aprender o bastante para depois entender dados novos de validação?

Como é que decidimos o quanto treinamos a nossa rede?

Podemos dar uma olhada nestes gráficos. Quando a validação está alta e o treino está baixo, na perda, é mais ou menos pela época de número 10. Se observarmos a acurácia, em 10, a linha de validação está subindo, enquanto a de treino está descendo. O que podemos fazer agora é treinar a nossa rede por mais 5 ou 10 vezes para vermos qual resultado temos nos gráficos de validação e treino.

Alteraremos, então, o número de épocas que temos, de 5 para 10. E vamos rodar novamente o nosso modelo. Terminamos de rodar o modelo por 10 épocas, e agora veremos que resultados temos. Vamos executar novamente para vermos o output. No gráfico de acurácia por épocas teremos que os dados de treino saíram de quase 0 de acurácia, e aumentaram um pouquinho.

Então nossa rede já treinou melhor, mas em compensação nossos dados de validação estão até tentando subir, mas não conseguiram alcançar os dados de treino, que estão em quase 1. Também podemos analisar nossa perda para vermos o que aconteceu com ela. Veremos que a perda de treino decaiu bastante, ficando bem próxima de 0, mas a perda da avaliação está oscilando um pouco e pode ser que ela suba.

Então, o que estamos vendo é o oposto do _underfitting_. O nosso modelo está se adaptando tão bem ao treino que ele está _overfitting_, servindo demais aos nossos dados de treino e pouco aos de validação. Teremos que ver o que mais pode ser feito além de alterarmos o número de treinamentos.

Sobre isso, tem pessoas que dizem que uma métrica boa é treinar mais ou menos 30 vezes a sua rede, você pode testar e ver se funciona para você. E um parênteses que gostaria de fazer neste vídeo é que muitas vezes os seus gráficos podem sair diferentes desses, por conta da quantidade de vezes que sua rede treinou, por restartar ou não o Runtime, quantas vezes a célula de treinamento foi executada, e é bem provável que os gráficos saiam diferentes destes.

O interessante é saber como interpretar esse gráfico de perda, e esse de acurácia. Neste, se você perceber que a linha de treino está indo muito bem, enquanto a de teste está caindo, então terá um _overfitting_, ou seja, sua rede está entendendo o treino muito melhor do que a validação.

E também, na perda, se percebermos que o erro de teste está muito menor que o de validação, também deve ter algo a ser ajustado, porque estamos nesta situação de entendermos o treino bem demais. Já veremos como lidar com isso.