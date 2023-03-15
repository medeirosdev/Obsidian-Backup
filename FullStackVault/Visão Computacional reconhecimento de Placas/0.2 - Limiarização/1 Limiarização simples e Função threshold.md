Podemos aplicar diversos pré-processamentos em uma imagem a fim de destacar seus caracteres e melhorar a detecção de textos do Tesseract. O primeiro pré-processamento que vamos aplicar é conhecido como **limiarização** e consiste em transformar uma imagem em escalas de cinza para preto e branco.

A seção ["Processamento de imagens em OpenCV"](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html), na documentação da biblioteca _OpenCV_, informa como podemos aplicar este procedimento. O primeiro passo é conhecido como "Limite Simples" ou "Limiarização simples" e, para entendê-lo, antes precisamos compreender o funcionamento dos pixels de uma imagem em escala de cinza.

Por definição, **pixel** é a unidade de medida padrão para imagens digitais. Consiste, portanto, na menor unidade que compõe uma imagem digital e é possível atribuir-lhe cor. De uma forma mais simples, é como se fosse um ponto, e a junção desses pontos formam a imagem inteira.

Cada um dos pixels de uma imagem em escala de cinza possui um valor, que varia de 0 a 255, correspondente à intensidade de cinza daquele pixel. Quanto mais próximo de 0, mais escuro é esse pixel, portanto, 0 representa a tonalidade preta. Da mesma forma, quanto mais próximo de 255, mais claro ele é, sendo 255 a cor branca.

No processo de limiarização simples, definimos um valor chamado de **limite** ou **limiar** com o qual iremos comparar a intensidade de todos os pixels da imagem. Caso o pixel tenha uma intensidade maior que o limite estabelecido, atribuiremos uma nova cor. Se a intensidade for menor que o limite, este pixel deve ser transformado para a cor preta, ou seja, 0.

Para esta etapa, utilizaremos o limiar ["cv.THRESH_BINARY"](https://docs.opencv.org/4.x/d7/d1b/group__imgproc__misc.html#ggaa9e58d2860d4afa658ef70a9b1115576a147222a96556ebc1d948b372bcd7ac59), que fará a transformação citada. Ele funciona da seguinte maneira: os pixels maiores que o limite devem ser transformados para o branco, ou seja, 255; e os menores, para 0, ou seja, preto. A função responsável por realizar este procedimento é `threshold`.

Vamos à um exemplo!

A imagem a seguir apresenta uma espécie de tabela onde cada célula apresenta um número e cor correspondente ao valor de sua intensidade na escala de cinza.

![Tabela em que cada célula apresenta um número e cor correspondente ao valor de sua intensidade na escala de cinza. Os números são, da esquerda para a direita, 201, 140, 30 e 86, na linha 1; 195, 140, 86 e 90, na linha 2; 46, 86, 160 e 190, na linha 3; 246, 96, 15 e 163, na linha 4; e 234, 94, 26 e 37, na linha 5. Os quadros 15, 26, 30, 37 e 46 possuem tons de cinza parecidos, mais próximos do preto. 86, 90, 94 e 96 possuem tons de cinza um pouco escuro, mas não próximos do preto. 140 é um tom de cinza intermediário e os números 160, 163, 190, 195 e 201, tons de cinza claro. Por fim, os números 234 e 246 apresentam variações claras do cinza, aproximando-se da cor branca.](https://cdn1.gnarususercontent.com.br/1/1310269/824ee971-e7b6-4299-9d7e-4e70c7b45d76.jpeg)

Ao estabelecermos, por exemplo, um limiar de 139, cada célula deve assumir o tom de preto, 0, ou de branco, 255, e ficará assim:

![As células, agora, variam entre as cores preto e branco e possuem a numeração correspondente à cor, sendo branco, 255, e preto, 0. Assumiu a seguinte ordem, da esquerda para direita: 255, 255, 0 e 0, na linha 1; 255, 255, 0 e 0, na linha 2; 0, 0, 255 e 255, na linha 3; 255, 0, 0 e 255, na linha 4; e 255, 0, 0 e 0, na linha 5.](https://cdn1.gnarususercontent.com.br/1/1310269/e3bf62e7-4551-40f1-91d1-2b133e76edbe.png)Agora aplicaremos este procedimento à imagem da nossa placa.

Em uma nova célula, definiremos o valor do limiar:

```ini
limiar = 25
```

Em seguida, utilizaremos a função `threshold`, que retorna dois valores. O primeiro diz respeito ao valor do limiar `valor`, e o segundo à imagem limiarizada `lim_simples`.

```makefile
limiar = 25
valor, lim_simples = cv2.threshold()
```

Esta função recebe três parâmetros: a imagem em escala de cinza, que é nossa variável `imagem`; a variável `limiar`, onde estabelecemos o valor do limite; a cor para a qual o pixel deve ser transformado caso sua intensidade seja maior que o limiar - estabeleceremos `255`, branco; e o procedimento de limiarização que vamos utilizar THRESH_BINARY, `cv2.THRESH_BINARY`.

```makefile
limiar = 25
valor, lim_simples = cv2.threshold(imagem, limiar, 255, cv2.THRESH_BINARY)
```

Ainda nesta célula, passaremos o comando de visualização `cv2_imshow(lim_simples)` para que seja retornada a variável `lim_simples`, ou seja, a imagem após o processo de limiarização.

```makefile
limiar = 25
valor, lim_simples = cv2.threshold(imagem, limiar, 255, cv2.THRESH_BINARY)
cv2_imshow(lim_simples)
```

Execute esta célula e observe que nos retorna a seguinte imagem:

![A placa de veículo, agora, limita-se a variações de cor preto e branco. Nela é possível identificar somente os caracteres "BR", no canto inferior esquerdo da placa, e "PLR3D97", ambos na cor preta e com falhas em branco. Não é possível diferenciar a barra correspondente à cor azul, tampouco o conteúdo "BRASIL" seguido da bandeira deste país.](https://cdn1.gnarususercontent.com.br/1/1310269/93da675e-75d6-4571-b67e-2a456a4510d8.png)

Todos os pixels de intensidade maior que 25 foram transformados para branco, e os de intensidade menor, para preto. Perceba que alguns caracteres ficaram muito falhados porque adotamos um limiar muito próximo da cor preta. Vamos alterá-lo!

Para isso, copie o código anterior, cole em uma nova célula e altere o limiar de 25 para 127:

```makefile
limiar = 127
valor, lim_simples = cv2.threshold(imagem, limiar, 255, cv2.THRESH_BINARY)
cv2_imshow(lim_simples)
```

Execute a célula e perceba que nos retornará uma imagem ainda em preto e branco, mas que permite a visualização dos demais caracteres da placa.

![Placa de veículo na cor branca. Em letras garrafais na cor preta, é possível ler "PLR3D97", com pequenas falhas brancas no interior dos caracteres. No canto inferior esquerdo, em letras menores e pretas, "BR". Há uma barra preta na parte superior da placa, escrito "BRASIL" na cor branca. Ao final desta barra, a bandeira do Brasil, também em tons de preto e branco.](https://cdn1.gnarususercontent.com.br/1/1310269/9d9d5c01-fa38-462f-905c-afa1ec189d27.png)

Perceba que eles estão visualmente mais destacados, embora ainda ocorram algumas pequenas falhas.

Para tentar aprimorar este resultado de limiarização, copie o código anterior, cole-o em uma nova célula e altere o valor do limiar para 170.

```makefile
limiar = 127
valor, lim_simples = cv2.threshold(imagem, limiar, 255, cv2.THRESH_BINARY)
cv2_imshow(lim_simples)
```

Ao executar este código, ele deve nos retornar a imagem com os caracteres mais destacados e as falhas preenchidas.

![Placa de veículo na cor branca. Em letras garrafais, na cor preta, é possível ler "PLR3D97". Ao lado esquerdo, possui um quadrado na cor preta. No canto inferior esquerdo, em letras menores e pretas, "BR". Há uma barra preta na parte superior da placa, escrito "BRASIL" na cor branca. Ao final desta barra, a bandeira do Brasil, também em tons de preto e branco.](https://cdn1.gnarususercontent.com.br/1/1310269/9c1d68bf-11a0-4919-a206-233c9bd4f40b.jpeg)

Perceba que, para encontrar este limiar, precisamos testar e aplicar diversos valores, o que não é tão interessante se pensarmos na otimização do projeto, por tratar-se de um trabalho manual.

Sendo assim, voltaremos à documentação de _OpenCV_ a fim de verificar quais outros procedimentos de limiarização podem ser aplicados!

O processo de limiarização pode ser aplicado a uma imagem em escala de cinza para transformá-la em preta e branco usando o método `cv2.threshold()` da biblioteca OpenCV.

A respeito da função `cv2.threshold()`, o que é correto afirmar?

Selecione uma alternativa

-   No processo de limiarização simples o valor do limiar é escolhido de forma automática pela função da biblioteca, escolhendo sempre o melhor valor para a imagem.
    
-   A função retorna dois resultados, sendo o primeiro deles a imagem limiarizada e o segundo deles o valor do limiar.
    
-   Na limiarização simples precisamos passar como um parâmetro da função o valor do limiar manualmente para que seja feita a transformação da imagem.
    
-   A função sempre retorna uma imagem em preto e branco, onde os pixels com intensidade menor que o limiar se tornam pretos e os pixels com intensidade maior se tornam brancos.