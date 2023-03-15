Agora, removeremos alguns ruídos que podem atrapalhar o processo de detecção da posição da placa. Para isso, utilizaremos a função `clear_border()`, da biblioteca _Scikit Image_, que elimina os pixels brancos que tocam a borda da figura.

Iniciaremos importando a biblioteca:

```javascript
from skimage.segmentation import clear_border
```

Em seguida, vamos aplicar o efeito à imagem.

Em uma variável `limiarizacao`, armazenamos a função `clear_border()` que receberá o parâmetro `limiarizacao`. Ainda nesta célula, chamamos o comando de visualização `cv2_imshow(limiarizacao)`.

```java
from skimage.segmentation import clear_border
limiarizacao = clear_border(limiarizacao)
cv2_imshow(limiarizacao)
```

Ao executá-la, deve nos retornar a seguinte imagem:

![Imagem preta com manchas brancas. As regiões brancas que correspondiam ao contorno do carro e tocavam a borda da imagem, foram removidas.](https://cdn1.gnarususercontent.com.br/1/1310269/b8e0a427-08d2-41d6-89bd-e60873897546.png)

Perceba que as regiões brancas que tocavam a borda da imagem foram removidas.

Agora, usaremos a função `findContours()` para identificar os contornos que restam. A função receberá a imagem `limiarizacao` em que deve ser aplicado o efeito, o parâmetro de hierarquia `cv2.RETR_TREE` e o argumento `CHAIN_APPROX_SIMPLES`, que pega os pontos inicial e final de cada contorno.

```undefined
contornos, hierarquia = cv2.findContours(limiarizacao, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLES)
```

Usaremos a função `sorted()` e definiremos os parâmetros `contornos`, `key = cv2.contourArea`, que informa que o ordenamento deve ser feito por tamanho de área, e `reverse = True`, para que sejam elencados do maior para o menor. Armazenaremos este comando em uma variável `contornos`.

```python
contornos, hierarquia = cv2.findContours(limiarizacao, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLES)
contornos = sorted(contornos, key = cv2.contourArea, reverse = True)
```

Adicionaremos, ainda, um filtro de lista que deve nos trazer somente os 10 primeiros resultados `[:10]`. Por fim, chamamos, a variável `contornos`.

```python
contornos, hierarquia = cv2.findContours(limiarizacao, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLES)
contornos = sorted(contornos, key = cv2.contourArea, reverse = True)[:10]
contornos
```

A execução desta célula deve nos retornar as coordenadas dos contornos presentes na imagem. A partir dessas coordenadas, extrairemos os possíveis retângulos, ou seja, áreas da placa. Mas, ao invés de utilizar a aproximação de polígonos, usaremos a proporção da placa 40x13.

Ao dividir essas medidas (40/13), chegamos a aproximadamente 3,07. Sendo assim, vamos identificar as áreas que se aproximam deste valor. Usaremos um valor um pouco maior, cerca de 3 - 3,5, levando em consideração os possíveis ruídos que podem influenciar no tamanho da área.

Faremos um loop que deve iterar por esses contornos, extrair o ponto inicial, altura e comprimento (x, y, w e h) através da funçaõ `cv2.boundingRect(contorno)` e fazer o cálculo de proporção `float(w)/h`, assumindo que será um valor do tipo float.

```bash
for contorno in contornos:
        x, y, w, h = cv2.boundingRect(contorno)
        proporcao = float(w)/h
```

Em seguida, faremos uma condicional para estabelecer se o valor da proporção é maior ou igual a 3 e menor ou igual a 3,5. Sendo a condição verdadeira, armazenaremos esse contorno na variável `placa` com as coordenadas de y até a altura h e de x até o coprimento w, fazendo o recorte da placa.

```bash
for contorno in contornos:
        x, y, w, h = cv2.boundingRect(contorno)
        proporcao = float(w)/h
        if proporcao >=3 and proporcao <= 3.5:
            placa = imagem[y:y+h, x:x+w]
```

Agora, extrairemos a região de interesse, que é a imagem da placa limiarizada, e aplicaremos a função `clear_border()` para extrair possíveis ruídos em torno da imagem. Por fim, chamamos dois comandos visualização para vermos a placa e a região de interesse.

```css
for contorno in contornos:
        x, y, w, h = cv2.boundingRect(contorno)
        proporcao = float(w)/h
        if proporcao >=3 and proporcao <= 3.5:
            placa = imagem[y:y+h, x:x+w]
            valor, regiao_interesse = cv2.threshold(placa, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
            regiao_interesse = clear_border(regiao_interesse)
            cv2_imshow(placa)
            cv2_imshow(regiao_interesse)
```

Ao executar esta célula, ela deve nos retornar as seguites imagem:

![Recorte da placa do carro em escalas de cinza. Em letras garrafais, "BDM3D69". No canto inferior esquerdo, "BR". Há uma barra superior mais escura onde lê-se "BRASIL". No canto direito desta barra, a bandeira do Brasil.](https://cdn1.gnarususercontent.com.br/1/1310269/e6b34dff-d65b-4032-9111-49b5a8ec55a7.png)

![Imagem anterior em tons de preto e branco. A placa possui cor branca e os textos "BDM3D69" e "BR" estão em preto. "BRASIL" está na cor branca.](https://cdn1.gnarususercontent.com.br/1/1310269/1ef52a60-6069-4812-9ed8-2475f3d8a73b.png)

Perceba que foi extraída exatamente a região da placa e aplicada a limiarização.

Agora, usaremos esse recorte para detectar o texto com o _Tesseract_.

```lua
texto = pytesseract.image_to_string(regiao_interesse, lang = 'por', config = config_tesseract)
print(texto)
```

Ao executar este código, deve nos retornar ".BDM3D69". Para eliminar possíveis erros no texto advindos de ruídos, utilizaremos _Regex_ para extrair o texto principal da placa.

```bash
texto_extraido = re.search('\w{3}\d{1}\w{1}\d{2}', texto)
texto_extraido
```

Ao rodar esta célula, será encontrado um objeto. Para mostrá-lo, execute `print(texto_extraido.group(0))`.

```scss
print(texto_extraido.group(0))
```

O texto "BDM3D69" deve ser mostrado na tela. Pronto! Conseguimos identificar corretamente o texto. Nossa estratégia funcionou!