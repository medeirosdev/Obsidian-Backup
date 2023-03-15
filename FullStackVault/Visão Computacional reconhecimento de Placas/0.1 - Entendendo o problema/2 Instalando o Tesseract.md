O intuito do nosso projeto é detectar textos em placas de carros de forma automatizada. Esse processo, em visão computacional, é conhecido como OCR, sigla para _Optical Character Recognition_, ou Reconhecimento Ótico de Caracteres, em português.

Para realizar essa tarefa utilizaremos a ferramenta _Tesseract OCR_, que precisa ser instalada diretamente no computador. Executaremos os códigos no _Google Colab_, que utiliza uma máquina Linux, portanto, nossos comandos corresponderão a este sistema operacional.

Em uma célula, coloque `!`, para acessar o terminal, seguida do comando `sudo apt install tesseract-ocr`, e execute. Este passo instala o _Tesseract_ no computador do _Colab_.

```diff
!sudo apt install tesseract-ocr
```

Para ter acesso ao comando de instalação em outros sistemas operacionais, consulte a [documentação do _Tesseract_](https://tesseract-ocr.github.io/tessdoc/Installation.html).

Agora, vamos instalar a biblioteca _PyTesseract_, do Python, que deve se conectar com o software instalado. Utilizaremos o seguinte comando:

```diff
!pip install pytesseract
```

É possível que, ao executar a instalação do _PyTesseract_, surja uma mensagem de erro responsável por informar que existia uma versão anterior da biblioteca _Pillow_ que precisou ser desinstalada para dar lugar a uma nova versão a fim de poder baixar o _PyTesseract_.

Neste caso, é preciso reiniciar o ambiente de execução para que a versão mais recente seja adotada no _Google Colab_. Para isso, temos duas opções: clicar no botão "RESTART RUNTIME", que aparece abaixo do aviso, ou em Ambiente de execução>Reiniciar ambiente de execução, na barra superior do _Colab_.

> Após reinicar o ambiente, não será necessário refazer os passos anteriores.

Para utilizar a versão em português da ferramenta, precisamos acessar o [GitHub do _Tesseract_](https://github.com/tesseract-ocr/tessdoc) e clicar na opção "tessdata", no readme, que contém o arquivo das línguas disponíveis. Procure "por.traineddata", que corresponde à Língua Portuguesa, e faça o download.

Após baixar o arquivo, você pode fazer seu upload para a sessão do _Colab_ clicando na opção "Fazer upload para o armazenamento da sessão", presente no ícone "Arquivos", na barra lateral. No entanto, sempre que abrir o _Colab_ em diferentes dias, seria necessário refazer este upload manualmente. Como estamos utilizando o Linux, usaremos comandos responsáveis por baixar e salvar esse arquivo de maneira automatizada.

Primeiro, criaremos uma pasta com o comando `!mkdir` e a nomearemos de `tessdata`.

```bash
!mkdir tessdata
```

Após executar o comando anterior, perceba que a pasta foi criada nos arquivos desta sessão.

Em seguida, usaremos um código que fará o download do arquivo diretamente do GitHub e o colocará na pasta que acabamos de criar. Para isso, em uma nova célula, coloque o comando `!wget -O` seguido do caminho da pasta onde o arquivo deve ser salvo `./tessdata/` e o nome que deve ser dado ao arquivo salvo `por.traineddata`. Em seguida, adicione a url do dowload que consta na opção "View raw", dentro do arquivo "por.traineddata", no GitHub `https://github.com/tesseract-ocr/tessdata/blob/main/por.traineddata?raw=true`. O comando ficará assim:

```bash
!wget -O ./tessdata/por.traineddata https://github.com/tesseract-ocr/tessdata/blob/main/por.traineddata?raw=true
```

Execute-o.

O ambiente está pronto para utilizarmos o _Tesseract_, em português, com a linguagem _Python_. A seguir, faremos o upload de uma imagem a fim de detectar os textos presentes nela!

O Tesseract é uma ferramenta de código aberto utilizada para realizar o reconhecimento de textos a partir de imagens. O software conta com a detecção automática da posição dos caracteres e com a interpretação dos caracteres transformando-os em texto.

Para utilizar o Tesseract, é necessário instalá-lo diretamente no computador, sendo suportado nos sistemas operacionais Windows, Linux e MacOS. O tutorial para instalação de ferramenta em cada sistema operacional pode ser encontrado na [documentação](https://tesseract-ocr.github.io/tessdoc/Installation.html).

Diversas línguas estão disponíveis para a detecção dos textos, dentre elas a língua portuguesa. A ferramenta Tesseract pode ser instalada diretamente com a língua portuguesa, mas para um desempenho maior é recomendado ter um arquivo de treinamento da língua separadamente, disponível no [repositório da ferramenta](https://github.com/tesseract-ocr/tessdata).

O Tesseract não conta diretamente com interface gráfica, sendo necessário a utilização em linha de comando, porém existem diversos projetos para sua utilização com interfaces, como o OCRFeeder e Tesseract-GUI, conforme a página do [github](https://github.com/tesseract-ocr/tessdoc/blob/main/User-Projects-%E2%80%93-3rdParty.md).

Outra forma de utilizar a ferramenta é através da API, por meio de linguagens de programação. A biblioteca [pytesseract](https://pypi.org/project/pytesseract/) para a linguagem python é muito útil em projetos, uma vez que outras ferramentas como o OpenCV estão disponíveis para processamento das imagens. Esse processamento de imagens é um passo importante, visto que a detecção dos textos do Tesseract terá uma qualidade muito ruim se as imagens de entrada não forem pré-processadas anteriormente.