As operações bitwise ou bit a bit são muito úteis para extrair qualquer parte da imagem com um formato personalizado, diferente de um retângulo, círculo, ou outras figuras geométricas comuns. Elas consistem em utilizar operações lógicas como AND, OR, NOT e XOR pixel por pixel da imagem. É possível aplicar uma **máscara** para definir a região em que será realizada a operação lógica.

A máscara é uma imagem em que alguns dos valores de intensidade de pixel são zero e outros são diferentes de zero. Sempre que o valor da intensidade do pixel for zero na imagem da máscara, a intensidade do pixel da imagem mascarada resultante será definida para zero. Ou seja, é uma imagem para filtrar somente regiões em que os pixels são diferentes do preto.

As operações lógicas funcionarão segundo a tabela verdade:

As funções da biblioteca OpenCV para realizar o processo de bitwise são:

-   bitwise_and() para operações lógicas AND
-   bitwise_not() para operações lógicas NOT
-   bitwise_or() para operações lógicas OR
-   bitwise_xor() para operações lógicas XOR

Os parâmetros de todas as funções são duas imagens em que serão realizadas a operação lógica pixel a pixel e um parâmetro opcional para utilizar uma máscara, definindo a região em que a operação será realizada.

A operação AND em imagens em preto e branco tomarão o resultado do pixel como branco caso os pixels na mesma posição das duas imagens sejam brancas. O resultado será um pixel branco caso pelo menos um deles seja branco. Se o desejo é aplicar uma máscara em uma única imagem, basta usar a operação AND repetindo a mesma imagem e utilizar a máscara como filtro.

Caso queira aprender mais sobre operações aritméticas em imagens ou sobre cada uma das funções bitwise, consulte a documentação da biblioteca OpenCV:

-   [Operações aritméticas em imagens](https://docs.opencv.org/3.4/d0/d86/tutorial_py_image_arithmetics.html)
-   [Funções bitwise](https://docs.opencv.org/3.4/d2/de8/group__core__array.html#ga60b4d04b251ba5eb1392c34425497e14)