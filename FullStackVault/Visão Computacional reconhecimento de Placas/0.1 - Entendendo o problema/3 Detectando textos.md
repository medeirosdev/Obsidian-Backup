Agora que instalamos a ferramenta _Tesseract_, veremos como utilizá-la para detectar textos em uma imagem!

Iniciaremos importando a biblioteca anteriormente instalada, _PyTesseract_, e a biblioteca _OpenCV_, utilizada para tratar e trabalhar com imagens.

Em uma célula, executaremos os comandos a seguir:

```cpp
import cv2
import pytesseract
```

Agora, veremos as versões dessas bibliotecas que estão sendo utilizadas. Assim, se gerar algum erro, você identificará se está usando a mesma versão que consta na máquina do instrutor. Para isso, execute o comando a seguir que deve retornar a versão 4.6.0 do _OpenCV_.

```markdown
cv2.__version__
```

Em seguida, verifique a versão do _PyTesseract_, que deve ser 0.3.9.

```markdown
pytesseract.__version__
```

Agora faremos a leitura de uma imagem do trecho de um livro. Para isso, vá em "Arquivos", na barra lateral, e em "Fazer upload para o armazenamento da sessão". Em seguida, selecione a imagem chamada "trecho_livro.png" e aguarde o carregamento.

> As imagens que serão utilizadas no curso foram disponibilizadas na etapa "Preparando o ambiente". Mas você também pode baixá-las clicando [neste link](https://caelum-online-public.s3.amazonaws.com/2666-visao-computacional/01/imagens.zip).

Em uma nova célula, criaremos a variável `imagem`, onde vamos chamar a biblioteca _OpenCV_ `cv2` e sua função `.imread()` para realizar a leitura deste arquivo. Esta função recebe como parâmetro o caminho da imagem entre aspas. Para ter acesso ao caminho, vá em "Arquivos", na barra lateral esquerda, clique com o lado direito do mouse sobre "trecho_livro.png" e em "Copiar caminho".

```ini
imagem = cv2.imread('/content/trecho_livro.png')
```

Execute esta célula e, em uma nova, solicite a visualização de `imagem` com a função do _OpenCV_ `imshow()`.

```scss
cv2.imshow(imagem)
```

Se você está usando o _Colab_, provavelmente a execução de visualização gerou um erro. Este erro é muito comum e ocorre porque a função utilizada gera uma quebra nas sessões do _Jupyter_. Utilizaremos, então, a sugestão dada por esse erro: importar a função `cv2_imshow`, do _Google Colab_. Para isso, execute o código a seguir:

```javascript
from google.colab.patches import cv2_imshow
```

Agora solicite novamente a visualização fazendo uso da função importada:

```scss
cv2_imshow(imagem)
```

Ao executar a célula, observe que nos é retornado a imagem do trecho do livro digitalizada.

> "- Um mal é um mal, Stregobor - retrucou seriamente o bruxo, pondo-se de pé. - Menor, maior, médio, tanto faz... As proporções são convencionadas e as fronteiras, imprecisas. Não sou um santo eremita e não pratiquei apenas o bem ao longo de minha vida. Mas, se me couber escolher entre dois males, prefiro abster-me por completo da escolha. Está na hora de ir embora. Ver-nos-emos amanhã."

Veremos, agora, se o _PyTesseract_ consegue realizar a leitura do texto presente na imagem.

Em uma nova célula, criaremos uma variável `texto` onde chamaremos a função `pytesseract.image_to_string()`, que receberá a variável `imagem` como parâmetro. Esta função será responsável por transformar a imagem em uma string (dado do tipo texto).

```ini
texto = pytesseract.image_to_string(imagem)
```

Ainda nesta célula, insira o comando de visualização `print(texto)` para que a variável `texto` seja impressa na tela.

```bash
texto = pytesseract.image_to_string(imagem)
print(texto)
```

Ao executar este comando, ele nos retornará o texto contido na imagem:

> "- Um mal é um mal, Stregobor - retrucou seriamente 0 bryxo, pondo-se de pé. - Menor, maior, médio, tanto faz... As porgdes sao convencionadas e as fronteiras, imprecisas. um santo eremita e nao pratiquei apenas 0 bem ao longo de minha vida. Mas, se me couber escolher entre dois males, prefiro abster-me por completo da escolha. Esta na hora de ir embora. Ver-nos-emos amanha. S pro- 40 SOU"

Perceba que ele conseguiu identificar a maioria dos caracteres de forma correta, embora tenha trocado o artigo "o" pelo número 0, a letra "u" por "y" e não tenha colocado alguns sinais de acentuação. Observe, ainda, que as duas últimas linhas não correspondem ao texto, o que também sugere uma falha na leitura. Como podemos melhorá-la?

Para aprimorar essa decodificação, utilizaremos o arquivo da Língua Portuguesa baixado anteriormente, informando que queremos utilizar essa língua. Podemos, ainda, adotar uma segmentação de páginas que ajude a melhor identificar esse texto.

Sendo assim, em uma nova célula, execute o seguinte comando:

```css
!tesseract --help-psm
```

Ele nos retorna as formas de segmentação de página disponíveis no _Tesseract_. A forma de número 6, "Assume a single uniform block of text", melhor atende às nossas expectativas, porque assume que a imagem se trata de um bloco uniforme de texto. Nós a utilizaremos no código seguinte.

Criaremos uma variável de configuração `config_tesseract`, que deve receber o nome do arquivo referente à Língua Portuguesa `'--tessdata-dir` e a pasta onde está localizado `tessdata`. Em seguida, colocaremos a configuração de segmentação de página `--psm-6'`.

```ini
config_tesseract = '--tessdata-dir tessdata --psm-6'
```

Execute esta célula para salvar essa configuração no _Tesseract_ e, em uma nova, tentaremos ler novamente o texto. Para isso utilizaremos a mesma função `texto = pytesseract.image_to_string(imagem)`, mas, além do parâmetro `imagem`, passaremos, também, os argumentos `lang = 'por'`, referente à língua que deve ser detectada, e `config = config_tesseract`, que informa que devem ser usadas as configurações passadas na variável `config_tesseract`.

```ini
texto = pytesseract.image_to_string(imagem, lang = 'por', config = config_tesseract)
```

Adicione, ainda, o comando de visualização `print(texto)`.

```lua
texto = pytesseract.image_to_string(imagem, lang = 'por', config = config_tesseract)
print(texto)
```

Ao executar esta célula, perceba que nos retornará o seguinte texto:

> "- Um mal é um mal, Stregobor - retrucou seriamente o bryxo, pondo-se de pé. - Menor, maior, médio, tanto faz... As proporções são convencionadas e as fronteiras, imprecisas. Não sou um santo eremita e não pratiquei apenas o bem ao longo de minha vida. Mas, se me couber escolher entre dois males, prefiro abster-me por completo da escolha. Está na hora de ir embora. ; Ver-nos-emos amanhã."

Perceba que a letra "o", antes reconhecida como "0", agora foi corretamente identificada, assim como os sinais de acentuação gráfica. Note, também, que não há mais os caracteres " S pro- 40 SOU" contidos no fim do bloco e que nada correspondiam com o texto. Os únicos erros que permanecem são a troca do "u" pelo "y", na palavra "bruxo", e um ponto e vírgula (;), erroneamente colocado após a frase "Está na hora de ir embora. ;". Sendo assim, podemos considerar que o _Tesseract_ conseguiu realizar uma boa leitura do texto contido na imagem!

A seguir, aplicaremos esse mesmo processo na imagem de uma placa de veículo. Vamos lá?