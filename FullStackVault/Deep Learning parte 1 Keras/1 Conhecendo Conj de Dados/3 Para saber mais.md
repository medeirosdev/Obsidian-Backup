O dataset Fashion-MNIST

Se você está iniciando os estudos em Deep Learning (ou Machine Learning) e der uma olhada por aí, vai perceber que algumas pessoas, posts e blogs podem recomendar o uso de um dataset chamado **MNIST**.

O [MNIST](http://yann.lecun.com/exdb/mnist/) (site em inglês) é um conjunto de imagens de números escritos à mão, e o seu nome significa literalmente que é um dataset Modificado do Instituto Nacional de Padrões e Tecnologia (em inglês Modified National Institute of Standards and Technology database). E por que modificado? Porque já havia um dataset chamado NIST (do Instituto Nacional de Padrões e Tecnologia) que tinha sido formado por imagens de números escritos à mão coletados de um escritório norte americano responsável pelo censo e também de estudantes do colegial.

![imagem do formulário preenchido a mão que coletou os dados](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image7.png)

Então, agora sabemos que antes tinha o NIST, e depois o MNIST que modificou o NIST. Logo, o MNIST pegou as imagens de números no NIST, formatou essas imagens em 28x28 pixels e as deixou em escala de cinza. Ele possui 60.000 imagens para treino e 10.000 imagens para teste.

Após a criação do MNIST, ele acabou virando o padrão de uso para o aprendizado de máquina, e resultados próximos a uma identificação humana de dígitos foram atingidos com ele. O que tornou a tarefa de reconhecer dígitos mais fácil, tão fácil que entender esse dataset parou de ser algo desafiador para os modelos da época.

![imagem dos números do mnist](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image18.png)

E aí foi necessário pensar numa solução. Você tem um dataset que está fácil demais de identificar? O que dá pra fazer? Colocar mais imagens? Colocar imagens diferentes? Essa foi uma das respostas. Aumentar esse dataset, fazendo uma extensão dele para dificultar o aprendizado de máquina.

E aí surgiu o [EMNIST](https://arxiv.org/pdf/1702.05373.pdf) (arquivo em inglês), com E de extensão. E, do mesmo modo que o MNIST tinha herdado do NIST, o EMNIST herdou a “estrutura” do MNIST e adicionou letras aos números. Agora, tínhamos um dataset com números e letras.

Mas, ao começar a usar o dataset, as letras do EMNIST ainda ficavam muito próximas dos números, o que não foi o bastante para aumentar a complexidade da tarefa. As pessoas criando modelos e fazendo pesquisa ainda queriam algo mais desafiador. E agora? Uma resposta foi mudar o padrão original “alfa-numérico” e identificar imagens de roupas de uma loja alemã chamada [Zalando](https://jobs.zalando.com/en/) (site em inglês), criando assim o [Fashion MNIST](https://github.com/zalandoresearch/fashion-mnist) (github em inglês).

![imagem das roupas do fashion mnist](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image17.png)

Hoje em dia, o Fashion-MNIST é um dos datasets mais recomendados para uma introdução no estudo de Deep Learning. O que é um dos motivos para explorarmos esse dataset neste curso.