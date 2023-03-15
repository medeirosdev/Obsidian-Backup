O detector de bordas de Canny é um algoritmo bastante complexo para detectar os contornos dos objetos em uma imagem e passa por uma série de etapas até chegar ao resultado da transformação.

O primeiro passo é a redução de ruídos. Nesse sentido, a detecção de bordas é muito suscetível a ruídos na imagem, que podem interferir na detecção dos objetos de interesse na figura. Inicialmente, é aplicado um [filtro de desfoque (GaussianBlur)](https://docs.opencv.org/3.4/d4/d13/tutorial_py_filtering.html) na imagem para reduzir os ruídos.

O segundo passo é encontrar a intensidade do gradiente na imagem: O gradiente na imagem é a diferença de intensidade de cor em uma determinada direção. O cálculo do gradiente é feito com base na direção horizontal e vertical da figura através de um [algoritmo chamado Sobel](https://docs.opencv.org/3.4/d4/d86/group__imgproc__filter.html#gacea54f142e81b6758cb6f375ce782c8d).

O terceiro passo é fazer uma supressão, pois uma vez feito o cálculo do gradiente, um escaneamento será feito na figura pixel a pixel, checando em cada um dos pixels se o gradiente é o maior valor dentro de uma vizinhança próxima. Caso o pixel tenha uma magnitude do gradiente máxima localmente, este é escolhido como uma borda. Isso resulta em uma imagem com bordas finas dos objetos.

O último passo consiste em fazer um limite de histerese – a histerese é a tendência de um sistema de conservar suas propriedades –, esse passo decidirá quais bordas serão realmente contornos e quais não serão. São escolhidos, portanto, dois valores de limiar: um limiar mínimo e um máximo. Qualquer contorno que tenha uma intensidade de gradiente maior que o limite máximo é mantido como borda. Aqueles que tiverem uma intensidade menor que o limite mínimo serão descartados. Os pixels que tiverem uma gradiente entre os valores mínimo e máximo são mantidos somente se estiverem conectados continuamente a um pixel com gradiente maior que o limite máximo.

Ao utilizar a função Canny da biblioteca OpenCV, é necessário passar como parâmetro a imagem que será feita a transformação e os limites mínimo e máximo do teste de histerese. Os valores utilizados em aula são os mesmos dos exemplos da documentação: 100 para o limite mínimo e 200 para o limite máximo.

Dado então toda essa contextualização e levando que essa atividade é encarada como desafio, sugiro que você modifique os valores de limite máximo e mínimo e veja a diferença no resultado da transformação de Canny para a imagem da placa utilizada na aula.

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/visao-computacional-deteccao-texto-placas-carro/113524/opinion)

Colocando os valores de limites mínimo e máximo como 0 e 100, respectivamente, a quantidade de bordas na imagem aumenta se comparado com os valores 100 e 200, aumentando a quantidade de informação dos objetos:

```makefile
bordas = cv2.Canny(imagem, 0, 100) 
cv2_imshow(bordas)
```

![alt text: Imagem de uma placa de carro toda em preto e com as bordas dos objetos representadas por linhas brancas finas](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/04/Aula4-img1.png)

Levando em conta os valores de limites mínimo e máximo como 200 e 550, respectivamente, a quantidade de bordas na imagem diminui se comparado com os valores 100 e 200, perdendo muita informação:

```makefile
bordas = cv2.Canny(imagem, 200, 600) 
cv2_imshow(bordas)
```

![alt text: Imagem de uma placa de carro toda em preto e com as bordas dos objetos representadas por linhas brancas finas](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/04/Aula4-img2.png)

 [DISCUTIR NO FORUM](https://cursos.alura.com.br/forum/curso-visao-computacional-deteccao-texto-placas-carro/exercicio-desafio-metodo-de-canny/113524/novo)