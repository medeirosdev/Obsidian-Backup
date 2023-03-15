Agora que encontramos as coordenadas dos contornos da imagem, identificaremos aqueles que possuem quatro lados. No entanto, observe que o contorno da placa não é totalmente linear e apresenta diversos ruídos.

Através da função `cv.approxPolyDP()`, podemos aproximar um contorno de um polígono. Essa função recebe como parâmetros o contorno da figura, um `epsilon`, que se trata de uma margem de erro, e o `True` que serve para que esse polígono seja fechado, ou seja, comece e termine no mesmo ponto. O `epsilon` geralmente é calculado como uma porcentagem do perímetro através da função `cv.arcLength()`.

De volta ao _Colab_, vamos criar um loop for na variável `contornos` que deve iterar por cada um dos contornos gerados pela função _Canny_. Em seguida, criaremos a variável `epsilon`, que definiremos como `0.02`, ou seja, 2% do perímetro do contorno, vezes `*` a função `cv2.arcLength()`. Essa função recebe `contorno` e `True` como argumentos.

```yaml
for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
```

Agora, criaremos uma variável `aproximacao` que deve armazenar a função `cv2.approxPolyDP()`, responsável por associar cada contorno à um polígono. Os parâmetros dessa função serão `contorno`, `epsilon` e `True`.

```yaml
for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
```

Em seguida, criaremos uma condicional que deve conferir se o contorno criado é convexo, ou seja, se podemos traçar uma linha de qualquer ponto a qualquer outro ponto dentro do polígono, sem cortar a sua borda. Aplicaremos, também, outra condição que diz respeito sobre o tamanho da aproximação ser igual a 4, no caso, se gera 4 coordenadas, performando 4 lados.

```css
for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if cv2.isContourConvex(aproximacao) and len(aproximacao) == 4:
```

Se essas condições forem verdadeiras, deve-se armazenar `aproximacao` na variável `localizacao`. Por fim, utilizaremos um `break` para parar a execução ao encontrar este contorno de 4 lados.

```css
for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if cv2.isContourConvex(aproximacao) and len(aproximacao) == 4:
        localizacao = aproximacao
        break
```

Rode esta célula e, em uma nova, execute `localizacao` para termos acesso ao resultado.

```undefined
localizacao
```

Perceba que nos retorna 4 coordenadas, que consistem nos 4 pontos do polígono.

A seguir, veremos se o polígono identificado condiz com a posição da placa!
É possível fazer aproximação de contornos para polígonos, que são figuras geométricas com uma quantidade **n** de lados, utilizando a biblioteca OpenCV. A ideia utilizada em aula para encontrar a região da placa é encontrar os contornos da imagem, aproximar esses contornos para polígonos e extrair somente os polígonos que têm 4 lados e são convexos.

Escolha a alternativa que contém o código para executar a tarefa citada:

Selecione uma alternativa

-   ```css
    for contorno in contornos:
        aproximacao = cv2.approxPolyDP(contorno, True)
        if cv2.isContourConvex(aproximacao) and len(aproximacao) == 4:
              localizacao = aproximacao
              break
    ```
    
-   ```css
    for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if cv2.isContourConvex(aproximacao):
              localizacao = aproximacao
              break
    ```
    
-   ```python
    for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if len(aproximacao) == 4:
              localizacao = aproximacao
              break
    ```
    
-   ```css
    for contorno in contornos:
        epsilon = 0.02 * cv2.arcLength(contorno, True)
        aproximacao = cv2.approxPolyDP(contorno, epsilon, True)
        if cv2.isContourConvex(aproximacao) and len(aproximacao) == 4:
              localizacao = aproximacao
              break
    ```