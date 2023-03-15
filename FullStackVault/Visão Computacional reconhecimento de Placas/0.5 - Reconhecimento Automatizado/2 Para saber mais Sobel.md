O operador de Sobel é utilizado para destacar as bordas dos objetos em imagens e é utilizado no algoritmo de detecção de bordas de Canny. Ele calcula a diferença de intensidades da cor cinza em uma direção x ou y através de um kernel pré-definido de tamanho 3x3 e operações de **convolução - operação matemática envolvendo matrizes que será brevemente explicada nos parágrafos abaixo, juntamente com uma referência para saber mais**. Os kernels utilizados pelo Sobel são:

-   Kernel na direção x:

![alt text: Matriz com 3 linhas e 3 colunas. Primeira coluna: -1,-2 e -1. Segunda coluna: 0,0,0. Terceira coluna: 1,2,1](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/05/Aula5-img1.png)

-   Kernel na direção y:

![alt text: Matriz com 3 linhas e 3 colunas. Primeira coluna: -1,0 e 1. Segunda coluna: -2,0,2. Terceira coluna: -1,0,1](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/05/Aula5-img2.png)

A convolução é uma operação que toma cada um dos valores da matriz do kernel multiplicando pela intensidade do pixel e soma todo o resultado em cada uma das regiões da imagem de tamanho 3x3.

A partir desses valores é possível identificar a diferença de intensidade dos pixels nas direções x e y e aqueles valores que forem maiores podem representar uma borda, visto que a borda pode ser entendida como uma mudança brusca na tonalidade dos pixels próximos uns aos outros.

Caso queira saber mais a respeito sobre essa transformação, consulte a documentação do openCV sobre o [Sobel](https://docs.opencv.org/3.4/d2/d2c/tutorial_sobel_derivatives.html).

Se tiver curiosidade sobre a operação de convolução ou outros kernels que geram outras transformações, cheque a [wiki sobre kernel](https://en.wikipedia.org/wiki/Kernel_%28image_processing%29).