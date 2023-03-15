Agora conheceremos a limiarização de Otsu!

Neste processo, o valor do limiar é definido automaticamente e utilizado para todos os pixels, ou seja, é um limiar global. A partir de uma imagem em escala de cinza é extraído um histograma da intensidade de cor dos pixels. Com base neste gráfico, é escolhido um limiar que esteja entre os dois picos do histograma, ou seja, entre as intensidades de cor.

Vamos aplicar este processo à nossa imagem!

Iniciaremos construindo um histograma para que possamos observar a distribuição da intensidade de cor dos pixels. Para isso, chamemos a variável `imagem` a fim de ver o que há armazenado nela.

```undefined
imagem
```

Perceba que nos retorna um array, ou seja, uma matriz com vários valores em que cada um representa a intensidade dos pixels da imagem.

Para transformar esses valores em um histograma, precisamos que este array esteja no formato de lista. Faremos essa modificação com o seguinte código:

```java
import seaborn as sns
ax = sns.histplot(imagem.flatten())
ax.figure.set_size_inches(10,6)
```

`histplot()` é o gráfico responsável por mostrar um histograma e `flatten()` é a função que transforma um array com várias dimensões para um array com uma só dimensão. Por fim, definimos o tamanho 10x6 para a figura através do comando `ax.figure.set_size_inches(10,6)`.

Ao executar esta célula, ela nos retornará o histograma da quantidade de pixels para cada intensidade de cor presente na imagem. Perceba que há uma concentração entre as intensidades 0 e 50, e entre (aproximadamente) 180 e 200. Ou seja, pela lógica deste procedimento, o limiar escolhido deve estar entre 60 e 180.

Vamos, agora, fazer o processo de limiarização. Para isso, utilizaremos a função `threshold()`, usada anteriormente na limiarização simples, que nos retorna dois resultados: o valor do limiar e a imagem transformada.

Coloquemos, então, esses dois resultados em nova célula: `valor` e `lim_otsu` - variável que armazenará a imagem limiarizada. Eles receberão a função `cv2.threshold()` que, por sua vez, recebe os parâmetros `imagem`; `0` e `255`, valores para os quais transformaremos os pixels caso estes sejam menores ou maiores que os limiar, respectivamente; e `cv2.THRESH_BINARY`, que estabelece as cores preto e branco. Temos, ainda, um último parâmetro que pode vir antecedido por `+` ou por `|`: o método `cv2.THRESH_OTSU`.

Em seguida, adicione o código de visualização `cv2_imshow(lim_otsu)` e o comando `print(f'Limiar: {valor}')`, que deve imprimir o valor definido como limiar. O comando ficará assim:

```python
valor, lim_otsu = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
cv2_imshow(lim_otsu)
print(f'Limiar: {valor}')
```

Execute esta célula e repare que a imagem está limiarizada e, embora existam algumas falhas e ruídos, é possível identificar os caracteres presentes nela. Observe, também, que o valor do limiar foi definido em 96, ou seja, está entre os dois picos do histograma.

Agora, usaremos o _Tesseract_ para tentar detectar o texto da placa. Para isso, criamos uma variável de configuração `config_tesseract` e passaremos `'--tessdata-dir tessdata'`, que deve localizar a pasta onde estão armazenadas as configurações de Língua Portuguesa.

Em seguida, a variável `texto` receberá `pytesseract,image_to_string(lim_otsu, lang = 'por', config = config_tesseract)`. Por fim, chamamos o comando de impressão `print(texto)`.

```lua
config_tesseract = '--tessdata-dir tessdata'
texto = pytesseract,image_to_string(lim_otsu, lang = 'por', config = config_tesseract)
print(texto)
```

Execute a célula de código e perceba que não houve um retorno. Ou seja, mesmo com o procedimento de limiarização, o _Tesseract_ não foi capaz de identificar o texto presente na placa.

Veremos, então, outros pré-processamentos que podem ser aplicados à imagem para facilitar a detecção do texto!

# Sobre a limiarização de Otsu

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/visao-computacional-deteccao-texto-placas-carro/task/113513/next)

-   [](https://cursos.alura.com.br/suggestions/new/visao-computacional-deteccao-texto-placas-carro/113513/question)

A limiarização de Otsu utiliza um limiar global para transformar uma imagem da escala de cinza em uma imagem preto e branco. Porém, diferente da limiarização simples, a escolha do limiar é feita de forma automática a partir de um histograma de intensidade de cinza dos pixels da imagem.

Quais as alternativas representam o código correto para aplicar o processo de limiarização de Otsu em uma imagem?

Selecione 3 alternativas

-   ```undefined
    valor, lim_otsu = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)
    ```
    
-   ```undefined
    valor, lim_otsu = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY or cv2.THRESH_OTSU)
    ```
    
-   ```ini
    limiarizacao = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
    ```
    
-   ```undefined
    valor, lim_otsu = cv2.threshold(imagem, 0, 255, cv2.THRESH_BIN
    ```