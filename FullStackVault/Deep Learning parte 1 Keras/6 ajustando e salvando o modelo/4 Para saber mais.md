Nome do arquivo ao salvar o modelo

No curso, salvamos o modelo como `modelo.h5`.

![notebook com o código para salvar o modelo](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image19.png)

Nesse caso, estamos nos introduzindo e também lidando com um só modelo. Mas, no dia a dia, pode ser que tenhamos 3, 4, 5 modelos diferentes e também variações do números de épocas de treinamento.

Então, podemos usar um outro tipo de nomenclatura, ao invés de salvarmos como `modelo.h5`, podemos dar mais detalhes como o número de épocas e o número de nós (ou camadas), salvando como `modelo_epochs5_nos3.h5`, por exemplo, para não misturarmos os modelos.

Como com o nosso modelo do curso,

![código do modelo de 3 camadas do curso](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image12.png)

e 5 épocas, ficamos com

![salvando o modelo com o título modelo_epochs5_nos3.h5](https://s3.amazonaws.com/caelum-online-public/982-tensorflow/image4.png)