Anteriormente, aplicamos a limiarização de Otsu na imagem da placa em escalas de cinza e observamos que ficaram algumas falhas em branco dentro dos caracteres. Para tentar corrigir esse problema, utilizaremos outros pré-processamentos a fim de viabilizar a detecção do texto pelo _Tesseract_.

O pré-processamento que aplicaremos é conhecido como transformação morfológica e divide-se em vários subtipos, aos quais temos acesso na [documentação da biblioteca _OpenCV_](https://docs.opencv.org/4.x/d9/d61/tutorial_py_morphological_ops.html). Vale ressaltar que essas transformações geralmente são aplicadas em imagens que já estão limiarizadas, mas, para entender este processo, antes precisamos compreender como funciona um _Kernel_.

_Kernel_, também chamado de elemento estruturante ou núcleo, é uma região de vizinhança onde será feita a transformação com base no pixel de referência. Ou seja, há uma vizinhança em torno de cada pixel e, dependendo de como funciona essa vizinhança, aplicaremos algum processamento naquele pixel. Existem vários tipos de _Kernel_, são eles retangular, elíptico e em forma de cruz. É necessário adotar um dos tipos e definir o seu tamanho.

A transformação morfológica, por sua vez, divide-se em **erosão** e **dilatação**, e é a partir destas que podemos construir outros tipos de modificações. A erosão expande os pixels pretos enquanto a dilatação expande os pixels brancos. Vamos a um exemplo!

Esta é a imagem original:

![Letra "J" na cor branca em um fundo preto.](https://cdn1.gnarususercontent.com.br/1/1310269/f11bdc7b-85f0-4343-bc09-fa22afac945a.png)

Após aplicar a erosão, a imagem assume esta forma:

![A letra "J", agora, está mais fina.](https://cdn1.gnarususercontent.com.br/1/1310269/50378ae4-cbbd-4653-bfe9-7d3be55f7ab0.png)

Perceba que a letra está mais fina, pois os pixels pretos se expandiram e preencheram parte da borda do caractere, tornando a região de preenchimento branco mais estreita.

Ao aplicar a dilatação, no entanto, ocorre o efeito contrário:

![Letra "J" mais grossa que na formatação original.](https://cdn1.gnarususercontent.com.br/1/1310269/64f5a68d-bd2f-464f-8cb0-4cb2f425f6dd.png)

Agora, os pixels brancos que se expandiram e preencheram a borda da letra, enlarguecendo a região de preenchimento branco e, consequentemente, a letra também.

Hora de aplicar a transformação morfológica na nossa placa!

De volta ao _Colab_, iniciaremos com a definição do _Kernel_. Para isso, crie uma variável `kernel` que deve receber a função `cv2.getStructuringElement()`. Esta função possui dois argumentos: o tipo de _Kernel_, que será retangular, `cv2.MORPH_RECT`, e o tamanho desse _Kernel_ `(5,5)`.

```ini
kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (5,5))
```

Execute esta célula.

Agora, aplicaremos a erosão à imagem da placa limiarizada por Otsu.

Em uma variável `erosao`, chamamos a função `cv2.erode()` que deve receber como parâmetros `lim_otsu`, que é a imagem limiarizada, e `kernel`, que configuramos anteriormente. Por fim, chamamos o comando de visualização `cv2_imshow(erosao)`.

```makefile
erosao = cv2.erode(lim_otsu, kernel)
cv2_imshow(erosao)
```

Ao executar este comando, perceba que as falhas brancas internas aos caracteres foram preenchidas, pois os pixels em preto foram expandidos.

![Placa de carro na cor branca com os caracteres "PLR3D97" em letras garrafais pretas. No canto inferior esquerdo, a sigla "BR", também em preto. Há uma barra superior na cor preta onde é possível visualizar "BRASIL" na cor branca, embora os caracteres sejam bem finos e apresentem falhas. Ao final desta barra, no canto direito, a bandeira do Brasil apresenta manchas que inviabilizam sua identificação.](https://cdn1.gnarususercontent.com.br/1/1310269/6448dbfa-da78-4bb6-8ba7-f645b8bf23a1.png)

Aplicaremos, agora, o procedimento de dilatação. Para isso, em uma nova célula, criaremos uma variável `dilatacao` que deve receber a função `cv2.dilate()`. Esta função, por sua vez, receberá os parâmetros `lim_otsu` e `kernel`. Por fim, acrescente o comando de visualização `cv2_imshow(dilatacao)`.

```makefile
dilatacao = cv2.dilate(lim_otsu, kernel)
cv2_imshow(dilatacao)
```

Ao executar este comando, ele nos retornará esta imagem:![Placa de carro na cor branca. Os caracteres "PLR3D97", em letras garrafais pretas, possuem diversas manchas brancas que dificultam a identificação, embora não impossibilitem. A sigla "BR", no canto inferior esquerdo, desapareceu e, em seu lugar, há somente uma leve mancha preta. Há uma barra superior na cor preta onde é possível identificar "BRASIL" em letras brancas. Ao final desta barra, no canto direito, a bandeira do Brasil já não pode ser identificada, pois assumiu a forma de um quadrado branco com um leve ruído na cor preta.](https://cdn1.gnarususercontent.com.br/1/1310269/006d0952-5604-4411-977a-d53056d414ae.png)

Perceba que os pixels em branco foram expandidos, portanto, as falhas brancas assumiram formas maiores. É importante lembrar que o tamanho do _Kernel_ impacta diretamente na expansão dos pixels pretos ou brancos. Sendo assim, a transformação por dilatação não gerou um resultado satisfatório.

A seguir veremos como utilizar outros processos de transformação morfológica em nossa figura!

O kernel ou elemento estruturante é uma matriz de valores que servem como uma máscara para a imagem, e a partir dessa máscara podem ser feitas transformações de acordo com certas condições. O kernel pode possuir diferentes formatos bem como diferentes dimensões, de modo que cada uma dessas escolhas reflete em como a transformação na imagem será realizada.

Exemplos de kernel com tamanho 5x5:

-   Kernel retangular:

![alt text: Matriz com 5 linhas e 5 colunas totalmente preenchida por valores 1](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/03/Aula3-img1.png)

-   Kernel elíptico:

![alt text: Matriz com 5 linhas e 5 colunas. Todos os valores da matriz são 1 com exceção da primeira e da última linha, em que apenas o terceiro elemento é 1 e os demais são 0. Valores 0 estão em fundo preto, valores 1 estão em fundo branco.](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/03/Aula3-img2.png)

-   Kernel em cruz:

![alt text: Matriz com 5 linhas e 5 colunas. Todos os valores da matriz são 0 com exceção de toda a terceira linha e toda a terceira coluna, que estão preenchidas com valor 1, formando uma cruz na matriz como um todo. Valores 0 estão em fundo preto, valores 1 estão em fundo branco.](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/03/Aula3-img3.png)

Na aplicação de erosão, o kernel utilizado passa por cada pixel da imagem e verifica se os pixels na vizinhança em que o kernel é igual a 1 são brancos. Caso todos sejam brancos, o pixel na imagem transformada se torna branco. Caso pelo menos 1 pixel na vizinhança em que o kernel é igual a 1 não seja branco, o pixel na imagem transformada se torna preto.

O procedimento de dilatação é o contrário. A dilatação considera que caso pelo menos 1 pixel da vizinhança em que o kernel é igual a 1 seja branco, o pixel da imagem transformada se torna branco, expandindo assim a área branca da figura.

Os kernels também podem ser utilizados para outros tipos de transformações, utilizando matrizes com valores numéricos diferentes de 0 e 1. A partir desses valores é feita uma operação com os pixels da imagem chamada de convolução, retornando uma figura transformada. Você pode checar alguns exemplos através do [link](https://en.wikipedia.org/wiki/Kernel_%28image_processing%29).