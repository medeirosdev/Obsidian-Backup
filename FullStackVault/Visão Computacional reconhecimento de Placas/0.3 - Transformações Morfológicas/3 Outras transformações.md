Agora veremos as últimas três transformações morfológicas que podemos aplicar em nossas imagens.

A primeira delas é o **gradiente morfológico** e se constrói através da diferença entre uma dilatação e uma erosão. O resultado obtido é a detecção das bordas dos caracteres da imagem.

A segunda transformação é chamada de **cartola** ou **tophat**. Ela é feita através da diferença entre a imagem original e a abertura realizada nessa imagem. É útil para detectar regiões claras em um fundo escuro.

A terceira é conhecida como **chapéu preto** ou **blackhat** e consiste na diferença entre a imagem original e o fechamento realizado nessa imagem. Ao contrário da **cartola**, é comumente utilizada para detectar regiões escuras em um fundo claro.

Vamos aplicar essas modificações à nossa figura!

De volta ao _Colab_, criaremos uma variável `gradiente` que receberá a função `cv2.morphologyEx()`. Esta função, por sua vez, recebe como parâmetros `lim_otsu`, que é a imagem limiarizada por _Otsu_, `cv2.MORPH_GRADIENTE`, que corresponde ao tipo de transformação por gradiente, e `kernel`, variável que configuramos anteriormente. Por fim, chamamos o comando de visualização `cv2_imshow(gradiente)`.

```makefile
gradiente = cv2.morphologyEx(lim_otsu, cv2.MORPH_GRADIENTE, kernel)
cv2_imshow(gradiente)
```

Ao executar esta célula, ela deve nos retornar a seguinte imagem:

![A placa assumiu a cor preta e seus caracteres são pretos com a borda branca. Há ainda, algumas manchas brancas internas aos caracteres "PLR3D97". A bandeira do Brasil assumiu a cor branca com manchas pretas, sendo inviável de identificá-la.](https://cdn1.gnarususercontent.com.br/1/1310269/d2e6b04e-3c54-48fc-afc2-03393f26bb58.png)

Perceba que as bordas dos caracteres e da própria placa foram melhores detectadas com a utilização deste gradiente.

Vamos aplicar a segunda transformação através do seguinte comando:

```makefile
cartola = cv2.morphologyEx(lim_otsu, cv2.MORPH_TOPHAT, kernel)
cv2_imshow(cartola)
```

Execute este código.

![Imagem preta com um retângulo de borda branca, correspondente à placa. O interior da placa, no entanto, assumiu a cor preta e há várias manchas brancas no lugar dos caracteres, porém não é possível identificá-los.](https://cdn1.gnarususercontent.com.br/1/1310269/fd9341d3-f12d-4f5b-a9fc-eebbc3252693.png)

Perceba que, nesta imagem, as falhas foram destacadas, pois o objetivo do cartola é identificar regiões claras em fundo escuro. Como nossos caracteres são escuros, destacou-se as falhas, escurecendo as demais partes e inviabilizando a identificação dos elementos.

É importante destacar que as formas cartola e chapéu preto podem ser aplicadas em imagens em escala de cinza, por isso adotaremos outro kernel. As placas de carro brasileiras possuem dimensões de 40cm de comprimento por 13cm de altura, então usaremos essas mesmas medidas no nosso kernel.

Para defini-lo, crie a variável `kernel_retangular` em uma nova célula e chame a função `cv2.getStructuringElement()`. Esta função recebe os parâmetros `cv2.MORPH_RECT`, que diz respeito ao tipo de kernel retangular, e `(40,13)` que define as dimensões deste kernel.

```ini
kernel_retangular = cv2.getStructuringElement(cv2.MORPH_RECT, (40,13))
```

Em seguida, adicione o comando anterior, `cartola`, alterando somente `kernel` para `kernel_retangular`:

```makefile
kernel_retangular = cv2.getStructuringElement(cv2.MORPH_RECT, (40,13))
cartola = cv2.morphologyEx(lim_otsu, cv2.MORPH_TOPHAT, kernel_retangular)
cv2_imshow(cartola)
```

Execute esta célula.

![A placa permanece na cor preta. Os caracteres "BR" estão na cor preta, mas com uma parte do fundo branco, permitindo sua identificação. "BRASIL" está escrito na cor branca e a bandeira do país assumiu cores de branco e preto, sendo possível identificá-la. O texto principal, "PLR3D97", continua na cor preta com manchas brancas, além disso, assumiu fundo branco em algumas letras e nos espaços entre essas letras. É possível distingui-los, embora com dificuldade.](https://cdn1.gnarususercontent.com.br/1/1310269/fc804e5a-da0c-4617-ad2f-422067ea8841.png)

Perceba que ele identificou melhor as regiões brancas em fundos escuros, no entanto, não consiste em um resultado satisfatório, pois encontramos dificuldade para definir os caracteres.

Vamos fazer esse procedimento na imagem em escalas de cinza. Para isso, aproveite o código anterior, altere `lim_otsu` por `imagem` e execute.

```makefile
cartola = cv2.morphologyEx(imagem, cv2.MORPH_TOPHAT, kernel_retangular)
cv2_imshow(cartola)
```

Ao executar, perceba que também foram detectadas as regiões claras em fundo escuro.

![Imagem semelhante a anterior, com os caracteres principais "PLR3D97" levemente mais visíveis.](https://cdn1.gnarususercontent.com.br/1/1310269/c030ac9a-72ff-4b06-8354-622421c737ac.png)

Aplicaremos, agora, o procedimento chapéu preto na imagem limiarizada por Otsu. Para isso, utilizaremos o seguinte comando:

```scss
chapeu_preto - cv2.morphologyEx(lim_otsu, cv2.MORPH_BLACKHAT, kernel_retang)
cv2_imshow(chapeu_preto)
```

Execute esta célula e observe a imagem retornada.

![Placa de carro preta com bordas brancas. Em letras garrafais na cor branca, "PLR3D97". No canto inferior esquerdo, "BR" também na cor branca. Na parte superior da placa, um retângulo branco com "BRASIL" escrito em preto. No canto superior direito, a bandeira do Brasil nas cores preto e branco.](https://cdn1.gnarususercontent.com.br/1/1310269/d7167d75-fe26-42a1-b915-1f2eb21e0b15.png)

Perceba que os caracteres foram melhor destacados.

Veremos qual seria o resultado dessa transformação na imagem em escalas de cinza. Para isso, execute o código a seguir em uma nova célula:

```scss
chapeu_preto - cv2.morphologyEx(imagem, cv2.MORPH_BLACKHAT, kernel_retang)
cv2_imshow(chapeu_preto)
```

A imagem retornada é a seguinte:

![Imagem semelhante à anterior, porém com os caracteres mais visíveis.](https://cdn1.gnarususercontent.com.br/1/1310269/26a29bf7-c39a-493f-b11e-0c289ad37c77.png)

Perceba que os caracteres em branco estão mais claros e melhor destacados, o que pode ajudar em nossas análises futuras.

Agora, tentaremos utilizar o _Tesseract_ na figura resultante do processo de erosão, pois os caracteres parecem melhor definidos.

Em uma nova célula, colocaremos a configuração do _Tesseract_: `config_tesseract = '--tessdata-dir tessdata --psm 6'`. Em seguida, criaremos uma variável `texto` e armazenaremos a função `pytesseract.image_to_string()`, que receberá `erosao`, imagem que passou pelo processo em questão, `lang = 'por'`, língua utilizada, e `config_tesseract`, configuração do nosso _Tesseract_. Por fim, chamaremos o comando de impressão `print(texto)`. O comando ficará assim:

```bash
config_tesseract = '--tessdata-dir tessdata --psm 6'
texto = pytesseract.image_to_string(erosao, lang = 'por', config_tesseract)
print(texto)
```

Execute esta célula e observe que foram retornados alguns caracteres. Perceba que o texto principal "PLR3D97" foi identificado como "PLRSD97", ou seja, trocou-se o "3" por "S". Note que há, ainda, alguns outros caracteres, provavelmente identificados erroneamente a partir dos ruídos presentes na imagem.

A seguir utilizaremos outras técnicas a fim de remover possíveis ruídos presentes na imagem, facilitando a detecção do texto pelo _Tesseract_. Te vejo lá!