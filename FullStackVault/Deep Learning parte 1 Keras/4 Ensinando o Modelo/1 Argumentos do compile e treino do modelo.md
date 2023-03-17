Fiquei de falar para vocês o que iremos passar à função modelo.compile, mas vejam que bacana, se voltarmos e irmos ao fim do nosso erro, RuntimeError, podemos ver que o final da frase está com "use modelo.compile com otimizador e perda". O otimizador é optimizer, e perda é loss, então o próprio erro já está dizendo para nós o que precisamos passar para o compile.

Vamos voltar àquela linha de código, e dentro de modelo.compile passaremos um otimizador, o tal do optimizer. O que é isso? Quando treinamos, podemos deixar o treino melhor, e esse otimizador fará isso. Não entrarei em detalhes disso agora, para podermos rodar nosso treino com mais agilidade, mas esta é a função do otimizador.

Usaremos um bem famoso para esses casos em que precisamos categorizar com mais de 2 categorias as nossas imagens. No caso, temos 10 categorias, então o otimizador mais indicado é o chamado adam, que colocaremos entre aspas simples. Também precisamos passar a nossa perda, ou loss. E o que é isso? Toda vez que passamos uma informação, como neste caso, uma parte que não necessariamente entenderemos 100%.

Então, em qualquer sistema teremos uma perda de informação. Do mesmo modo que vimos anteriormente, se classificarmos camiseta como Saia, há uma probabilidade, mas sabemos que o que estamos vendo é uma classificação errada, então, se nossa Rede fizer isso, ela perdeu informações. O que iremos usar para calcular essa perda?

Colocaremos um sinal de =, aspas simples, e usaremos um nome que mais parece um palavrão: Entropia Cruzada Categórica Esparsa. Quer dizer que trata-se de um cálculo deste erro, a entropia, por categorias, haverá uma mistura, esse cruzada, e o esparsa por ser algo abrangente com várias categorias.

Por enquanto ficaremos nesse entendimento em relação a isso. Agora, passaremos tudo isso para o inglês, que como sabemos ficam invertidas, então teremos sparse_categorical_crossentropy. Vamos salvar com Cmd + S, ou Ctrl + S, e daremos um Cmd + Enter para rodarmos.

Dessa vez não tivemos um erro, e tem um tal de Epoch acontecendo, uns números, algo sendo completado, 9s, e temos o loss, que sabemos que é uma perda, no caso, de 13.10. Além disso, sabemos que passamos por 60000 imagens, então nosso modelo finalmente foi criado, compilado e treinado, e é isso que vemos na interface quando treinamos o modelo.

Então, passamos por 60000 imagens, o que quer dizer que foi uma Epoch, um ciclo. Aqui no Deep Learning, chamamos um ciclo de época, uma rodada de passagem por estas 60000 imagens, e tentaremos entender cada uma delas. Começaremos a entender se isso é bom ou ruim, e o que podemos fazer neste processo para conseguir saber como está a nossa rede.

# Resultados do treinamento

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/deep-learning-introducao-com-keras/task/46346/next)

-   [](https://cursos.alura.com.br/suggestions/new/deep-learning-introducao-com-keras/46346/question)

Você criou, compilou e ao treinar o modelo viu o resultado abaixo:

![uma época com 60.000 imagens que durou 12 segundos com perda de 14.5](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image8.png)

Sobre o trecho Epoch 1/1, podemos dizer que época é

Selecione uma alternativa

-   Uma rodada de treinamento que passa por todos os exemplos do dataset.
    
-   Quantas vezes o modelo foi treinado por um tempo pré-definido.
    
-   Um parâmetro definido pelo Keras para indicar que o modelo treinou.
    
-   O número que mostra quantas vezes o modelo foi treinado.