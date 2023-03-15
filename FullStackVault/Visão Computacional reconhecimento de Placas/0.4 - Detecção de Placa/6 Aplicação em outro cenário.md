Realizamos os procedimentos na placa de carro e conseguimos detectar corretamente o texto através do _Tesseract_. Agora aplicaremos esses mesmos passos a uma nova imagem:

![Automóvel na diagonal frontal sobre uma rua de pedras. Árvores e construções de alvenaria desfocadas em segundo plano.  É possível visualizar a lateral esquerda do veículo, a lanterna frontal esquerda e a placa. Trata-se de um carro cinza, de 4 portas, da marca *Volkswagen*. Possui uma placa branca com contorno azul. Em letras garrafais azuis, "POX4G21", com um *QR Code* ao lado esquerdo. No canto inferior esquerdo, na cor preta, "BR". Há uma faixa azul na parte superior da placa. No canto esquerdo desta faixa, é possível identificar um símbolo com cerca de 4 estrelas e a palavra "MERCOSUL", na cor branca. Ao centro da faixa, "BRASIL", também em letras brancas. No canto direito, a bandeira do Brasil.](https://cdn1.gnarususercontent.com.br/1/1310269/5fc39905-8ea6-4f00-8537-05acf3397937.jpg)

Na aba lateral esquerda, faça o upload da imagem "placa_carro2", que você deve ter baixado no início do curso. Em seguida, copie o caminho desta imagem armazenada no _Colab_.

Em uma nova célula, crie uma variável `imagem`, chame a função `cv2.imread()` e passe o caminho da imagem como argumento desta função.

```ini
imagem = cv2.imread('/content/placa_carro2.jpg')
```

Ainda nesta célula, aplicaremos o procedimento de transformação da imagem para escalas de cinza através do comando `imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)`.

```ini
imagem = cv2.imread('/content/placa_carro2.jpg')
imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
```

Execute esta célula e chame o comando de visualização.

```scss
cv2_imshow(imagem)
```

![Imagem anterior agora em tons de cinza.](https://cdn1.gnarususercontent.com.br/1/1310269/76c2b65c-39fe-4cd7-a571-17c08a7efb8c.png)

Perceba que, agora, a imagem está em tons de cinza. Como trata-se de uma imagem que não foca necessariamente na placa e não dispõe de um ângulo frontal, teremos que encontrar a posição desta placa. Para isso, em uma nova célula, aplicaremos a detecção de bordas de _Canny_ para identificar os contornos. Armazenaremos o comando em uma variável `bordas`:

```ini
bordas = cv2.Canny(imagem, 100, 200)
```

Por fim, chamaremos o comando de visualização `cv2_imshow(bordas)`.

```makefile
bordas = cv2.Canny(imagem, 100, 200)
cv2_imshow(bordas)
```

Ao executar esta célula, ela deve nos retornar a seguinte imagem:

![Os objetos presentes na imagem assumiram a cor preta com contornos brancos. Na placa, ainda é possível detectar o texto "POX4G21", em letras garrafais, mas os demais caracteres tornaram-se difíceis de se identificar.](https://cdn1.gnarususercontent.com.br/1/1310269/d2ecb228-e09b-493e-8ead-79bbe7cef1d2.png)

Perceba que todas as bordas foram detectadas e esse procedimento nos revelou mais contornos do que conseguíamos identificar na imagem anterior, em escalas de cinza. Diante disso, teremos que fazer um processo para ordenar esses contornos com base no tamanho da área e em formas fechadas. Para isso, criaremos as variáveis `contornos` e `hierarquia`, que receberão a função `cv2.findContours()`. O primeiro parâmetro desta função será a imagem `bordas`, seguido do parâmetro de hierarquia `cv2.RETR_TREE`, que precisa ser colocado mesmo que não o utilizemos, e `cv2.CHAIN_APPROX_SIMPLE`, que deve nos retornar somente os pontos iniciais e finais dos contornos.

```undefined
contornos, hierarquia = cv2.findCountours(bordas, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
```

Por fim, adicionaremos um passo que deve ordenar os contornos `sorted(contornos)` e definir os parâmetros `key = cv2.contourArea`, que informa que o ordenamento deve ser feito por tamanho de área, e `reverse = True`, para que sejam elencados do maior para o menor. Armazenaremos este comando em uma variável `contornos`.

```python
contornos, hierarquia = cv2.findCountours(bordas, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
contornos = sorted(contornos, key = cv2.contourArea, reverse = True)
```

Adicionaremos, ainda, um filtro de lista que deve nos trazer somente os 10 primeiros resultados `[:10]`.

```python
contornos, hierarquia = cv2.findCountours(bordas, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
contornos = sorted(contornos, key = cv2.contourArea, reverse = True)[:10]
```

Execute esta célula e, em seguida, copie o código _for loop_, realizado anteriormente, para que possamos aproveitá-lo:

```css
for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if cv2.isContourConvex(aproximacao) and len(aproximacao) == 4:
                    localizacao = aproximacao
                    break
```

Lembre-se que esse _loop_ itera pelos contornos, realiza a porcentagem `epsilon` do perímetro do contorno, aproxima-o de um polígono fechado e confere se trata-se de um polígono convexo com 4 lados, armazenando-o em uma variável `localizacao`.

Execute a célula com este laço de repetição e, em uma nova, chame `localizacao`. Perceba que nos retorna um array com 4 coordenadas.

```undefined
localizacao
```

Agora, utilizaremos a função `boundingRect()` para pegar o ponto inicial, o comprimento e a altura do retângulo. Para isso, usaremos as variáveis `x`, `y`, `w` e `h`, chamaremos `cv2.boundingRect()` e passaremos `localizacao` como parâmetro.

```undefined
x, y, w, h = cv2.boundingRect(localizacao)
```

Após executar a célula, filtraremos os valores através do código a seguir:

```makefile
placa = imagem[y:y+h, x:x+w]
cv2_imshow(placa)
```

Ele deve nos retornar a seguinte imagem:

![Recorte da placa, inclinada, em escalas de cinza. É possível identificar "POX4G21" e "BR", embora a parte inferior da letra "B" tenha sido cortada. O recorte não permite a visualização completa da barra superior, somente a escrita "MERCOSUL".](https://cdn1.gnarususercontent.com.br/1/1310269/48f65c5c-551f-4560-9442-822bd1461fb1.png)

Perceba que mesmo com a grande quantidade de contornos presentes na figura, foi possível identificar a área correspondente à placa, embora ela esteja um pouco inclinada. Faremos, agora, a limiarização da imagem através deste código:

```undefined
valor, lim_otsu = cv2.threshold(placa, 0, 255, cv2.THRESH_BINARY, | cv2.THERSH_OTSU)
cv2_imshow(lim_otsu)
```

Pronto! A imagem está limiarizada:

![Imagem da placa recortada em preto e branco.](https://cdn1.gnarususercontent.com.br/1/1310269/60404955-a707-4e8b-b6e2-6194cac303e1.png)

Vamos aplicar o _Tesseract_ para tentar detectar o texto. Para isso, execute a célula seguinte:

```lua
texto = pytesseract.imagem_to_string(lim_otsu, lang = 'por', config = config_tesseract)
print(texto)
```

O comando deve nos retornar ""POX4G21", com aspas duplas no início, possivelmente decorrentes da tentativa de identificar o "BR" presente na placa. Extrairemos o texto utilizando _Regex_, mesma função que aplicamos na placa anterior:

```bash
texto_extraido = re.search('\w{3}\d{1}\w{1}\d{2}', texto)
texto_extraido
```

Deve nos retornar um objeto e, para imprimir o texto deste objeto, usaremos o comando `print(texto_extraido.group(0))`.

```scss
print(texto_extraido.group(0))
```

Ao executá-lo, teremos o texto "POX4G21". Pronto! Conseguimos aplicar os pré-processamentos à imagem viabilizando a detecção do texto pelo _Tesseract_.

Vale ressaltar, no entanto, que a abordagem utilizada aqui pode não funcionar em todos os casos. Sendo assim, a seguir, veremos outra forma de detectar a posição da placa em uma imagem diferente. Te encontro lá!

# Ordenando os contornos

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/visao-computacional-deteccao-texto-placas-carro/task/113527/next)

-   [](https://cursos.alura.com.br/suggestions/new/visao-computacional-deteccao-texto-placas-carro/113527/question)

Em uma imagem com muitos objetos e detalhes, ao realizar a detecção de bordas com o método de Canny serão gerados muitos contornos, e grande parte deles serão considerados ruídos, ou seja, irrelevantes para solucionar o problema de detecção da placa.

É possível reduzir a quantidade de contornos, filtrando aqueles que são relevantes a partir da área que o contorno ocupa na imagem. Escolha a alternativa que tem o código para realizar a filtragem dos 10 contornos com maior área na imagem:

Selecione uma alternativa

-   ```ini
    contornos = sorted(contornos, key=cv2.contourArea, reverse=True)[:10]
    ```
    
-   ```ini
    contornos = sorted(contornos, reverse=True)[:10]
    ```
    
-   ```ini
    contornos = sorted(contornos, key=cv2.contourArea, reverse=True)
    ```
    
-   ```ini
    contornos = sorted(contornos, key=cv2.contourArea, reverse=Fals
    ```