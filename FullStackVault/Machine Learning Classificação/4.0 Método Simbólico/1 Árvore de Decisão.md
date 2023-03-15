[00:00] Estamos quase alcançando o nosso objetivo que você, cientista de dados, sugeriu classificar os novos clientes em potenciais candidatos a deixar ou não a Alura Voz.

[00:10] Nesse processo nós recebemos o conjunto de dados da empresa, fizemos o tratamento, balanceamento, recebemos as informações da Maria, nossa nova cliente, e também aprendemos mais sobre o que é classificação e como as funções funcionam nos algoritmos de Machine Learning. Além disso, aplicamos dois modelos: o KNN e o Bernoulli Naive Bayes.

[00:35] Vamos agora ver o exemplo da Maria, dar uma olhada com outra visão, com outros detalhes nas características dela.

[00:45] Temos aqui a primeira variável, os meses de contrato, se recapitularmos o exemplo da Maria, meses de contrato maior que 50 meses. A Maria é uma nova cliente, não completou ainda nenhum um mês na empresa, isso quer dizer que essa variável vai seguir para o lado direito, vai para o falso. A próxima variável que está indicando é o tipo de internet que a pessoa contratou, a que a Maria contratou, que está dizendo igual à fibra óptica.

[01:19] A Maria contratou o serviço de fibra óptica da empresa Alura Voz, vamos para o lado esquerdo desse fluxo, vamos para o verdadeiro. Nesse exemplo a Maria foi classificada com um Churn igual a não, a Maria é uma potencial cliente a não deixar a empresa Alura Voz.

[01:41] E como você pôde ter percebido, esse fluxo de decisão é utilizado no algoritmo de Machine Learning a Árvore de Decisão ou _Decision Tree_. Esse modelo pode ser usado tanto para tarefas de classificação quanto regressão, que prevê classes ou valores de Y a partir de decisões simples inferidas a partir dos dados de treino.

[02:08] Esse modelo parece ser muito interessante para o que queremos fazer com os dados dos clientes. Vamos entender melhor quais são as suas estruturas e as suas terminologias.

[02:21] Tudo começa no nó raiz, que é aquele nó onde é escolhido o melhor atributo para dividir os nossos dados. Para fazer essa escolha é aplicado um critério de impureza, ou seja, ele verifica o quão puro é um atributo, o resultado desse atributo tem que ser conjuntos homogêneos. Ele vai pegar e avaliar todos os atributos do nosso conjunto.

[02:56] Após ter selecionado o melhor atributo para dividir esses dados a partir desses critérios, nós dividimos em outros dois nós: verdadeiro e falso. E eles se tornam os nós de decisão, que a partir deles é tomado outra decisão, é feita de um formato recursivo a aplicação do critério de verificação da impureza. Novamente, vai aplicar esse critério em todos os atributos e escolher nesses nós de decisão quais são os atributos que melhor dividem os dados.

[03:34] A partir desses nós de decisão, vão surgir outros nós e assim a árvore vai se expandindo de acordo com o seu fluxo e com a aplicação desse critério nos atributos. Aqui no nosso exemplo, a partir do nó de decisão é dividido em outros dois nós e encerrada a nossa árvore. Esses nós finais são conhecidos com nó folha ou nó terminal.

[04:02] Isso significa que esse nó é o nó onde tomamos a decisão, é o nó da nossa variável classificadora, o nosso Churn. Retomando ao exemplo da Maria, o nosso nó raiz seria os meses de contrato maior que 50 e os nós folha o Churn, e os nós de decisão seria o caso do tipo de internet que abrirá outros dois caminhos.

[04:33] Outros termos muito interessantes de se conhecer é o nó pai e o nó filho. O nó pai seriam todos os nós de decisão, que a partir dessa decisão surge outros dois resultados que são os nós filhos. Por exemplo, temos uma raiz, o nó raiz é pai de outros dois nós de decisão.

[04:59] Agora, existe outra terminologia que é muito interessante que é nessa questão das árvores crescerem, a sub árvore. A árvore vai crescendo, pode ser que se torne uma forma complexa e surjam essas ramificações, essas mini árvores, sub árvores, que tem justamente esse formato: nó de decisão, outros dois nós e vai se estruturando outra árvore dentro da árvore. Parece confuso, mas é muito intuitivo.

[05:35] E falando em intuição, essa é uma das vantagens de se utilizar o modelo árvore de decisão. Além de ser intuitivo, fácil de entender por você conseguir enxergar o fluxo dos dados do início até o final até a variável classificadora, ela também não necessita obrigatoriamente realizar tratamento nos dados. Não é obrigatório normalizar, fazer a limpeza para aplicar esse modelo porque ela não é tão sensível a _outliers_, a essas transformações.

[06:12] E até pensando na transformação de variáveis, por exemplo, categóricas para numéricas, esse não é um dos problemas também porque a árvore de decisão trabalha tanto com essas variáveis categóricas quanto numéricas. Por isso não há esse problema também de ter que transformar esses valores.

[06:31] Claro, nada é perfeito. Temos também as desvantagens da árvore de decisão, que a primeira seria a possível ocorrência de um _overfitting_. Isso quer dizer que a árvore vai crescendo tanto e tornando-se uma estrutura tão complexa que ela vai se ajustar perfeitamente àqueles dados de treinos. E ao surgir os novos dados, por exemplo, os dados da Maria a nova cliente, a árvore não vai conseguir tomar decisões para os dados dela porque ele foi ajustado perfeitamente aos nossos dados de treino, não vai conseguir classificar a Maria de uma forma adequada.

[07:15] Outra desvantagem também é em relação até a esse crescimento, que seria a instabilidade da árvore de decisão. Qualquer mudança que for feita em qualquer parte da árvore, ela vai gerar uma árvore nova. Por isso deve-se tomar muito cuidado e atenção na hora de montar e estruturar essa árvore, fazer os tratamentos se desejar ou não fazer, deve-se ter bastante atenção.

[07:42] Nós entendemos como funcionam as principais terminologias para entender a árvore de decisão. Vamos agora entender melhor quais são esses critérios para decidir o melhor atributo a se dividir o dado. Como se calcula esses critérios?