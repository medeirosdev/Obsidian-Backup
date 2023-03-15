[00:00] Vamos agora entender melhor e aprender como calcular esses critérios que avaliam o grau de impureza dos nossos atributos para, aí sim, criarmos a nossa própria estrutura de árvore de decisão.

[00:15] Os principais critérios de divisão dos nós, são os seguintes: temos o índice Gini, o Qui-Quadrado, o Ganho de informação (entropia) e a Redução na variância.

[00:30] Os mais utilizados e que eu escolhi para trabalharmos com eles, é o índice Gini e o Ganho de informação, a entropia. Eles são os critérios mais utilizados e mais conhecidos, estou dando uma atenção maior a eles. Vamos entender melhor como funciona o índice Gini e esse cálculo de entropia.

[00:54] Primeiro o Índice Gini. Você já deve estar assustado com a matemática, mas calma que eu vou explicar por partes. Aqui temos a seguinte fórmula: temos o G que é de Gini, igual ao somatório da nossa probabilidade de uma classe ocorrer, vezes ou menos a probabilidade da classe ocorrer. Como assim probabilidade da classe ocorrer? Vamos lá.

[01:29] Esse Pk é a probabilidade de ocorrência de um dado da classe K. Temos o exemplo da Maria, meses de contrato maior que 50. Meses de contrato é o atributo, ele pode ser maior que 50 ou menor que 50, são os conjuntos resultantes, as classes resultantes desse dado. Nós vamos calcular a probabilidade de ocorrência para cada um desses valores, a probabilidade de ocorrer meses de contrato maior que 50 dividido pela ocorrência de todos os dados, todos os atributos, todas essas características, a ocorrência total dos meses de contrato. E da mesma forma para os meses de contrato menor que 50.

[02:29] Vamos pegar essa probabilidade e multiplicar pela probabilidade de não ocorrência de um dado da classe K. Nós vamos ter calculado essa probabilidade de qual é a chance da Maria ter meses de contrato maior que 50 entre todas as possibilidades, todas as ocorrências da nossa amostra dos nossos conjuntos de informações.

[02:56] 1 menos isso seria a probabilidade de não ocorrência. O cálculo final vai ser calculado essa probabilidade vezes a probabilidade de não ocorrência de cada uma dessas classes e somar os resultados. Vai pegar o resultado de meses de contrato maior que 50, meses de contrato menor que 50 e vai resultar em um valor.

[03:24] No caso do índice Gini, a ideia é medir o quão impuro está o dado, o quão heterogêneo ele está. Quando o resultado for próximo de 1, quanto maior o resultado mais heterogêneo o dado está, mais difícil de extrair informações, conseguir dividir este dado em diferentes classes.

[04:00] Agora, quanto menor mais homogêneo que seria o ideal. Se aplicarmos esse Índice Gini nos nossos atributos para decidir qual que é o nó raiz, aquele atributo que apresentar o menor Índice Gini vai ser o selecionado para começar a nossa árvore de decisão, é mais homogêneo.

[04:22] Agora, vamos para a entropia, como que a entropia funciona e qual é a ideia de calcular a entropia. A entropia mede a ordem dos dados, de certa forma a entropia e o Índice Gini é semelhante, até por isso que os dois são usados como critérios para verificar a impureza.

[04:40] Mas a entropia foca no ganho de informação, até outro nome conhecido e bem familiar que você pode encontrar por aí nos materiais.

[04:52] A entropia vai medir, falamos de desordem, se um dado está muito desordenado, ele está impuro. Vai ser mais difícil conseguir dividir esses dados ou extrair alguma informação dele.

[05:08] A entropia vai calcular esse ganho de informação, quanto maior a entropia mais desordenado está o dado e quanto menor mais ordenado está, maior ganho de informação. E ele é calculado da seguinte forma: menos o somatório, novamente, da probabilidade da ocorrência daquela classe, vezes o log da probabilidade da ocorrência daquela classe na base dois.

[05:39] Esse Pk é a mesma coisa do Índice Gini, qual a probabilidade de ocorrer, meses de contrato maior que 50. Vai ser meses de contrato dividido pela quantidade total de ocorrências na nossa amostra. Essa vai ser a probabilidade, aí vai multiplicar pelo log dessa probabilidade na base dois.

[06:00] Vai ser calculada para maior que 50 meses de contrato e menor que 50. Então, é realizado o somatório desses resultados obtendo a entropia. E da mesma forma que o Índice Gini é feito de forma recursiva, aplicando em todos os atributos e assim a nossa árvore crescendo e se estruturando.

[06:23] Agora que entendemos como funciona e como se calcula os critérios de decisão, tomada de decisão da divisão dos nós, vamos voltar ao Colab e aplicar de fato o nosso modelo.

O processo de construção de uma árvore de decisão envolve diversas etapas. Pensando nisso, assinale as alternativas que contêm informações corretas:

Selecione 2 alternativas

-   O índice de Gini nos dá a informação relacionada à impureza de um nó, ou seja, se o valor é igual a zero o nó é puro.
    
-   Caso a árvore seja muito profunda, pode ocorrer o sobreajuste dos dados de treinamento, também chamado de overfitting.
    
-   O nó inicial de uma árvore de decisão é conhecido como folha.
    
-   A árvore de decisão só funcionará quando os dados que estão sendo trabalhados estiverem normalizados.