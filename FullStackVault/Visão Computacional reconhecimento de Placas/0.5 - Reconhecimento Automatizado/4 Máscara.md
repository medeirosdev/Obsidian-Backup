Agora aplicaremos uma transformação de fechamento à imagem para expandir a região clara da figura. Para isso, utilizaremos um kernel retangular com as proporções da placa. Dessa maneira, os contornos destacados com Sobel vão se expandir tornando a região mais clara. Em seguida, aplicaremos a limiarização para que esta região clara se torne branca.

Iniciaremos aplicando o efeito de desfoque _gaussian blur_, que deve remover alguns ruídos da imagem gerados pelo sobel. Para isso, em uma nova célula, armazene a função `cv2.GaussianBlur()` na variável `sobel_x`. Esta função receberá os parâmetros `sobel_x`, que diz respeito à imagem em que queremos aplicar o efeito; o tamanho de kernel `(5,5)`; e a intensidade do efeito `0`.

```ini
sobel_x = cv2.GaussianBlur(sobel_x, (5,5), 0)
```

Em seguida, aplicaremos a transformação de fechamento. Chame `sobel_x` e armazene o comando `cv2.morphologyEx()`. Passe `sobel_x`, `cv2.MORPH_CLOSE` e `kernel_retangular` como parâmetros da função.

```ini
sobel_x = cv2.GaussianBlur(sobel_x, (5,5), 0)
sobel_x = cv2.morphologyEx(sobel_x, cv2.MORPH_CLOSE, kernel_retangular)
```

Ainda nesta célula, chame o comando de visualização `cv2_imshow(sobel_x)`.

```makefile
sobel_x = cv2.GaussianBlur(sobel_x, (5,5), 0)
sobel_x = cv2.morphologyEx(sobel_x, cv2.MORPH_CLOSE, kernel_retangular)
cv2_imshow(sobel_x)
```

Aplicaremos, neste mesmo código, a limiarização da imagem. Para isso, crie as variáveis `valor` e `limiarizacao` e armazene a função `cv2.threshold()`, que deve receber os parâmetros `sobel_x`, `0`, `255` e `cv2.THRESH_BINARY | cv2.THRESH_OTSU`. Em seguida, ordene a visualização `cv2_imshow(limiarizacao)`.

```makefile
sobel_x = cv2.GaussianBlur(sobel_x, (5,5), 0)
sobel_x = cv2.morphologyEx(sobel_x, cv2.MORPH_CLOSE, kernel_retangular)
cv2_imshow(sobel_x)

valor, limiarizacao = cv2.threshold(sobel_x, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
cv2_imshow(limiarizacao)
```

Execute a célula. Ela deve nos retornar as seguintes imagens:

![Imagem do carro em preto e branco. A figura tornou-se um borrão. É possível perceber que trata-se de um carro, além de localizar alguns componentes como a placa e o símbolo, mas não se pode identificar os caracteres da placa e nem as palavras escritas no porta-malas.](https://cdn1.gnarususercontent.com.br/1/1310269/3aae4b46-c774-420f-ad47-4271a3fb9d74.png)

Perceba que a região da placa foi expandida, sendo possível identificá-la por um retângulo majoritariamente branco.

![Imagem preta com manchas brancas. É possível associar algumas dessas manchas brancas ao carro e a itens do carro como, por exemplo, um retângulo branco à placa do veículo.](https://cdn1.gnarususercontent.com.br/1/1310269/62153ad0-b1f5-4e3b-94c1-2f2e24d4b182.png)

Com a aplicação da limiarização, a região da placa tornou-se totalmente branca, assim como outras áreas da imagem.

A partir da imagem limiarizada, removeremos alguns ruídos que ainda permaneceram, como pequenos pontos brancos ao redor do veículo. Utilizaremos a erosão para realizar essa remoção, expandido a região preta da figura e preenchendo esses pontos brancos. Aplicaremos esse procedimento com um kernel de tamanho 3x3.

```ini
kernel_quadrado = cv2.getStructuringElement(cv2.MORPH_RECT, (3,3))
```

Em seguida, adicionamos o código responsável pelo procedimento de erosão. Usaremos o parâmetro `iterations = 2` informando que este procedimento deve ser aplicado duas vezes, ou seja, uma erosão seguida de outra

```ini
kernel_quadrado = cv2.getStructuringElement(cv2.MORPH_RECT, (3,3))
limiarizacao = cv2.erode(limiarizacao, kernel_quadrado, iterations = 2)
```

Aplicaremos, ainda, duas dilatações, para que as partes brancas não se distorçam após os processos de erosão e mantenham suas espessuras originais.

```ini
kernel_quadrado = cv2.getStructuringElement(cv2.MORPH_RECT, (3,3))
limiarizacao = cv2.erode(limiarizacao, kernel_quadrado, iterations = 2)
limiarizacao = cv2.dilate(limiarizacao, kernel_quadrado, iterations = 2)
```

Por fim, chame o comando de visualização `cv2_imshow(limiarizacao)`.

```makefile
kernel_quadrado = cv2.getStructuringElement(cv2.MORPH_RECT, (3,3))
limiarizacao = cv2.erode(limiarizacao, kernel_quadrado, iterations = 2)
limiarizacao = cv2.dilate(limiarizacao, kernel_quadrado, iterations = 2)
cv2_imshow(limiarizacao)
```

Execute esta célula e observe a imagem retornada.

![Imagem anterior com menos ruídos brancos.](https://cdn1.gnarususercontent.com.br/1/1310269/9c902293-4c02-431e-ad98-9e140aab1c6b.png)

Perceba que vários ruídos brancos foram removidos e a imagem está mais limpa.

A partir de agora aplicaremos um efeito de máscara, que realiza um filtro na imagem limiarizada. Para realizar esse filtro, uma imagem é sobreposta à outra e toda a região de cor branca na máscara deve permanecer na imagem. As regiões pretas, no entanto, serão removidas. Criaremos essa máscara a partir da imagem em escala de cinza.

Primeiramente, aplicaremos um efeito de fechamento na imagem em escalas de cinza para expandir a região mais clara.

```ini
fechamento = cv2.morphologyEx(imagem, cv2.MORPH_CLOSE, kernel_quadrado)
```

Agora aplicamos a limiarização a este fechamento e adicionamos o comando de visualização `cv2_imshow(mascara)`

```makefile
fechamento = cv2.morphologyEx(imagem, cv2.MORPH_CLOSE, kernel_quadrado)
valor, mascara = cv2.threshold(fechamento, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
cv2_imshow(mascara)
```

Execute esta célula. Ela deve nos retornar a seguinte imagem:

![Imagem do carro em preto e branco. É possível visualizar a placa na cor branca com os caracteres "BDM3D69" na cor preta.](https://cdn1.gnarususercontent.com.br/1/1310269/9d8ce265-b506-44a4-a416-0846996f67d0.png)

Esta deve ser nossa máscara. A região da placa, por ser mais clara, tornou-se branca. Sendo assim, quando a utilizarmos como máscara, somente as regiões brancas serão mantidas na imagem limiarizada. Vamos aplicá-la!

Utilizaremos a função `bitwise_and()` que nos permite sobrepor cada um dos pixels de duas imagens limiarizadas, por isso receberá o parâmetro `limiarizacao` duas vezes. Passamos, ainda, a máscara `mask = mascara`.

```ini
limiarizacao = cv2.bitwise_and(limiarizacao, limiarizacao, mask = mascara
```

Perceba que os caracteres da placa estão em preto, portanto, aplicaremos duas dilatações para preenchê-los.

```ini
limiarizacao = cv2.bitwise_and(limiarizacao, limiarizacao, mask = mascara
limiarizacao = cv2.dilate(limiarizacao, kernel_quadrado, iterations = 2)
```

Ainda nesta célula, aplicaremos uma erosão para que retorne a espessura dos caracteres.

```ini
limiarizacao = cv2.bitwise_and(limiarizacao, limiarizacao, mask = mascara
limiarizacao = cv2.dilate(limiarizacao, kernel_quadrado, iterations = 2)
limiarizacao = cv2.erode(limiarizacao, kernel_quadrado)
```

Por fim, chamamos o comando de visualização.

```makefile
limiarizacao = cv2.bitwise_and(limiarizacao, limiarizacao, mask = mascara
limiarizacao = cv2.dilate(limiarizacao, kernel_quadrado, iterations = 2)
limiarizacao = cv2.erode(limiarizacao, kernel_quadrado)
cv2_imshow(limiarizacao)
```

A imagem retornada deve ser esta:

![Imagem em preto com manchas brancas que podem ser associadas a alguns itens do carro. O retângulo branco, que condiz com a placa, apresenta pequenos ruídos pretos internos a ele. É possível, ainda, verificar uma faixa branca acima deste retângulo. Há, ainda, um círculo branco correspondente ao símbolo da marca *Renault*.](https://cdn1.gnarususercontent.com.br/1/1310269/ea7558eb-9cbe-4018-ab55-342843978312.png)

Perceba que muitas regiões foram removidas, mas ainda há partes que não correspondem à placa e precisam ser retiradas. Continuaremos com essa aplicação!