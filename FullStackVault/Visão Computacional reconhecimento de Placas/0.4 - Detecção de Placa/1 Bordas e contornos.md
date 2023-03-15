Já realizamos diversos pré-processamentos na imagem, mas ainda não foram suficientes para que o _Tesseract_ identificasse corretamente o texto presente na placa.

Utilizaremos, então, uma nova abordagem para detectar a posição da placa na imagem, fazer um recorte da placa e eliminar ruídos. Para isso, extrairemos as bordas presentes na imagem através de uma função. Após essa extração, pegaremos os contornos e os associaremos com polígonos. Os polígonos que apresentarem 4 lados serão considerados como possíveis regiões da placa.

Neste processo, usaremos a [detecção de bordas de _Canny_](https://docs.opencv.org/4.x/da/d22/tutorial_py_canny.html), da biblioteca _OpenCV_, que identifica as bordas presentes em uma imagem em escala de cinza. A função `cv.Canny()` recebe como parâmetros a imagem a ser analisada, e dois valores correspondentes ao limite inferior e superior, respectivamente. Esses limites servem para identificar quais bordas serão mostradas na imagem, sendo assim, as bordas acima do valor superior serão consideradas, assim como os pixels conectados a ela. As bordas abaixo do limite superior e não conectadas às que estão acima, serão desconsideradas, juntamente com as que estão abaixo do limite inferior.

Após a detecção dos contornos, precisaremos identificar suas coordenadas através da função `cv.findContours()`, que recebe como argumento a imagem a ser analisada, a informação de hierarquia (contornos internos a outros) e as coordenadas dos pixels. Você pode consultar as informações desta função [nesta seção](https://docs.opencv.org/4.x/d4/d73/tutorial_py_contours_begin.html) da biblioteca _OpenCV_.

De volta ao _Colab_, vamos aplicar esse processamento!

Em uma nova célula, crie uma variável `bordas` que deve armazenar a função `cv2.Canny()`. Esta função receberá a imagem em escala de cinza, `imagem`, e os limites inferior e superior, que serão `100` e `200`, respectivamente. Em seguida, passamos o comando de visualização `cv2_imshow(bordas)`.

```makefile
bordas = cv2.Canny(imagem, 100, 200)
cv2_imshow(bordas)
```

Execute a célula e observe a imagem:

![Placa de carro na cor preta com contornos brancos. Em letras garrafais, "PLR3D97". No canto inferior esquerdo, "BR". Na parte superior, centralizado, "BRASIL". No canto superior direito, a bandeira do Brasil. Todos os caracteres também assumiram contornos brancos, inclusive as manchas internas a eles.](https://cdn1.gnarususercontent.com.br/1/1310269/6ad89302-b035-4119-a1fb-51aca943a211.png)

Perceba que ele conseguiu identificar o contorno exato da placa e dos seus caracteres. Como a borda da placa é contínua, usaremos a função `findContours` para melhor defini-la.

Esta função retorna dois resultados, portanto, em uma nova célula, crie as variáveis `contornos`, correspondente às coordenadas, e `hierarquia`, que diz respeito aos contornos internos a outros. Nós não usaremos a hierarquia neste curso, mas precisamos defini-la porque trata-se de um retorno da função que aplicaremos.

Nessas variáveis, armazenaremos a função `cv2.findContours()` que receberá os parâmetros `bordas`, `cv2.RETR_TREE`, que guarda as informações de hierarquia, e `cv2.CHAIN_APPROX_SIMPLE`, que deve pegar os pontos inicial e final de cada coordenada dos contornos.

```undefined
contornos, hierarquia = cv2.findContours(bordas, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
```

Execute esta célula para salvar o comando e, em uma nova célula, chame a variável `contornos`.

```undefined
contornos
```

Perceba que nos retorna todas as coordenadas dos contornos geradas pela função `findContours` a partir da detecção de bordas.

A seguir, pegaremos esses contornos e tentaremos aproximá-los por polígonos, a fim de identificar quais possivelmente fazem parte da placa.