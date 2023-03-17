E se formos olhar nosso Notebook, veremos que ele começa bem bonitinho, com os importes, sabemos que carregamos o dataset, explorando os dados, exibindo-os, e aí começa a ficar meio estranho, com muitos códigos juntos, uns gráficos no meio, com números no final, então do mesmo modo que fizemos anteriormente, podemos organizar o nosso Notebook dividindo o código e arrumando os títulos de cada uma dessas células.

Vamos começar com a parte em que anotamos a normalização, clicando em uma nova célula de texto e escrevendo "Normalizando as imagens". Clicaremos fora da célula para salvarmos, e podemos deixar na célula logo abaixo apenas o que fazemos com as imagens de treino.

Criaremos outra célula mais embaixo e pegaremos nosso modelo que está sendo compilado, com o histórico, por enquanto. Pegaremos tudo, recortaremos, rodaremos as imagens. Outra opção é clicar nos três pontos no canto superior direito da célula e em "Clear output". Na célula nova, colaremos o que foi recortado: criamos, compilamos e treinamos o modelo, salvando o histórico.

É bastante coisa, e aqui, fica a seu critério: se preferir separar a criação do modelo com a compilação, do treinamento do modelo, é possível. Eu deixarei os três juntos e incluiremos um título para dar mais sentido, que será "Criando, compilando e treinando o modelo".

Agora, está mais organizado. Também fizemos a camada de Dropout, e colocamos um split de validação, então também poderemos adicionar isso no título, que então passará a ser "Criando, compilando, treinando e normalizando o modelo", se você achar que ficou muita coisa, você pode separar em mais células.

Agora que salvamos o modelo, perceba que há um importe, algo que também fica a seu critério. Como estamos utilizando um Notebook e iremos usar este importe específico nesta parte do código, poderíamos até manter assim porque faz sentido. Mas, caso queira, é possível movê-lo para junto dos demais importes, como no caso vou fazer, por questões de organização.

Vamos voltar para baixo e dar um "Clear output" para ficar mais fácil de visualizarmos a exibição dos dados. Continuando, na célula seguinte estamos salvando o modelo e fazendo o load, portanto clicaremos em Text e digitaremos "Salvando e carregando o modelo treinado".

Na célula seguinte estamos plotando o gráfico de acurácia por épocas, clicaremos nos três pontos para limparmos o _output_, e vamos incluir o título "Visualizando as acurácias de treino e validação por época". Seguindo, daremos um "Clear output" na célula seguinte, cujo título será "Visualizando as perdas de treino e validação por época".

O próximo envolve o teste do modelo, então o título da célula será "Testando o modelo e o modelo salvo", e mais abaixo temos a avaliação do modelo, e podemos incluir uma célula de texto com "Avaliando o modelo". Não podemos esquecer de dar um "Clear output" também.

Feito isso, daremos um Cmd + S, ou Ctrl + S, para termos certeza de que salvamos tudo. Podemos ver como está nosso Notebook, com os importes, o carregamento de dataset, exploração dos dados, exibição deles, e nesta parte, se quiser, podemos até deletar a parte que acabamos não usando, mantendo apenas o colorbar.

E então normalizamos as imagens, criamos, compilamos, treinamos e normalizamos o modelo, que depois salvamos e carregamos, visualizamos as acurácias, as perdas, testamos o modelo e o avaliamos. Ficamos com este código bonitinho em nosso Notebook. Para fecharmos este conteúdo com chave de ouro, terminaremos com os slides que mostrarei a vocês.

Começamos a entrar neste mundo do Deep Learning, subcategoria do Machine Learning, e o que gostaria de frisar é que o que geralmente visamos atingir com estes modelos que vamos criando com uma e mais camadas, é sempre ir experimentando, e tentando minimizar a perda e aumentar a acurácia nas nossas camadas de entrada, ocultas e de saída.

Então só para fazermos uma revisão, vimos nossa camada de entrada, usamos o Flatten para pegarmos as imagens de 28 por 28 dimensões, e transformar num array, depois, nas camadas ocultas usamos camadas do tipo Dense, que se conectavam totalmente entre os neurônios e usavam a ReLU, que introduz uma não linearidade no nosso modelo, considerado o tempero do nosso Deep Learning.

Por fim, na camada de saída fazemos a classificação com o softmax, entre camiseta, calça, bota, vestido, por exemplo, e com a nossa acurácia e perda víamos o quanto acertávamos e errávamos no final. Lembrando mais uma vez: quando você for falar sobre o que construiu aqui, a primeira camada é 0, não conta geralmente.

A camada com ReLU seria a primeira camada, a segunda a intermediária, e a 3, a final. Então, com duas camadas intermediárias fazemos uma rede de 3 camadas. Se fizermos da maneira como terminamos no Notebook, a nossa rede neural possui Flatten de entrada, Dense como camada oculta, Dropout como outra camada oculta, e Dense como a camada de saída, isto é, fizemos esta rede neural de 3 camadas. Se você, por exemplo, retirar o Dropout, teríamos 2 camadas.