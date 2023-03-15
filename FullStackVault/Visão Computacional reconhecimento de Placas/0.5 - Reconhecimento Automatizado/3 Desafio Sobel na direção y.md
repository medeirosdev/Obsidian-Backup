Na aula foi utilizada a transformação de Sobel para destacar as bordas na direção x da imagem, uma vez que esse efeito será útil para destacar a região da placa, que tem um comprimento maior do que a altura, nas proporções de 40 por 13.

Como desafio, utilize o efeito de Sobel na direção y e veja a diferença de resultado para a imagem de Sobel na direção x.

Para alterar o efeito Sobel na direção y, é necessário utilizar o valor 1 no parâmetro dy da função. O código para realizar o efeito Sobel na direção y é o seguinte:

```makefile
import numpy as np

imagem = cv2.imread('/content/placa_carro3.jpg')
imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
kernel_retangular = cv2.getStructuringElement(cv2.MORPH_RECT, (40, 13))
chapeu_preto = cv2.morphologyEx(imagem, cv2.MORPH_BLACKHAT, kernel_retangular)
sobel_x = cv2.Sobel(chapeu_preto, ddepth=cv2.CV_32F, dx=0, dy=1, ksize=1)
sobel_x = np.absolute(sobel_x)
sobel_x = sobel_x.astype("uint8")
cv2_imshow(sobel_x)
```

O resultado será uma imagem com as bordas destacadas na direção vertical:

![alt text: Imagem de um carro na visão traseira em preto e com as bordas dos objetos representadas por linhas brancas finas](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/05/Aula5-img3.png)

 [DISCUTIR NO FORUM](https://cursos.alura.com.br/forum/curso-visao-computacional-deteccao-texto-placas-carro/exercicio-desafio-sobel-na-direcao-y/113532/novo)