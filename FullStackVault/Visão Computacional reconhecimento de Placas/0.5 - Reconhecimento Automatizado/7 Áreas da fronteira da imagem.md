Há uma expressão muito famosa na ciência da computação que é a seguinte: "Garbage in, garbage out", em português: Entra lixo, sai lixo. Em um projeto de detecção de placas, é muito importante o alinhamento e posicionamento da câmera ou dispositivo para gerar as imagens para facilitar o processo de identificação dos caracteres e garantir o bom funcionamento do código. O projeto precisa ser pensado como um todo e caso não tenha imagens em boa resolução ou posicionamento ruim, o processo de identificação do texto também ficará ruim.

Em um projeto bem planejado, a localização da placa nunca estará em regiões de fronteira da imagem, tocando as bordas, já que poderia cortar algum caractere ou informação importante da placa. Com isso em mente, no momento de localizar a região da placa, pode ser aplicado um procedimento para remover as áreas na borda da imagem que não serão relevantes para encontrar a posição da placa. Marque a alternativa que corresponde ao método para realizar esse procedimento de remoção de bordas:

Selecione uma alternativa

-   Utilizando o método `clear_border()` da biblioteca scikit-image.
    
-   Aplicando o procedimento de erosão para remover ruídos brancos.
    
-   Utilizando o método `clear_border()` da biblioteca OpenCV.
    
-   Utilizando uma máscara com a função `bitwise_and`.![[Aula5.ipynb]]