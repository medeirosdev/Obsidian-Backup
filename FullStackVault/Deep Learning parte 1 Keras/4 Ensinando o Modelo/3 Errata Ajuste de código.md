No vídeo anterior, **Escala de cinza e normalização**, os dados foram normalizados entre 0 e 1 para que fossem definidos em escala cinza e, assim, melhorar o aprendizado do modelo. O código final dessa aula pode ser observado a seguir:

```python
#normalização
imagens_treino = imagens_treino/float(255)
modelo = keras.Sequential([keras.layers.Flatten(input_shape = (28,28)), 
                          keras.layers.Dense(256, activation = tensorflow.nn.relu),
                          keras.layers.Dense(10, activation = tensorflow.nn.softmax)])

modelo.compile(optimizer = 'adam', loss = 'sparse_categorical_crossentropy')

modelo.fit(imagens_treino,identificacoes_treino)
```

Na próxima aula, **Definindo número de camadas**, há uma alteração no código final da aula anterior no qual ele é executado várias vezes para ajustar o modelo. O problema dessa prática é que o conjunto `imagem_treino` é também **dividido por 255 diversas vezes**, fazendo o conjunto perder a característica de _conjunto normalizado_ que pode afetar o aprendizado do modelo.

Desse modo, para que você obtenha um resultado de treino eficaz, separe o comando de normalização da célula de construção do modelo do seguinte modo:

### Célula 1:

```ini
#normalização
imagens_treino = imagens_treino/float(255)
```

### Célula 2:

```python
modelo = keras.Sequential([keras.layers.Flatten(input_shape = (28,28)),
                          keras.layers.Dense(256, activation = tensorflow.nn.relu),
                          keras.layers.Dense(10, activation = tensorflow.nn.softmax)])

modelo.compile(optimizer = 'adam', loss = 'sparse_categorical_crossentropy')

modelo.fit(imagens_treino,identificacoes_treino)
```

Tendo as duas células e já realizada a normalização dos dados de treino, você pode seguir executando o código **da Célula 2 em diante**, sem adicionar outro código que irá dividir o conjunto de **treino** por 255.

> **ATENÇÃO:** Fazendo isso você terá resultados diferentes dos mostrados em aula, mas eles tenderão a ser melhores e estarão correta