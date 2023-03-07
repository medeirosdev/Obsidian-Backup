[[OpenCV]]Nessa aula, você aprendeu que conseguimos achar termos em textos e imagens utilizando a **biblioteca re**, de expressões regulares, porém alguns dos termos não foram destacados e aparentemente isso aconteceu por conta das letras estarem de formas diferentes, ou seja, a forma de pesquisa foi feita com todas as letras em minúscula e as palavras no texto tinham alguma letra maiúscula.

Para que isso não seja um impeditivo, **encontre** uma forma de fazer com que as palavras, independente da letra ser maiúscula ou minúscula no texto e no termo de pesquisa, sejam encontradas.
Para fazermos a comparação de termos e não ocorrer problemas com letras maiúsculas, como é o caso atual, podemos inserir um método do próprio Python para trabalhar com strings, que é o `.lower()`.

Então, quando temos a comparação entre `termo_pesquisa` com cada uma das palavras em `texto` na função `OCR_processa_imagem`, ao invés de deixarmos a linha como era anteriormente desta forma:

```yaml
if termo_pesquisa in texto:
```

Inserimos o método `.lower()` no final de cada uma das nossas variáveis, ou seja, ambas terão nesse caso apenas um retorno de caracteres minúsculos.

```lua
if termo_pesquisa.lower() in texto.lower():
```

Desse modo, a comparação será apenas entre a composição das palavras e não mais levando em consideração as letras maiúsculas e minúsculas.

O código final da função `OCR_processa_imagem` fica desta forma:

```python
def OCR_processa_imagem(img, termo_pesquisa, config_tesseract, min_conf):
  resultado = pytesseract.image_to_data(img, config=config_tesseract, lang='por', output_type=Output.DICT) #imagem para dados, que já fizemos anteriormente
  num_ocorrencias = 0 #inicializando como 0

  for i in range(0, len(resultado['text'])): # vai de 0 ao tamanho do número de valores do texto
    confianca = int(resultado['conf'][i]) # qual a confiança da detecção
    if confianca > min_conf: # se a confiança for maior que o valor mínimo, passa para a linha abaixo
      texto = resultado['text'][i] #texto será igual ao resultado text no momento i 
      if termo_pesquisa.lower() in texto.lower(): #se o termo de pesquisa estiver no texto:
        x, y, img = caixa_texto(i, resultado, img, (0,0,255)) # faz a caixa de bounding box
        img = escreve_texto(texto, x, y, img, fonte_dir, (50,50,225), 14) #escreve o texto 

        num_ocorrencias += 1 #faz a iteração no num de ocorrências e volta para o laço até acabar o texto
  return img, num_ocorrencias
```

# Para saber mais: salvando todas as imagens

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/visao-computacional-reconhecimento-texto-ocr-opencv/task/113569/next)

-   [](https://cursos.alura.com.br/suggestions/new/visao-computacional-reconhecimento-texto-ocr-opencv/113569/question)

Na aula 3, aprendemos como [salvar uma imagem](https://cursos.alura.com.br/course/visao-computacional-reconhecimento-texto-ocr-opencv/task/113556). O primeiro passo é criar a pasta que vai armazenar as imagens, utilizando o módulo **os**.

```lua
import os
os.makedirs('images_project', exist_ok=True)
```

Agora, o passo que faremos será semelhante aos passos feitos durante a aula 5, utilizando a estrutura for para passar em todas as imagens de uma vez e, após isso, o passo a passo para salvar a imagem será feito. Algo importante a ser feito também é definir o `termo_pesquisa` que guiará nossa busca de ocorrências.

```lua
termo_pesquisa = 'learning'
for imagem in caminho:
  img = cv2.imread( imagem)
  img_original = img.copy()
  nome_imagem = os.path.split(imagem)[-1]
  img, numero_ocorrencias = OCR_processa_imagem(img, termo_pesquisa, config_tesseract, min_conf)
```

Até agora conseguimos fazer com que a imagem seja mostrada com o uso da função `OCR_processa_imagem` e para salvar **apenas as imagens que contém o termo de pesquisa** faremos um if dentro do for que trás a seguinte condição `if numero_ocorrencias > 0` a imagem é salva, em caso negativo, ela não é mostrada.

```css
  if numero_ocorrencias > 0:
    mostrar (img)
    novo_nome_imagem = 'OCR_' + nome_imagem
    nova_imagem = 'images_project/' + str(novo_nome_imagem)
    cv2.imwrite(nova_imagem, img)
```

Então após a conferência do valor do número de ocorrências, a imagem é mostrada, logo em seguida definimos o novo nome da imagem que será OCR_ + o nome original da imagem, também é necessário definir a pasta que a imagem será salva, como a pasta criada foi a `images_project`, o caminho será o nome dessa pasta mais o `novo_nome_imagem`. Para salvar as imagens, vamos utilizar o mesmo comando que utilizamos na Aula 3 para salvar, `cv2.imwrite()`. Então o código final é:

```lua
termo_pesquisa = 'learning'
for imagem in caminho:
  img = cv2.imread( imagem)
  img_original = img.copy()
  nome_imagem = os.path.split(imagem)[-1]
  img, numero_ocorrencias = OCR_processa_imagem(img, termo_pesquisa, config_tesseract, min_conf)
  if numero_ocorrencias > 0:
    mostrar (img)
    novo_nome_imagem = 'OCR_' + nome_imagem
    nova_imagem = 'images_project/' + str(novo_nome_imagem)
    cv2.imwrite(nova_imagem, img)
```

**Parabéns** pela finalização do curso de **Reconhecimento de texto com OCR**. Esse treinamento é a "ponta do iceberg", isto é, apenas uma parte da visão computacional e reconhecimento de texto.

Nós estudamos sobre o **PyTesseract** e o **OpenCV**, entendemos como ele funciona e que também trabalha em BGR. Aprendemos a fazer a **análise de imagens** e que algumas imagens precisam de um padrão para que o OCR consiga entender o que está escrito nelas, para isso, usamos o Page Segmentation Modes (PSM).

Além disso, aprendemos a fazer _bounding boxes_, ou seja, caixas delimitadoras que podem ser aplicadas tanto em textos de alguma imagem, quanto para textos que buscamos com frequência, por exemplo, datas, e-mails ou textos únicos. É o caso do nosso projeto final, em que tínhamos uma pasta com várias imagens de textos grandes e buscamos uma palavra chamada "learning".

Nosso processo de aprendizado foi muito positivo. Começamos entendendo o que é o OCR e passamos por várias etapas até criarmos um projeto para o nosso portfolio. Espero que você continue estudando visão computacional e aprimore seus conhecimentos, porque ainda há muito a descobrir nesta área!

Como eu disse, o projeto que desenvolvemos pode ir para o seu portfolio. Não se esqueça de colocar no GitHub, compartilhar no LinkedIn, me marcar e marcar a **Alura**. Ficaremos muito felizes em ver o seu projeto! Além disso, você pode mandar feedbacks, contando sobre o que você gostou e o que poderia ser melhor.