Utilizar a detecção de bordas de _Canny_ para identificar a posição da placa não funcionará em todos os casos, por isso aprenderemos uma forma de identificar esse posicionamento através da transformação morfológica _black hat_, ou _chapéu preto_, que dá um destaque maior a regiões escuras sobre um fundo claro. Para isso, utilizaremos a imagem a seguir:

![Traseira de um veículo na cor grafite. A imagem não permite visualizá-lo por inteiro e recorta parte do vidro traseiro. Na parte superior do porta-malas, há o símbolo prateado da marca *Renault*, que se assemelha a um losango. Abaixo deste símbolo, lê-se o nome do carro, "CAPTUR", em letras garrafais prateadas. Mais abaixo, placa branca de bordas pretas. Na placa, em letras garrafais pretas, "BDM3D69". Em seu canto inferior esquerdo, "BR" em letras pretas. Na parte superior da placa, há uma barra azul escrito "BRASIL" em letras brancas. No canto direito desta barra, a bandeira do Brasil. No canto inferior esquerdo do porta-malas, lê-se "RENAULT" em letras prateadas. O automóvel está sobre uma rua asfaltada, aparentemente no acostamento direito, onde observa-se alguns matos. Em segundo plano, algumas árvores.](https://cdn1.gnarususercontent.com.br/1/1310269/0ea89aa6-8a05-41bf-9d32-ad0e5840e3d0.jpg)

Na aba lateral esquerda, faça o upload da imagem "placa_carro3", que você deve ter baixado no início do curso. Em seguida, copie o caminho desta imagem armazenada no _Colab_.

Em uma nova célula, faremos a leitura dessa imagem. Crie uma variável `imagem`, chame a função `cv2.imread()` e passe o caminho da imagem como argumento desta função.

```ini
imagem = cv2.imread('/content/placa_carro3.jgp')
```

Ainda nesta célula, aplicaremos a transformação para escalas de cinza através da função `cv2.cvtColor()`. Os parâmetros serão `imagem` e a transformação para escalas de cinza `cv2.COLOR_BGR2GRAY`. Por fim, chame o comando de visualização `cv2_imshow(imagem)`.

```makefile
imagem = cv2.imread('/content/placa_carro3.jgp')
imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
cv2_imshow(imagem)
```

Ao executar, deve nos retornar a imagem em escalas de cinza:

![Imagem anterior em escalas de cinza.](https://cdn1.gnarususercontent.com.br/1/1310269/cc1bc15c-cb9f-4071-96d6-b9e9438525a5.png)

Perceba que topo da placa há um sombreamento, devido ao formato do porta-malas, o que pode dificultar a identificação dos contornos, por isso utilizaremos uma estratégia diferente da detecção de bordas de _Canny_: o _chapéu preto_.

Iniciaremos criando um _kernel_ retangular e atribuindo a ele as medidas da placa 40x13.

```ini
kernel_retangular = cv2.getStructuringElement(cv2.MORPH_RECT, (40,13))
```

Ainda nesta célula, faremos a transformação morfológica em uma variável `chapeu_preto`, onde chamaremos a função `cv2.morphologyEx()`, que receberá `imagem`; o tipo de transformação `cv2.MORPH_BLACKHAT`; e o kernel que criamos `kernel_retangular`. Por fim, chamamos o comando de visualização `cv2_imshow(chapeu_preto)`.

```makefile
kernel_retangular = cv2.getStructuringElement(cv2.MORPH_RECT, (40,13))
chapeu_preto = cv2.morphologyEx(imagem, cv2.MORPH_BLACKHAT, kernel_retangular)
cv2_imshow(chapeu_preto)
```

Execute esta célula e observe a imagem retornada:

![Imagem anterior nas cores preto e branco. Assemelha-se a uma pintura.](https://cdn1.gnarususercontent.com.br/1/1310269/9c009acd-e7e2-496f-b18d-b2727bb7d314.png)

Observe que, na região da placa, os caracteres ficaram bem destacados. Há, ainda, outras regiões da imagem que apresentam maior destaque, principalmente onde havia fundo escuro.

Agora tentaremos aplicar um destaque maior às bordas dos caracteres da placa, especificamente na direção x da imagem. Em seguida, utilizaremos um borrão para identificar a posição da placa. Para isso, usaremos a função `sobel`, que calcula a diferença entre os pixels em determinada direção e aplica valores positivos ou negativos.

Em uma nova célula, crie uma variável `sobel_x` e chame a função `cv2.Sobel()` que receberá como parâmetro a imagem `chapeu_preto`; a quantidade de bits dos cálculos que devem ser realizados `ddepth = cv2.CV_32F`, permitindo valores negativos e do tipo _float_, que serão convertidos posteriormente; `dx = 1` e `dy = 0` que nos dizem a direção em que o sobel deve ser aplicado nos eixos x e y; e a intensidade do efeito `ksize = 1`.

```ini
sobel_x = cv2.Sobel(chapeu_preto, ddepth = cv2.CV_32F, dx = 1, dy = 0, ksize = 1)
```

Em seguida calcularemos o sobel. Para isso, chame a variável `sobel_x` e armazene o comando `np.absolute(sobel_x)`, que deve calcular o valor absoluto de todos os valores calculados no Sobel. Para que isso seja possível, será necessário importar a biblioteca _Numpy_ inserindo o comando `import numpy as np` no início do código.

```java
import numpy as np

sobel_x = cv2.Sobel(chapeu_preto, ddepth = cv2.CV_32F, dx = 1, dy = 0, ksize = 1)
sobel_x = np.absolute(sobel_x)
```

Adicione, ainda, o comando `sobel_x = sobel_x.astype('uint8')` que possibilitará a conversão dos valores em float de 32 bits para 8 bits, pois as próximas transformações requerem que os valores estejam neste formato. Por fim, passe o código de visualização `cv2_imshow(sobel_x)`.

```java
import numpy as np

sobel_x = cv2.Sobel(chapeu_preto, ddepth = cv2.CV_32F, dx = 1, dy = 0, ksize = 1)
sobel_x = np.absolute(sobel_x)
sobel_x = sobel_x.astype('uint8')
cv2_imshow(sobel_x)
```

Execute a célula e perceba que há um destaque maior nas bordas dos caracteres da placa, na direção x, ou seja, na horizontal. Muitas das partes da figura resultado do _chapéu preto_ se dissiparam, pois não obtiveram destaque, embora ainda haja regiões de ruídos.

![Os caracteres da placa "BDM3D69" assumiram a cor preta com contornos brancos, ganhando maior destaque com relação às demais bordas da imagem, que não estão visivelmente demarcadas.](https://cdn1.gnarususercontent.com.br/1/1310269/51d49c36-e797-4fe2-9515-85fed141eb88.png)

A seguir, utilizaremos novas transformações morfológicas para aplicar um efeito de borrão à imagem, além de identificar a posição da placa!