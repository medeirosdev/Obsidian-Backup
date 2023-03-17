## Transcrição

Vimos que `imagens_treino` volta esse array para nós, mas precisamos investigar para entendermos melhor o que isso quer dizer.

```css
array([[[0, 0, 0 ..., 0, 0, 0],
        [0, 0, 0 ..., 0, 0, 0],
        [0, 0, 0 ..., 0, 0, 0],
        ...,
        [0, 0, 0 ..., 0, 0, 0],
        [0, 0, 0 ..., 0, 0, 0],
        [0, 0, 0 ..., 0, 0, 0]]])
```

Como de costume, podemos ver qual a extensão deste `imagens_treino`, então usaremos o `len` do Python para isso.

```scss
len(imagens_treino)


60000
```

Conseguimos com isso entender que são 60000 imagens que temos para treino. Mas qual é a composição, o formato dessas imagens?

Para falarmos isso, usaremos `imagens_treino.shape`, e executaremos novamente.

```scss
len(imagens_treino)
imagens_treino.shape

(60000, 28, 28)
```

Então, podemos ver que o primeiro elemento que volta nesta resposta de 60000 é a len da nossa imagem, depois temos 28, 28, o que significa que temos um array de 28 linhas e 28 colunas, então são 28 vezes 28 posições que estão descrevendo a nossa imagem.

Temos 60000 imagens, mas lembra que eu tinha dito que teríamos 70000? O que houve com essas outras 10000 imagens? Acabamos de ver as imagens de treino, vamos dar uma olhada nas de teste escrevendo `imagens_teste.shape`, pois sabemos que no próprio shape sabemos qual é a `len` de cada uma delas. Com Cmd + Enter executamos o código.

```scss
imagens_test.shape

(10000, 28, 28)
```

Aqui estão as nossas 10000 imagens, e agora temos 70000, todas com 28 por 28 de dimensão. Sabemos que as imagens de treino e as de teste têm o mesmo tamanho, o que é muito bom quando formos treinar a nossa rede. Olhamos as imagens, mas não vimos as identificações, será que elas estão batendo, com a quantidade de imagens que temos?

Usaremos o `len(identificacoes_treino)` para verificar, que será 60000, como esperado, então podemos dar uma olhada nas de teste, para ver se está batendo. Teremos 10000, então nossas identificações ou _labels_ estão batendo com as imagens. Legal, mas que imagens são essas, que até então não visualizamos?

Para isso, vamos usar uma biblioteca do Python chamada `matplotlib`, uma "lib" de biblioteca, "plot" de plotar, desenhar o gráfico, e "mat" de matemática. Usaremos algo interno a ela, específico para visualizarmos a nossa imagem, que se chama `pyplot`. E como vimos, para podermos usar o que está dentro dele, teremos que importá-lo, como `plt`. Trata-se de uma convenção dentro do Python, quando você vir já vai saber que vem do pyplot do matplotlib.

```javascript
import matplotlib.pyplot as plt
```

Vamos executar a célula mais uma vez, agora podemos dar um Enter e tentar visualizar essa imagem. Para isso usaremos o `imshow()` do matplotlib, "im" de imagem e "show" de mostrar.

Dentro dessa função, vamos passar nossa primeira imagem, no caso, `imagens_treino`, colocando entre colchetes o índice `0`, e como o `imshow()` está dentro do `pyplot` e o chamamos de `plt`, escreveremos, antes de `imshow()`, `plt.`.

```css
plt.imshow(imagens_treino[0])
```

Vamos executar e ver o que acontece? Já temos uma imagem. À esquerda, a numeração vai de 0 a pouco mais de 25, daquelas 28 dimensões que tínhamos falado, enquanto na base os números vão de 0 a pouco mais de 25 novamente.

Podemos ver que é uma imagem de 28 por 28 espaços, ou pixels, e cada um desses traz essa informação, que conseguimos visualizar agora.

![](https://caelum-online-public.s3.amazonaws.com/982-tensorflow/transcri%C3%A7%C3%A3o+acess%C3%ADvel/01.07_001_imagem1.png)

A partir disso, vamos seguir com nosso projeto e código.

# O retorno do .shape


Você executou a linha

```undefined
imagens_treino.shape
```

lá no Colab e a resposta foi

```scss
(30 000, 25, 25)
```

O que esses números significam respectivamente?

Selecione uma alternativa

-   As dimensões das imagens de treino, quantidade de imagens e número de linhas das imagens.
    
-   As colunas das imagens de treino, dimensões das imagens e tamanho das imagens.
    
-   A quantidade de imagens de treino, número de linhas das imagens e o número de colunas das imagens.
    
-   O número de posições que as imagens de treino ocupam, tamanho das imagens e número de linhas das imagens.

A quantidade de imagens de treino, número de linhas das imagens e o número de colunas das imagens.

Correto! O primeiro número indica que temos 30 000 imagens, o segundo que são compostas de 25 linhas e o terceiro que elas são compostas de 25 colunas.