Vimos que o procedimento de limiarização simples não é tão interessante para o nosso projeto por tratar-se de um trabalho manual, que consiste em testar diversos valores até encontrar o que retorne o resultado mais satisfatório.

Sendo assim, veremos, agora, o processo de [limiarização adaptativa](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html) ou limite adaptativo. Este tipo de limiarização consiste em utilizar um limiar para cada região da imagem, ao invés de um limiar global, como na limiarização simples. Assim, aplicamos um limiar para cada uma das regiões de vizinhança em torno de cada um dos pixels da figura.

Para este tipo de limiarização, temos dois procedimentos: a adaptativa utilizando a média e adaptativa utilizando a gaussiana. A primeira, calcula uma média da intensidade de cor dos pixels da vizinhança em torno do pixel de referência. Em seguida, esta média é subtraída de uma constante C de nossa escolha. Ou seja, o pixel de referência será comparado com o limiar da vizinhança que o cerca e, através dessa comparação, será transformado para preto a ou branco. A segunda consiste em um cálculo que define um peso maior para os pixels mais próximos do pixel de referência. O valor calculado também será subtraído de uma constante C.

Vamos a um exemplo de limiarização simples e adaptativa!

Observe a imagem a seguir e perceba que se trata da fotografia de um jogo de sudoku. A imagem apresenta uma sombra mais escura no lado esquerdo da fotografia.

![Fotografia de jogo de sudoku composto por uma grade de 9 linhas e 9 colunas. Alguns números estão pré-preenchidos. A foto possui um sombreamento mais escuro em seu lado esquerdo.](https://cdn1.gnarususercontent.com.br/1/1310269/dac7e3d9-16d1-4395-b47a-f73dc57ed38d.png)

Ao passar pelo processo de limiarização simples com um limiar de 127, ela assume a seguinte forma:

![Imagem do jogo de sudoku na cor preto e branco. A imagem possui uma mancha preta, que se inicia no lado esquerdo, e percorre quase metade da figura, impedindo a visualização da área que cobre.](https://cdn1.gnarususercontent.com.br/1/1310269/b0aa9531-8de9-42d2-90bb-bbc7c1e660af.png)

Perceba que a sombra presente na foto assumiu a cor preta, atrapalhando a visualização da imagem. No entanto, isso não ocorre quando adotamos a limiarização adaptativa usando a média, como podemos ver na imagem a seguir:

![Imagem de jogo de sudoku em preto e branco, com pequenos ruídos pretos.](https://cdn1.gnarususercontent.com.br/1/1310269/fb32fc15-f1c0-408e-bf8d-aa12135b9589.png)

Agora, observe a imagem em questão com o processo de limiarização adaptativa utilizando gaussiana:

![Imagem de jogo de sudoku em preto e branco, composto por uma grade de 9 linhas e 9 colunas. Alguns números estão pré-preenchidos.](https://cdn1.gnarususercontent.com.br/1/1310269/b593d86e-082e-4f29-9f9f-7ff1a091d38c.png)

Perceba que, assim como a média, a imagem assume as cores preto e branco, mas quase sem ruídos e manchas.

O exemplo anterior nos mostrou que, em determinadas situações, a limiarização adaptativa nos retorna um resultado mais satisfatório. Veremos, agora, como aplicá-la!

Para aplicar a limiarização adaptativa, utilizaremos a função `cv.adaptiveThreshold` tanto para a média quanto para a gaussiana. O que deve diferenciá-las, no entanto, são os parâmetros `cv.ADAPTIVE_THRESH_MEAN_C` ou `cv.ADAPTIVE_THRESH_GAUSSIAN_C` que correspondem à média e à gaussiana, respectivamente.

Suponhamos que aplicaremos este procedimento na imagem a seguir:

![Tabela em que cada célula apresenta um número e cor correspondente ao valor de sua intensidade na escala de cinza. Os números são, da esquerda para a direita, 201, 140, 30 e 86, na linha 1; 195, 140, 86 e 90, na linha 2; 46, 86, 160 e 190, na linha 3; 246, 96, 15 e 163, na linha 4; e 234, 94, 26 e 37, na linha 5. Os quadros 15, 26, 30, 37 e 46 possuem tons de cinza parecidos, mais próximos do preto. 86, 90, 94 e 96 possuem tons de cinza um pouco escuro, mas não próximos do preto. 140 é um tom de cinza intermediário e os números 160, 163, 190, 195 e 201, tons de cinza claro. Por fim, os números 234 e 246 apresentam variações claras do cinza, aproximando-se da cor branca.](https://cdn1.gnarususercontent.com.br/1/1310269/71c32b53-48a3-4f62-aad3-0f24159f41d4.png)

O primeiro pixel de referência, seria 201, e, no processo de limiriazação adaptativa por média, escolheríamos como sua vizinhança os números 195, 140 e 140, que estão posicionados abaixo, ao lado direito e na diagonal direita de 201. Sendo assim, o limiar médio seria 169.

![Tabela anterior, com os dois primeiros quadros das duas primeiras linhas envolvidos por um retângulo de borda vermelha. O primeiro quadro, com o número 201, possui, ainda, um círculo de borda vermelha.](https://cdn1.gnarususercontent.com.br/1/1310269/99636250-4650-457a-b960-bf1b0acd8c23.jpeg)

Como 201 é maior que o limiar 169, assumirá o pixel 255, de cor branca. Este mesmo processo é feito para cada um dos pixels seguintes. Já no processo de limiarização adaptativa por gaussiana, será dado um peso maior aos pixels mais próximos do pixel de referência.

Agora que melhor compreendemos esse processo, vamos aplicá-lo na imagem da nossa placa!

De volta ao _Colab_, crie uma varivável `lim_adapt`, onde chamaremos a função `cv2.adaptiveThreshold()`. Esta função receberá os seguintes parâmetros:

1.  `imagem` - figura que queremos limiarizar;
2.  `255` - valor para o qual transformaremos o pixel caso este seja maior que o limiar;
3.  `cv2.ADAPTIVE_THRESH_MEAN_C` - tipo de limiarização adaptativa que queremos fazer, neste caso, a média;
4.  `cv2.THRESH_BINARY` - parâmetro responsável por transformar os pixels para preto ou branco;
5.  `11` - distância, em pixels, da região de vizinhança em torno do pixel de referência;
6.  `8` - valor da constante C, do qual será subtraída a média.

Por fim, adicione o comando de visualização `cv2_imshow(lim_adapt)`.

O código ficará assim:

```makefile
lim_adapt = cv2.adaptiveThreshold(imagem, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 8)
cv2_imshow(lim_adapt)
```

Ao executar a célula, observe que nos retorna a placa nos tons de preto e branco. Embora seja possível identificar os caracteres porque os contornos estão bem marcados, eles apresentam várias falhas, como manchas, na cor branca.

![Placa na cor preto e branco. Os caracteres presentes na figura possuem borda preta e não estão totalmente preenchidos, pois possuem diversas manchas brancas.](https://cdn1.gnarususercontent.com.br/1/1310269/8c1c5a8e-ba8e-4a2b-969f-7a981dba7579.png)

Copie o código anterior e cole em uma nova célula, modificando somente o terceiro parâmetro para `cv2.ADAPTIVE_THRESH_GAUSSIAN_C`:

```makefile
lim_adapt = cv2.adaptiveThreshold(imagem, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 8)
cv2_imshow(lim_adapt)
```

Execute esta célula e observe que o resultado da limiarização adaptativa utilizando gaussiana é bem semelhante ao anterior, com a diferença que os caracteres estão preenchidos majoritariamente pela cor branca e possuem ruídos na cor preta:

![Placa na cor preto e branco. Os caracteres presentes na figura possuem borda preta e são preenchidos, principalmente, pela cor branca, embora apresentem diversas manchas pretas.](https://cdn1.gnarususercontent.com.br/1/1310269/9ebe5e9a-01a2-4e6e-bb35-e7b9acb224d5.png)

A seguir, veremos o procedimento de limiarização de Otsu!

# Simples x Adaptativa

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/visao-computacional-deteccao-texto-placas-carro/task/113512/next)

-   [](https://cursos.alura.com.br/suggestions/new/visao-computacional-deteccao-texto-placas-carro/113512/question)

O processo de limiarização adaptativa é melhor aplicado em imagens que nelas mesmas possuem uma diferença de iluminação e sombra. Isso porque o procedimento de limiarização simples aplicada a essas figuras acaba transformando as regiões sombreadas em pixels pretos e regiões iluminadas em pixels brancos, impedindo a identificação das formas presentes na imagem.

Quais das alternativas destacam as diferenças entre os processos de limiarização simples e adaptativa?

Selecione 2 alternativas

-   No processo de limiarização simples o valor do limiar é global, enquanto na limiarização adaptativa são definidos valores diferentes para cada região da imagem.
    
-   O método utilizado para realizar a limiarização simples é o `cv2.threshold`, enquanto para a limiarização adaptativa é o `cv2.adaptiveThreshold`.
    
-   O limiar no processo de limiarização simples é calculado pela média de intensidade dos pixels na vizinhança de cada pixel, enquanto na adaptativa o cálculo tem um peso maior para pixels mais próximos.
    
-   Na limiarização adaptativa a escolha do limiar é feita de forma manual, enquanto na limiarização simples a escolha é feita de forma automática.