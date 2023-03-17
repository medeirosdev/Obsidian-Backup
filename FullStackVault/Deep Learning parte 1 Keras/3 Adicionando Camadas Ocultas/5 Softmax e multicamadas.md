Fiquei de falar para vocês que tipo de função, e o que iremos usar na nossa camada de saída do modelo que estamos fazendo. Trouxe um exemplo de quatro imagens e cinco categorias para vermos o que faremos nesta camada. Vamos concentrar na primeira imagem, que sabemos, mas a nossa rede não sabe, que é uma camiseta.

Se pegarmos esta camiseta e ligarmos à sua categoria correta, seria Camiseta. Mas se não soubéssemos disso e chutássemos uma probabilidade disso estar correto, seria 67%, por exemplo. Agora se ligarmos a camiseta com a categoria Saia, qual a probabilidade disso estar correto? 11%. Com Calça, 8%, Bota, chutamos 2%, e Vestido, 12%.

Agora, temos probabilidades para cada tipo de identificação ligada à imagem que estamos analisando. Então, podemos agrupar tudo isso, após o qual podemos dividir todas estas probabilidades e valores por 100. Então, ficaremos com decimais: 0.11, 0.67, 0.08, 0.02 e 0.12. E então queremos agrupar estes valores, e colocá-los dentro de um array.

Vamos fazer isso! Além disso, queremos somar todos estes valores. Ao fazermos isso, teremos como resultado 1. É isso que a nossa função vai fazer: comparar as imagens com as categorias, dar um percentual de que aquilo pode estar ok, agrupar tudo isso e todas essas probabilidades vão somar 1, então será sempre um número de 0 a 1.

O nome deste algoritmo, dessa função, é Softmax, e saberemos que, por exemplo, o 0.67 foi a categoria que possui a maior probabilidade de estar correta. Sabendo disso, vamos lá escrever Softmax em nosso Notebook, no ponto em que havíamos parado. Agora, temos aqui um modelo que vai acontecer em sequência, com uma camada que achata e duas camadas totalmente conectadas, uma que possui ReLU acontecendo pelo meio.

Já vimos que ele fará com que todos os valores menos que 0 se tornem 0, e que olhará para os valores positivos, por debaixo dos panos, o que ela vai fazer é identificar como estão as linhas das nossas imagens, entendendo os contornos para diferenciação de uma imagem da outra.

E então temos a última camada, que terá 10 saídas, pois temos 10 categorias, com Softmax, que indicará a probabilidade dessas imagens pertencerem às categorias. Terminamos de criar o nosso modelo, e esse não é nenhum modelo famoso ou específico de Deep Learning, mas tem várias camadas, sendo então multicamadas, e se formos contá-las, no fim das contas podemos dizer que ele tem 2 camadas.

E aí queria trazer para vocês uma discussão que existe em relação ao que é considerado multicamadas ou profundas. Neste caso, por ele ter 2 camadas, algumas pessoas consideram que já é Deep Learning, um Aprendizado Profundo, e outras diriam que ainda precisamos de mais camadas intermediárias para isso.

Se copiássemos a linha com relu, por exemplo, e colássemos mais vezes na célula, de acordo com essas pessoas, agora sim, teríamos um Aprendizado Profundo. Definições à parte, o primeiro modelo que analisaremos é este com várias camadas, ou _multilayers_. Só queria trazer isso para vocês entenderem que temos 2 camadas, porque a primeira é a 0.

Do mesmo modo que fizemos no curso de Machine Learning, podemos treinar esse modelo, e para isso usamos modelo.fit, para o qual passamos dados e marcações, que são imagens_treino e indentificacoes_treino. Será que vai rodar agora?

Obteremos uma mensagem de erro dizendo que erramos a sintaxe! O que aconteceu é que temos várias camadas, mas esquecemos de colocar a vírgula entre elas. Vamos rodar mais uma vez. Teremos outro erro dizendo que precisamos compilar o modelo antes de treiná-lo, ou testá-lo. Repare que existe uma diferença no uso do Keras e do TensorFlow, também porque já fizemos isso antes, com MultinomialNB.

Aqui, não basta criarmos um modelo e já treiná-lo, existe um processo no meio disso, que é um modelo compilado, com alguns dados para darmos forma a este modelo antes de treinarmos ele. Este compilado, como já vimos, será modelo.compile, também uma função. Veremos a seguir o que precisamos colocar dentro dele.

# O que aprendemos?

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/deep-learning-introducao-com-keras/task/46341/next)

-   [](https://cursos.alura.com.br/suggestions/new/deep-learning-introducao-com-keras/46341/question)

Nesta aula, aprendemos:

-   o que é uma camada _Dense_,
-   a usar um número de unidades que seja múltiplo de 2,
-   processar nossos inputs usando _ReLU_,
-   como a _ReLu_ funciona,
-   como linearidade e não linearidade são usadas na classificação,
-   o número de unidades na nossa camada de saída,
-   como a _Softmax_ funciona,
-   o que é um modelo multi-camadas,
-   que há uma discussão em torno do que é considerado deep learning,
-   como treinar o nosso modelo,
-   a necessidade de compilar o modelo.