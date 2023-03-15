A limiarização, um dos processos mais simples de segmentação de imagens, se baseia na intensidade de cor dos pixels para realizar uma transformação. Em uma imagem em escala de cinza, a partir de um valor denominado limiar, os pixels da imagem serão segmentados em dois grupos: o grupo de pixels com intensidade de cinza abaixo do limiar e o grupo de pixels com intensidade de cinza acima do limiar. Esse limiar pode ser definido globalmente, servindo para todos os pixels da imagem simultaneamente, ou localmente, onde cada região da imagem terá um limiar diferente.

A imagem limiarizada será aquela em que cada um dos grupos de pixels segmentados receberá um valor fixo de intensidade de cinza. De forma alternativa, um dos grupos pode manter a intensidade original, enquanto o outro grupo receberá um valor fixo. As formas diferentes de realizar a limiarização através da biblioteca OpenCV são:

-   cv.THRESH_BINARY: Valor fixo x, caso a intensidade da cor do pixel seja maior que limiar, e 0 caso contrário
    
-   cv.THRESH_BINARY_INV: Valor fixo x, caso a intensidade da cor do pixel seja menor que limiar, e 0 caso contrário
    
-   cv.THRESH_TRUNC: Valor do limiar, caso a intensidade da cor do pixel seja maior que o limiar, e a intensidade original caso contrário
    
-   cv.THRESH_TOZERO: Intensidade original, caso a intensidade da cor do pixel seja maior que o limiar, e 0 caso contrário
    
-   cv.THRESH_TOZERO_INV: Intensidade original, caso a intensidade da cor do pixel seja menor que o limiar, e 0 caso contrário
    

Um exemplo da [documentação da biblioteca Opencv](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html) mostra cada um desses modos aplicados a uma imagem em escala de cinza.

![Conjunto de 6 imagens em preto e branco com títulos: Original Image: degradê do preto para o branco da esquerda para a direita. BINARY: Imagem cortada ao meio, a parte esquerda é preta e a parte direita é branca, BINARY_INV: Imagem cortada ao meio, a parte esquerda é branca e a parte direita é preta, TRUNC: Imagem cortada ao meio, a parte esquerda é um degradê do preto para o cinza, a parte direita está na cor cinza, TOZERO: Imagem cortada ao meio, a parte esquerda é preta, a parte direita é um degradê do cinza para o branco, TOZERO_INV: Imagem cortada ao meio, a parte esquerda é um degradê do preto para o cinza, a parte direita é preta](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/02/Aula2-img1.png)

A escolha do método de limiarização mais adequado pode depender das condições de iluminação da imagem e do tipo de projeto que está sendo realizado.