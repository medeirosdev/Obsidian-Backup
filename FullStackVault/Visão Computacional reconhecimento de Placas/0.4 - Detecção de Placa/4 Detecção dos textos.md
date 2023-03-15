A variável `localizacao` está armazenando as 4 coordenadas do retângulo extraído pela aproximação do polígono.

Agora, usaremos uma função para extrair o ponto inicial, o comprimento e a altura do retângulo para que possamos filtrar esses dados na imagem original. Então, em uma nova célula, colocaremos as variáveis `x` e `y`, que correspondem à coordenada inicial, e `w` e `h`, relacionados ao comprimento e altura, respectivamente.

Essas variáveis devem armazenar a função `cv2.boundingRect()` que extrairá as informações de `localizacao`.

```undefined
x, y, w, h = cv2.boundingRect(localizacao)
```

Rode este comando e chame as variáveis `x`, `y`, `w` e `h`, uma em cada célula.

```undefined
x
```

```undefined
y
```

```undefined
w
```

```undefined
h
```

Perceba que retornam os valores 180, 168, 722 e 224, respectivamente.

Agora, filtraremos essas coordenadas na imagem original. Para isso, criaremos uma variável `placa` que armazenará a `imagem`. Em seguida, passaremos o filtro `[y:y+h]`, informando que deve percorrer o eixo `y` levando em consideração a altura `h`. É importante ressaltar que, na biblioteca _OpenCV_, o `+` corresponde ao percurso de descida na imagem.

```ini
placa = imagem[y:y+h]
```

Em seguida, acrescentaremos as coordenadas `x:x+w`. Por fim, chamamos o comando de visualização `cv2_imshow(placa)`.

```makefile
placa = imagem[y:y+h, x:x+w]
cv2_imshow(placa)
```

![Recorte da imagem contendo somente a placa e os caracteres internos a ela.](https://cdn1.gnarususercontent.com.br/1/1310269/1ecf0807-be8e-409d-a1c8-7803fb609de7.png)

Perceba que o código funcionou e realizou o recorte exato da placa. Ou seja, identificou os contornos da imagem, associou a placa a um polígono e a recortou.

Utilizaremos essa imagem para tentar detectar os textos. Mas, antes, precisamos submetê-la aos procedimentos de limiarização e erosão. Somente após esses processamentos poderemos aplicar o _Tesseract_.

Para aplicar a limiarização, usaremos o seguinte código:

```undefined
valor, lim_otsu = cv2.threshold(placa, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
```

Ainda nessa célula, acrescentaremos o comando responsável pela erosão. Para isso, em uma variável `erosao`, chamaremos a função `cv2.erode()`, que deve receber `lim_otsu` e a função `cv2.getStructuringElement()`. Esta, por sua vez, recebe os argumentos `cv2.MORPH_RECT`, que é o formato do kernel, e `(4,4)`, tamanho do kernel.

```makefile
valor, lim_otsu = cv2.threshold(placa, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
erosao = cv2.erode(lim_otsu, cv2.getStructuringElement(cv2.MORPH_RECT, (4,4)))
```

Por fim, chamamos o comando de visualização `cv2_imshow(erosao)`.

```makefile
valor, lim_otsu = cv2.threshold(placa, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
erosao = cv2.erode(lim_otsu, cv2.getStructuringElement(cv2.MORPH_RECT, (4,4)))
cv2_imshow(erosao)
```

![Placa na cor branca com bordas pretas. Em letras garrafais pretas, "PLR3D97". No canto inferior esquerdo, também na cor preta, "BR". Barra superior na cor preta escrito "BRASIL" em branco. Ao final dessa barra, no canto superior direito, a bandeira do Brasil em preto e branco.](https://cdn1.gnarususercontent.com.br/1/1310269/a3a0341d-d521-40d6-95b5-f1a84dd978a2.png)

Ao executar o comando, perceba que nos retorna a imagem já limiarizada e com o processo de erosão aplicado. Sendo assim, podemos aplicar o _Tesseract_ para tentar identificar o texto.

Iniciaremos configurando o _Tesseract_ a partir da variável `config_tesseract`, que receberá `'--tessdata-dir tessdata --psm 6'`. Em seguida, criaremos a variável `texto`, que armazenará a função `pytesseract.image_to_string()`. Esta função receberá como argumento a variável `erosao`, `lang = 'por'`, que corresponde à Língua Portuguesa, e a variável de configuração `config_tesseract`. Por fim chame o comando de impressão `print(texto)`

```bash
config_tesseract = '--tessdata-dir tessdata --psm 6'
texto = pytesseract.image_to_string(erosao, lang = 'por', config_tesseract)
print(texto)
```

Rode a célula e note que nos retorna "L" e "PLR3D97". Embora tenha identificado corretamente o texto central da placa, também leu um "L" que não condiz com os caracteres e, talvez, tenha sido identificada erroneamente no lugar da sigla "BR", no canto inferior esquerdo.

Aplicaremos um regex (expressão regular) no texto retornado para extrair somente as informações que nos interessa. Para isso, precisamos importar a biblioteca _Regex_ com `import re`. Em seguida, em uma variável `texto_extraido`, armazenaremos a função `re.search()` que deve pesquisar o formato que queremos encontrar. Uma placa sempre inicia com 3 letras `'\w{3}`, seguidas por um dígito `\d{1}`, uma letra `\w{1}` e dois números `\d{2}'`, portanto este formato é o alvo da nossa pesquisa no texto.

```java
import re
texto_extraido = re.search('\w{3}\d{1}\w{1}\d{2}')
```

A função `re.search()` receberá, ainda, a variável `texto`, onde deve ser feita a pesquisa. Por fim, chamemos a variável `texto_extraido` para conferir o seu retorno.

```java
import re
texto_extraido = re.search('\w{3}\d{1}\w{1}\d{2}', texto)
texto_extraido
```

O retorno deve nos informar que foi encontrado o objeto "PLR3D97", que se inicia na posição 2 e vai até a posição 9. Vamos escreve-lo rodando o comando `print(texto_extraido.group(0))`.

```scss
print(texto_extraido.group(0))
```

Pronto! Conseguimos identificar o texto.

A seguir faremos o upload de uma nova imagem e aplicaremos os processamentos para, enfim, submetê-la à detecção de textos do _Tesseract_.