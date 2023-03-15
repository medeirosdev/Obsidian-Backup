Você consegue entender como um computador armazena a informação de uma imagem, ou como a televisão consegue mostrar uma imagem na tela?

![alt text: monitor lcd com um zoom muito alto. No plano de fundo está a palavra Wiki e o zoom é aplicado no canto superior esquerdo da letra W. Os pixels do monitor podem ser visualizados no zoom, cada um contendo 3 faixas de cor verticais: vermelha, verde e azul](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/01/Aula1-img1.jpg)

Fonte da imagem: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Liquid_Crystal_Display_Macro_Example_zoom_2.jpg)

Uma imagem para o computador é formada por diversos pixels. Um pixel é a menor unidade que consegue conter uma informação única de cor. A quantidade de pixels na horizontal e na vertical formam a chamada resolução da imagem. Uma imagem Full HD por exemplo, precisa de cerca de 2 milhões de pixels para ser representada, com 1920 linhas de pixels na horizontal e 1080 colunas de pixels na vertical.

Para representar as mais diversas cores existentes, podem ser utilizadas 3 cores primárias: Azul (Blue), Verde (Green) e Vermelha (Red). A junção dessas três cores pode formar qualquer outra, conforme seja alterada a intensidade de cada uma delas.

Na biblioteca OpenCV, ao fazer a leitura de um arquivo de imagem, para a cor de cada pixel é armazenada a informação desses 3 canais de cores na ordem BGR (sigla para as cores em inglês: blue, green, red), com uma intensidade variando de 0 a 255 para cada uma delas. O valor 0 representa a ausência da cor, enquanto o 255 representa a intensidade mais forte da cor.

Para a detecção de textos, as cores da imagem não serão úteis e ocuparão espaço na memória, o que aumenta o tempo de processamento. Para melhorar o desempenho, é possível transformar uma imagem colorida para uma imagem em escala de cinza.

A cor cinza é equivalente a ter todos os canais de cor com a mesma intensidade, ou seja, ter a mesma quantidade de azul, verde e vermelho no pixel. Portanto, para realizar a transformação para a escala de cinza, basta retirar a média de intensidade de cada cor para cada pixel e armazenar o mesmo valor para BGR. Para poupar espaço de armazenamento, apenas um valor é armazenado, que contará como intensidade para as 3 cores simultaneamente.

 [DISCUTIR NO FORUM](https://cursos.alura.com.br/forum/curso-visao-computacional-deteccao-texto-placas-carro/exercicio-para-saber-mais-imagem-em-escala-de-cinza/113507/novo)