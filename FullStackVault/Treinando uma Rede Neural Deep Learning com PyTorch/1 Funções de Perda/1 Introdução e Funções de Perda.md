[00:00] Olá, pessoas. Meu nome é Camila, eu dou aula de deep learning desde 2018, em geral em cursos de extensão na federal de Minas Gerais. Eu também tenho um canal no YouTube chamado Peixe Babel, onde eu e a Virginia falamos sobre tecnologia.

[00:20] Neste curso, vamos aprender como treinar uma rede neural. Existe outro curso aqui na Alura introduzindo como construir uma rede neural. Esse curso já vai esperar que você saiba construir uma rede neural no Pytorch. De qualquer forma, vamos retomar essas ideias neste curso.

[00:44] Nós vamos aprender todos os elementos envolvidos no processo de otimização, como por exemplo funções de perda, que é nossa métrica de como está a qualidade do modelo. Vamos instanciar modelos neurais partindo do princípio que vocês já viram isso antes.

[01:02] Vamos aprender os otimizadores no Pytorch também, sempre associado a problemas reais, ainda que simples, e também vamos falar de hiper parâmetros de otimizadores. Para que entendamos quais são os otimizadores mais usados, mais eficientes, e quais já estão implementados no framework do Pytorch, que já adianto, são os mais úteis atualmente.

[01:30] Por fim, vamos falar um pouco sobre como funciona o fluxo de treinamento e teste. O que é um batch, uma época, uma iteração, quando você treina uma rede neural. Vamos ver na prática como carregar dados no Pytorch, para que possamos trabalhar com dados reais. Vamos ver que existem dados pré-carregados, mas também você pode carregar seu próprio dado. Vamos aprender como fazer isso. Iremos fazer todo o fluxo de treinamento e validação de uma rede neural.

[02:10] A ideia é que ao final deste curso vocês sejam capazes de construir ou carregar modelos neurais e também consigam implementar um fluxo de treinamento e validação, seja com dados existentes no framework ou com dados próprios seus que você pode carregar de forma muito eficiente no Pytorch.

[00:00] Olá, pessoal. Agora que já vimos quando precisamos de um único perceptron ou de múltiplos perceptrons na mesma camada, ou até de várias camadas de perceptron, vamos começar a falar como essas redes aprendem, como otimizamos essas coisas.

[00:18] Antes de entrar nas explicações de fato, gosto muito de uma analogia do Patrick Estrela, do Bob Esponja, tentando abrir um pote. Vamos ver um vídeo no YouTube e vou tentar explicar com a analogia desse vídeo.

[01:10] Eu amo de paixão esse exemplo, porque já conseguimos fazer a primeira analogia do que vamos aprender. Vocês viram que o Patrick estava recebendo instruções de como abrir a tampa. À medida em que ele chegava mais perto, ele ia mais devagar.

[01:32] A primeira coisa é que muita gente se refere ao aprendizado como tentativa e erro. Mas isso dá a ideia de que a pessoa está tentando loucamente várias alternativas, até chegar em algo bom. E não é bem assim. É uma tentativa guiada. Vamos ver como fazer isso de forma mais inteligente.

[02:00] Nesta aula vamos falar de funções de perda, ou funções objetivas, otimização e hiper parâmetros de otimizadores. Vamos começar pelas funções de perda. Você precisa definir uma medida de qualidade para saber se está se aproximando ou se afastando da solução. Você quer minimizar ou maximizar.

[02:22] Por exemplo, o Patrick quer minimizar a distância entre a mão dele e a tampa. Toda vez que ele tentar uma nova alternativa, ele sabe que está quente ou frio se estiver afastado ou aproximado da tampa. Seria um exemplo prático de função de perda. Minimizar a distância entre um ponto e outro.

[02:48] Você pode chamar de função objetiva, função de perda, critério, loss, função de custo. Tem vários nomes que querem dizer a mesma coisa. Eu trouxe alguns quotes interessantes para termos noção do que tem que ser a função de perda. Todas essas aspas foram retiradas da referência que está linkada aqui, que é um livro.

[03:16] A primeira delas é: “a função de custo reduz todos os aspectos bons e runs de um sistema complexo a um único número, um valor escalar, o que permite ranquear e comparar as soluções candidatas”. Quando falarmos de função de perda, estamos falando de um número. Posso querer minimizar a distância, mas também quero minimizar a força com que o Patrick bate no pote, porque ele pode quebrar o pote. Vou ter que somar esses critérios em um único valor. Não importa quantas métricas o problema exige.

[04:02] “Se fizermos uma escolha ruim de função de custo e os results obtidos não forem satisfatórios é nossa culpa por não especificar bem nosso objetivo”. Pode ser que você construa uma rede e ela não fique boa de jeito nenhum. Você pode pensar que não treinou direito, que a rede não é ideal, mas é importante pensar também que talvez você precise melhorar sua função de custo. Seu objetivo pode não estar bem definido. Não podemos ignorar a importância da função de custo.

[04:35] A escolha da função de custo está relacionada diretamente com o problema, assim como a camada de saída da sua rede, e vamos olhar para os principais problemas, que são regressão e classificação. Quando você estiver construindo sua arquivo e definindo sua função de perda, o problema que você está lidando vai interferir muito.

[04:55] Se você pensar no problema de regressão, sabemos que precisamos encontrar a função que vai descrever essa distribuição de dados. Vou ter uma variável independente, que no meu caso é o número de cômodos da casa, e uma variável dependente, que é o valor. Ela é dependente porque o valor da casa depende do número de cômodos que ela tem. É uma relação que precisa existir.

[05:25] Dado que o valor depende do número de cômodos, qual é a curva que vai se ajustar, permitir que eu faça predições? Eu consigo ver que se eu fizer uma coisa assim, consigo fazer predições. Dado que tenho uma casa com sete cômodos, consigo prever que ela vai custar algo em torno de 20 mil dólares. Mais ou menos isso que é a regressão.

[06:42] Aqui conseguimos realizar inferências. Dado que o exemplo que eu dei tem uma casa com sete cômodos custando 20 a 25 mil dólares, a métrica para medir a qualidade desse modelo é a distância entre o preço inferido e o preço real. Preço inferido vai ser o valor que vou inferir em cima da minha curva. Só que tenho uma amostra de uma casa com sete cômodos que custa 10 mil dólares. Eu errei por 15 mil dólares.

[07:37] A distância entre o preço real e o preço inferido pode ser um critério de qualidade. Neste caso, muito válido. Meu custo é 15 mil dólares de diferença entre o que eu predisse e o valor real.

[07:47] Dado que você tem uma regressão e você quer fazer a regressão de um valor, quero descobrir o preço de uma casa com base no número de cômodos e a minha inferência, que é o valor que ela custa. Eu criei uma rede com quatro neurônios na camada intermediária. Como temos uma rede com uma camada intermediária e uma camada de saída, vou conseguir modelar curvas, não só retas.

[08:25] Eu sei que minha camada de saída tem que ter um único neurônio, essa é uma limitação do problema, porque quero inferir um valor apenas, e sei que a minha função de custo pode ser a distância entre o valor real e o valor predito. Posso calcular uma distância absoluta, que é minha predição menos o valor real, ou uma distância quadrática, que é minha predição menos valor real elevado ao quadrado.

[09:00] Aqui são métricas reais, muito utilizadas para problemas de regressão, que no Pytorch e na maioria dos frameworks recebe o nome de perda L1, que é a distância absoluta, e o mean squared error, que é o erro médio quadrático, ou MSE. São métricas de custo que existem no Pytorch. Se o problema é de regressão, você pode ter essas duas funções de perda, que vão resolver bem o problema. São boas candidatas.

[09:42] A função de perda neste caso é minimizar a distância entre a predição e o rótulo. No caso do Patrick, ele está fazendo de certa forma uma regressão, dado que ele tem a posição da mão dele, a posição da tampa, ele está calculando a distância entre os dois valores.

[10:00] Em um problema como classificação, vamos supor que temos um problema de classificação de imagens. Queremos resolver com uma camada intermediária e uma camada de saída. Nesse caso, minha entrada x vai ter o número de dimensões igual ao número de pixels da imagem. Se tenho uma imagem 12x12 são 144 pixels, o numero de pontos no x. A camada de saída vai ter a quantidade de classes que eu modelar.

[10:40] Se eu quero classificar gato, cachorro, papagaio e calopsita, vou ter quatro neurônios na última camada. Um especializado em cada animal. Vimos isso quando falamos de múltiplos neurônios na mesma camada. Vou ter o x como valor de pixels e o y com o número de classes que estou modelando. A camada intermediária vai ser o que vai permitir a modelagem de funções mais complexas não lineares.

[11:16] Aqui tenho que y linha é a probabilidade de cada classe. Estou dizendo que a ativação é 0.25 para a classe cachorro, 0.9 para outra classe, 0.12 para outra classe, e daí por diante. O meu rótulo aqui vai ser uma codificação chamada de um 1 hot. Uma posição ativada e o resto desativada. Por exemplo, papagaio desativado, calopsita desativada, cachorro ativado e gato desativado, porque a imagem é de um cachorro.

[11:56] Teríamos a predição e o rótulo. Como calcular a qualidade dessas coisas? A ideia, como estamos trabalhando com distribuições, é mais complexa, mas vou dar uma ideia geral para explicar por que usamos uma métrica de distribuições.

[12:48] No caso de classificações com múltiplas classes, vamos usar a cross entropy, ou entropia cruzada, que é um conceito da teoria da informação. Queremos minimizar a entropia das distribuições. Para isso, vamos avaliar par a par os pares da nossa predição com o rótulo real. Se estivermos falando da classe correta, ou seja, se y for igual a 1, iremos tirar menos log da predição, e se não iremos fazer o menos log de 1 menos a predição.

[13:00] Isso na prática vai significar que quanto maior a probabilidade predita da classe correta, menor meu erro. Quanto mais próximo de 1 esse valor, mais correto estou. Menor tem que ser meu erro. Caso contrário, se y for igual a zero, quanto maior a probabilidade prevista, maior meu erro, porque estou dando uma ativação forte para a classe incorreta.

[13:41] São detalhes que se você quiser entender melhor você vai precisar pesquisar a literatura da função de entropia cruzada, mas é só para explicar que quando seu problema for de classificação, você vai ter que tratar com a função que vai calcular a diferença entre essas distribuições. Uma das funções é a cross entropy, que é a entropia cruzada.

[14:04] Quando você treina um modelo, o objetivo é fazer ele convergir para uma solução aproximadamente ótima. A função de perda é utilizada para acompanhar essa convergência. O gráfico de convergência vai ser dado pelos valores da sua perda à medida em que você passa por iterações de treinamento.

[14:26] Iremos falar um pouco mais disso depois, mas basta você saber que você não vai treinar sua rede uma única vez. Você vai treinar com vários conjuntos de dados, várias vezes. Isso iremos conversar melhor depois. Mas imagine que passei um conjunto de dados na minha rede e a perda foi 0.8. Faço mais uma iteração e a perda foi 0.6. Faço mais uma, deu 0.4. Estou convergindo, diminuindo a perda à medida em que treino meu modelo.

[15:13] Nosso objetivo é reduzir isso ao mínimo que conseguirmos. O que vai acontecer é que vai chegar um momento em que isso vai saturar e virar uma constante. Esse gráfico vai indicar se você está treinando bem ou mal sua rede, porque você pode também ter uma piora. Medir a loss ao longo das iterações é a forma de saber se você está melhorando ou se você voltou a piorar. O valor da loss é extremamente importante nesses casos, para avaliar se seu treinamento está bom ou ruim, convergindo, se a perda está diminuindo ou não.

[16:22] No próximo vídeo vamos dar uma olhada nas funções de perda do Pytorch.