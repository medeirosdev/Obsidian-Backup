[[OpenCV]]Nós utilizamos o regex para capturar algumas informações importantes da nossa imagem, por exemplo, a data de vencimento das contas. Agora vamos deixar essa data em destaque, isto é, em cores diferentes. Na nossa imagem, a cor azul é predominante. A data foi escrita em branco, sendo que o fundo da imagem está um pouco amarelado. Nós conseguimos visualizar o resultado dessa fonte, porém, ele não está tão expressivo/visível.

Para realizarmos o destaque das nossas informações, usaremos o `for` que construímos nas aulas anteriores e, na parte do `caixa_texto`, adicionaremos uma nova informação.

```go
img_copia = rgb.copy()
for i in range(0, len(resultado['text'])):
  confianca = int(resultado['conf'][i])
  if confianca > min_conf:
    texto = resultado['text'][i]

    if re.match(padrao_data, texto):
      x, y, img = caixa_texto(resultado, img_copia)
      img_copia = escreve_texto(texto, x, y, img_copia, fonte, 12)
    else:
      x, y, img_copia = caixa_texto(resultado, img_copia)

cv2_imshow(img_copia)
```

No trecho `if re.match(padrao_data, texto)`, ele está fazendo uma caixa de texto e está utilizando essa mesma caixa de texto mais abaixo no código, `x, y, img_copia = caixa_texto(resultado, img_copia`. Vamos utilizar uma nova cor, passando também um novo parâmetro. Primeiro, temos que lembrar que estamos em BGR e não RGB. Nosso destaque será em vermelho, então, colocaremos `(0,0,255)`.

Outra funcionalidade importante que podemos tentar implementar, para além do destaque na informação, é capturar as informações em texto, salvando em uma nova variável. Assim, poderemos utilizá-las fora da imagem. Na mesma célula, antes de `img_copia = rgb.copy()`, vamos escrever `datas=`, vamos abrir uma lista vazia, `data = []` e, ao final do código, depois do `re.match()`, vamos fazer `datas.append(texto)` e ele fará o `append` do texto.

```go
datas = []
img_copia = rgb.copy()
for i in range(0, len(resultado['text'])):
  confianca = int(resultado['conf'][i])
  if confianca > min_conf:
    texto = resultado['text'][i]

    if re.match(padrao_data, texto):
      x, y, img = caixa_texto(resultado, img_copia, (0,0,255))
      img_copia = escreve_texto(texto, x, y, img_copia, fonte, 12)
      datas.append(texto)
    else:
      x, y, img_copia = caixa_texto(resultado, img_copia)


cv2_imshow(img_copia)
```

Vamos rodar!

![Tabela de "Despesas bancárias" com todas as palavras, sinais de igual e datas da primeira e terceira coluna envoltas por uma moldura azul/bounding box. As molduras/bounding boxes das datas da segunda coluna são vermelhas, criando um destaque em relação aos demais elementos. Acima delas, está escrito em branco, respectivamente: 10/02/2021 e 04/02/2023.](https://cdn1.gnarususercontent.com.br/1/563691/8ed388d2-a345-43c8-98cf-1971da15b321.png)

Conseguimos criar o destaque vermelho, por isso, a visualização da informação está um pouco melhor. Agora, vamos visualizar como está a nossa lista de datas, chamando apenas `datas`.

```undefined
datas
```

> ['10/02/2021', '04/02/2021']

Isso é bastante interessante, pois, se tivermos um documento com várias datas, e-mails, nomes, ou outras informações repetidas, que nos permitem ou não utilizar o regex, podemos retirá-las/capturá-las e colocá-las em uma lista. Desta maneira, poderemos manipulá-las e utilizá-las no Python outra vez. Portanto, além de destacar a imagem e fornecer essa informação para quem está lendo, é possível enviá-la para listas do Python.

Essa é mais uma das funções do OCR. Nos encontramos na próxima aula
Agora que você já aprendeu como funciona o Regex e como destacamos as informações das imagens usando cores diferentes na caixa delimitadora, agora é sua vez de colocar a mão na massa!

Na pasta Atividades, dentro do GitHub, você vai encontrar a imagem **Aula4_cotacao.png** e agora irá aplicar o Regex para destacar todas as informações que contém valores de hora na imagem! Quais alternativas resultam em **TODOS** os valores de horas destacados em vermelho?

![Captura de tela de um banco de dados apresentado no Kaggle sobre a cotação atualizada do valor do dólar e do real. A imagem é predominantemente branca com as letras em cinza, porém o maior destaque são as caixas ao redor do texto. Quase todos os valores de texto têm caixas azuis ao redor para representar que é texto, apenas os valores de hora são representados com caixas vermelhas para um maior destaque destes valores.](https://caelum-online-public.s3.amazonaws.com/2663-visao-computacional/04/Aula4_cotacaofeita.png)

Selecione 2 alternativas

-   ```go
    import re
    horas = []
    min_conf = 25
    config_tesseract = "--tessdata-dir tessdata"
    padrao_hora = '([01]?[0-9]|2[0-3]):[0-5][0-9](:[0-5][0-9])?'
    
    img = cv2.imread('/content/text-recognize/Atividades/Aula4_cotacao.png')
    rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    resultado = pytesseract.image_to_data(rgb, config=config_tesseract, lang="por", output_type=Output.DICT)
    
    img_copia = rgb.copy()
    for i in range(0, len(resultado['text'])):
      confianca = int(resultado['conf'][i])
      if confianca > min_conf:
        texto = resultado['text'][i]
        if re.match(padrao_hora, texto):
          x, y, img = caixa_texto(resultado, img_copia, (0,0,255))
          horas.append(texto)
        else:
          x, y, img_copia = caixa_texto(resultado, img_copia)
    cv2_imshow(img_copia)
    ```
    
-   ```go
    import re
    horas = []
    config_tesseract = "--tessdata-dir tessdata"
    padrao_hora = '([01]?[0-9]|2[0-3]):[0-5][0-9](:[0-5][0-9])?'
    
    img = cv2.imread('/content/text-recognize/Atividades/Aula4_cotacao.png')
    rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    resultado = pytesseract.image_to_data(rgb, config=config_tesseract, lang="por", output_type=Output.DICT)
    
    img_copia = rgb.copy()
    for i in range(0, len(resultado['text'])):
      confianca = int(resultado['conf'][i])
      if confianca > min_conf:
        texto = resultado['text'][i]
        if re.match(padrao_hora, texto):
          x, y, img = caixa_texto(resultado, img_copia, (0,0,255))
          horas.append(texto)
        else:
          x, y, img_copia = caixa_texto(resultado, img_copia)
    cv2_imshow(img_copia)
    ```
    
-   ```go
    import re
    data = []
    config_tesseract = "--tessdata-dir tessdata"
    padrao_data = '^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[012])/(19|20)\d\d$'
    
    img = cv2.imread('/content/text-recognize/Atividades/Aula4_cotacao.png')
    rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    resultado = pytesseract.image_to_data(rgb, config=config_tesseract, lang="eng", output_type=Output.DICT)
    
    img_copia = rgb.copy()
    for i in range(0, len(resultado['text'])):
      confianca = int(resultado['conf'][i])
      if confianca > min_conf:
        texto = resultado['text'][i]
        if re.match(padrao_data, texto):
          x, y, img = caixa_texto(resultado, img_copia, (0,0,255))
          data.append(texto)
        else:
          x, y, img_copia = caixa_texto(resultado, img_copia)
    cv2_imshow(img_copia)
    ```
    
-   ```go
    import re
    horas = []
    config_tesseract = "--tessdata-dir tessdata"
    padrao_hora = '([01]?[0-9]|2[0-3]):[0-5][0-9](:[0-5][0-9])?'
    
    img = cv2.imread('/content/text-recognize/Atividades/Aula4_cotacao.png')
    rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    resultado = pytesseract.image_to_data(rgb, config=config_tesseract, lang="eng", output_type=Output.DICT)
    
    img_copia = rgb.copy()
    for i in range(0, len(resultado['text'])):
      confianca = int(resultado['conf'][i])
      if confianca > min_conf:
        texto = resultado['text'][i]
        if re.match(padrao_hora, texto):
          x, y, img = caixa_texto(resultado, img_copia, (0,0,255))
          horas.append(texto)
        else:
          x, y, img_copia = caixa_texto(resultado, img_copia)
    cv2_imshow(img_copia)
    ```