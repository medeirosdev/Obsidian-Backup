Entendemos a camada 0, ou camada de entrada, usando o keras.layers.Flatten, e sabemos o que ela está fazendo. Agora, podemos olhar para a próxima coisa que comentamos, o processamento. No que consiste isso? Porque até agora, com esta primeira camada, estamos pegando um array de 2 dimensões e achatando-o para que fique com uma dimensão única. Mas o que fazemos com isso?

Para acrescentarmos mais uma camada, podemos começar a escrever novamente, do mesmo modo que fizemos para o Flatten, que queremos mais uma layer, ou seja, layers, que virão do keras. Até então, vimos o Flatten, será que faz sentido colocarmos ele mais uma vez? Não, certo? Precisaremos fazer outra coisa aqui. Se temos várias bolinhas, várias funções, e cada uma delas está processando e achatando a nossa imagem, o que podemos fazer?

Podemos adicionar mais dessas bolinhas, e então teremos que fazer uma camada se comunicar com a outra. Vamos exemplificar isso um pouco melhor — abriremos o slide da apresentação para mostrar isso visualmente. Temos à esquerda as bolinhas da camada Flatten, e à direita as bolinhas novas. O primeiro pontinho da camada de entrada vai falar com uma bolinha da segunda camada, que falará com mais duas.

Agora, ela está falando com as três, então, se há algo passando por essa bolinha, ela está indo para as outras três. Pegaremos a bolinha de baixo, na primeira camada, ou camada 0, que também se conectará com as próximas 3. A próxima, a mesma coisa, e deste modo estamos fazendo com que esse processo, depois que achatamos as nossas imagens, que isso se comunique com a próxima camada que iremos colocar.

Fazendo isso, não fica uma comunicação rasa, estamos fazendo uma comunicação mais profunda, em que todos falam com todos. Com base nisso, essa próxima camada que criaremos será uma mais densa, então criaremos uma camada do tipo dense, ou camada totalmente conectada, em que todos se comunicam.

Então vamos voltar ao Notebook, e escreveremos densa em inglês, que é Dense. Do mesmo modo que com Flatten, Dense também é uma função. E agora, o que temos que colocar dentro dela? Como vimos, temos aquelas bolinhas, e agora definiremos quantas delas queremos. Então podemos colocar 10, por exemplo, 20.

Para definirmos isso vamos ajustando e experimentando, não existe um número certo ou errado, a dica é colocar sempre um valor múltiplo de 2, porque o nosso processamento trabalha dessa maneira, e ficará mais legal fazer as computações com as camadas. Então colocaremos um número aleatório, como 256.

Com isso estamos falando que queremos uma camada com 256 funções, bolinhas, que irão ser densas, completamente conectadas à nossa camada que está achatando as nossas imagens. Isso, porém, não é o bastante, também teremos que indicar ao keras como e quando essas bolinhas irão se comunicar, quando elas serão ativadas e irão agir no meio das nossas camadas.

Para isso iremos inserir uma vírgula, e ativação em inglês é activation, e o tipo de ativação que usaremos será função. Você pode me perguntar que função usaremos, e eu vou sugerir aquela que a maioria das pessoas estão adotando quando se trata de Deep Learning e Redes Neurais, que se chama relu.

Essa função se encontrará dentro do TensorFlow, que escreveremos no código. Além disso, precisamos passar nn, de _Neural networks_, isto é, Redes Neurais. Usaremos essa função de Redes Neurais do TensorFlow para indicar à segunda camada que ela pode mandar bala e começar a fazer o processamento dela.