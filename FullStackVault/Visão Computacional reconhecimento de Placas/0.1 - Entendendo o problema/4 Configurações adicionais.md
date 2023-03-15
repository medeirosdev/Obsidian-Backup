O método `pytesseract.image_to_string()` é utilizado para detectar o texto em imagens. Dependendo de qual língua é usada e a disposição desse texto na imagem, é necessário adicionar alguma configuração extra. Essa configuração auxilia na identificação do texto, fazendo com que menos erros sejam cometidos pela ferramenta.

Com base nisso, quais as alternativas corretas em relação às configurações adicionais do Tesseract?

Selecione 2 alternativas

-   As configurações do Tesseract são obrigatórias, sem elas o método não será executado e não será capaz de identificar os caracteres presentes na imagem.
    
-   Para detectar o texto em línguas diferentes do inglês, basta informar o código da língua no parâmetro `lang`.
    
-   O modo de segmentação de página a ser escolhido varia de imagem para imagem e, por isso, devemos definir manualmente a configuração para obter melhores resultados
    
-   O modo de segmentação de página é muito útil para direcionar o Tesseract a identificar o posicionamento dos caracteres presentes na imagem
- .Agora aplicaremos o processo de detecção de textos em uma placa de veículo!

Primeiramente, abra "Arquivos", na barra lateral esquerda, e faça o upload da imagem "placa_carro1", clicando na opção "Fazer upload para o armazenamento da sessão". Feito isso, copie o caminho da figura.

> Essa imagem foi disponibilizada no link de download das [imagens do curso](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/01/imagens.zip).

Em uma nova célula, crie uma variável `imagem`, que deve receber o código de leitura da figura em questão `cv2.imread('/content/placa_carro1.png')`. Em seguida, ainda nesta célula, passe o comando de visualização `cv2_imshow(imagem)` e execute.

```bash
imagem = cv2.imread('/content/placa_carro1.png')
cv2_imshow(imagem)
```

Este código deve nos retornar a imagem em questão:

![Placa de carro na cor cinza. Em letras garrafais, "PLR3D97", na cor preta. No canto inferior esquerdo, em letras menores, pode-se identificar "BR", também em preto. Há uma barra superior azul escrito "BRASIL" em letras brancas. Ao final desta barra, uma pequena bandeira do Brasil.](https://cdn1.gnarususercontent.com.br/1/1310269/3c93a429-864d-4e93-a014-92a148c7e583.png)

Esta imagem possui 3 canais de cor: "B", de _blue_ (azul), "G", de _green_ (verde) e "R" de _red_ (vermelho). Isso porque a biblioteca _OpenCV_ realiza a leitura da imagem com estes 3 canais de cor, respectivamente, portanto, precisamos transformar esta imagem colorida para uma escala de cinza. Essa transformação é necessária para que o _Tesseract_ tenha um melhor desempenho, já que, com apenas um canal de cor (cinza) o processamento tende a ser otimizado.

Para fazer essa modificação, usaremos a função `cvtColor()`. Então, em uma nova célula, crie uma variável `imagem` que deve receber a função `cv2.cvtColor()` que, por sua vez, recebe os seguintes parâmetros: `imagem`, que corresponde a variável anteriormente criada, onde passamos o caminho da nossa figura, e `cv2.COLOR_BGR2GRAY`, que diz respeito à transformação que queremos fazer, ou seja dos canais de cor "BGR" (azul, verde e vermelho) para o canal de cor "GRAY" (cinza).

```ini
imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
```

Chame, também, o comando de visualização `cv2_imshow(imagem)`. A imagem será retornada em escalas de cinza.

```makefile
imagem = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)
cv2_imshow(imagem)
```

Agora podemos aplicar o _Tesseract_!

Primeiramente, vamos fazer as configurações da língua criando uma variável `config_tesseract`, que deve receber o nome do arquivo referente à Língua Portuguesa `'--tessdata-dir` e a pasta onde está localizado `tessdata`.

```ini
config_tesseract = '--tessdata-dir tessdata
```

Ainda nesta célula, adicionaremos o comando responsável por transformar esta imagem em uma string, ou seja, um texto. Para isso, criaremos uma variável `texto` que deve receber a função `pytesseract.image_to_string()`. Essa função deve receber os parâmetros `imagem`, variável que armazena a figura em questão, `lang = 'por'`, referente à língua que deve ser detectada, e `config = config_tesseract`, que informa que devem ser usadas as configurações passadas na variável `config_tesseract`.

```ini
config_tesseract = '--tessdata-dir tessdata
texto = pytesseract.image_to_string(imagem, lang = 'por', config = config_tesseract)
```

Por fim, adicione o comando de visualização `print(texto)`.

```ini
config_tesseract = '--tessdata-dir tessdata
texto = pytesseract.image_to_string(imagem, lang = 'por', config = config_tesseract)
print(texto)
```

Ao executar esta célula, perceba que ele não conseguiu detectar nenhum caractere na imagem. Essa ocorrência nos leva à conclusão que, em projetos como este, precisamos considerar, por exemplo, o posicionamento da câmera que deve registrar essas placas. Isso é importante porque a depender da posição e resolução da imagem, o _Tesseract_ pode encontrar dificuldades de leitura, assim como encontrou para decodificar o texto desta imagem, embora trate-se de uma figura em ângulo frontal com relação à placa, permitindo que nós, humanos, possamos compreender e ler perfeitamente seu conteúdo.

Sendo assim, para que o _Tesseract_ consiga realizar a leitura de uma imagem, precisaremos, antes, tratá-la. A seguir, veremos o primeiro passo deste tratamento: a **limiarização**!