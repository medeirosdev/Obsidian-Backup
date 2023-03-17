Parabéns por ter finalizado mais um curso da Alura! Espero que tenha gostado deste comecinho do mundo do Deep Learning, dessas probabilidades que fazemos com as máquinas neste curso.

Vamos recapitular o que vimos: primeiro usamos o tensorflow, específico para estes modelos de Deep Learning, e acima dele, que usamos para escrever nosso código com Python, foi o keras, uma API de alto nível. Também utilizamos o matplotlib, o pyplot para fazer nossos gráficos e visualizar nossas imagens, entendendo nosso dataset, usamos o numpy, e há o importe do load_model, para quando salvamos nosso modelo.

Começamos usando o dataset fashion_mnist, que vem e está organizado dentro do próprio Keras, e vimos como ele voltava tuplas, acessava imagens_treino, identificacoes_treino, imagens_teste, identificacoes_teste, que vocês já tinham visto no curso de Machine Learning. E então carregamos os dados com outra função do Keras, então é legal que esta API faz bastante coisas para nós.

Exploramos estes dados entendendo se eles eram vetores, quantas dimensões eles tinham, imagens, quantas para teste e quantas para treino, e o dataset não vinha com os nomes das classificações, demos uma olhada na documentação do fashion_mnist do Zalando Research. Começamos a entender os pixels das nossas imagens, que estavam em escala de cinza, e vimos que uma boa pedida seria normalizar essa imagem para termos valores menores, os quais nos ajudariam durante nosso modelo.

Assim, fica mais fácil para nosso modelo processar estes dados, porque ele já faz muito. Começamos a construir este modelo que possui 3 camadas, a de entrada, 0, a primeira, densa, que é 1, Dropout que é 2 e a última, densa, que é 3. Vimos como fazer o Flatten, a ReLU, o que é Dropout, softmax, e quando fomos compilar o modelo, também entendemos que tínhamos que passar um otimizador, como calcularemos nossa perda, e uma métrica.

Então treinamos nosso modelo, salvamos em um histórico, e deixamos 20% dos dados para validarmos este modelo, e fomos mexendo na quantidade de épocas. Brincamos com o número de camadas da nossa rede para ver o que acontecia, e vimos que há um detalhe do Notebook, que é necessário restartar o Runtime.

Quando conseguimos chegar ao modelo que achamos mais interessante, porque fizemos os gráficos para visualizarmos as acurácias e as perdas que tivemos tanto em treino quanto em validação, com pyplot, salvamos e carregamos o modelo treinado. No meio disso tudo, também fomos testando este modelo com predict, como também tínhamos visto no curso de Machine Learning.

Vimos o resultado do teste, o número da imagem de teste, e comparamos o primeiro predict com o modelo salvo para vermos se estava tudo ok, e estávamos com o arquivo do modelo ok. Depois disso também vimos que é possível avaliar o modelo, entendendo como ele estava indo em nosso conjunto de testes. Trata-se de mais um dado de perda e acurácia, para controlarmos e ver se está minimizando a perda e aumentando a acurácia, como vimos no vídeo anterior.

Este é nosso objetivo, e vamos vendo o número de épocas, entendendo se está _underfitting_, _overfitting_, e vamos controlando para chegarmos em um bom resultado. Lembrando que além disso, é sempre importante que a sua rede generalize bem, então que a cada vez que tenha uma imagem nova, ela entenda e consiga classificar corretamente, com facilidade.

Espero que tenha gostado deste curso, lembre-se de fazer exercícios, há bastante informações extras para saber mais, e até a próxima.