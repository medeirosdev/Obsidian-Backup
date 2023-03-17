Rodamos o nosso modelo, e vimos que a nossa perda está em 13.10. Esse número não é bom; vamos parar para pensar: toda vez que perdemos algo, queremos perder mais ou menos? Geralmente queremos perder o mínimo possível, evitando-o a todo e qualquer custo, pois quanto mais tivermos de informações, melhor, não é?

Então, nosso intuito é fazer com que esta perda vá de 13 para o mais próximo de 0, queremos diminuir sempre esta perda. Para fazermos isso, olhem tudo que já fizemos, para compilar, fazer o fit do modelo. Como diminuímos esta perda? Podemos começar com a nossa camada de entrada; vamos lembrar o que está acontecendo aqui: pegamos as nossas imagens, que já vimos na exibição lá em cima, que têm o tamanho de 28 x 28, que é o tamanho do nosso array.

Já estamos jogando-as diretamente nesta primeira camada, com o input_shape. Será que esta é a melhor estratégia? Porque nossa imagem não é feita somente do tamanho dela, vimos que há todos os pixels contendo bastante informações. Então, aproveitaremos que fizemos esta divisão na exibição dos dados e criaremos mais uma coisa para visualizarmos aqui.

Daremos um Enter, e veremos o que mais temos de informação nestes pixels, por exemplo uma informação de cor. Que cores têm nossas imagens? Ao observarmos, parece que elas são em preto e branco, certo? Para verificarmos, copiaremos a linha com imshow, porém desta vez passaremos imagens_treino. Além disso, não queremos apenas ver a imagem, e sim a gradação de cor que ela possui.

Então faremos um gráfico que chama o gráfico de barras de cores, em inglês, colorbar. Feito isso, executaremos o código com Ctrl + Enter, e obteremos uma mensagem de erro dizendo que plt não está definido. O que acontece é que toda vez que vamos executar nosso Notebook, precisamos rodar as instruções anteriores, porque ele recarrega constantemente e às vezes perde a referência.

Como dividimos nosso código, não estamos importando o pacote todas as vezes. Como ele perdeu a referência do plt, iremos aos nossos importes e rodaremos a célula novamente. Já que isso aconteceu, é bem capaz que ele tenha perdido a referência do dataset, então rodaremos mais uma vez. Tudo foi baixado corretamente.

Voltaremos à exibição e rodaremos novamente, agora tivemos um problema pois estamos executando o código anterior. Para resolvermos isso, comentaremos essas primeiras linhas com três acentos agudos antes e depois do trecho do código. Salvaremos e executaremos mais uma vez. Agora sim, temos um Colorbar bem bonitinho da nossa imagem.

Reparem na gradação de cor dela, a informação de cor que temos nos pixels, que vai de 0 a pouco mais de 250. E são tons de cinza, não só preto e branco, como estava parecendo. Temos, então de 0 a mais de 250 valores em nossa imagem. Quando a jogamos em nossa rede, estamos jogando algo que tem 28 por 28 posições, sendo que cada um dos valores que preenchem essa matriz de 28 linhas por 28 colunas está variando de 0 a 255.

É uma variação bem grande, assim como nossa perda. Sendo assim, poderíamos tentar reduzir este número; se variar de 0 a 1, melhor, não é? Se eu te disser para me dizer um número de 0 a 200, você vai pensar por mais tempo do que se se pedir um número de 0 a 1. Mas de que forma faremos, se deixarmos 0 e 1, para capturar essa gradação, essa diferença de cores? Porque ela é importante para identificarmos as imagens.

Então, o que podemos fazer é deixar um espaço para este intervalo entre 0 e 1, capturar tudo o que vem no meio. Para isso, basta não utilizarmos inteiros, e sim o ponto flutuante, que incluirá o 0, 0.1, 0.2, 0.3, e assim por diante. Para isso, na primeira linha do nosso modelo daremos um Enter, e o que faremos é uma transformação nas nossas imagens de treino e podemos pegar estes 255 pixels e fazer uma divisão.

Agora, tudo que for 255, ao dividirmos por 255, vira 1. No entanto, são 255 pontos flutuantes, então temos algumas opções. Usamos 255.0 ou fazemos um Type Casting e colocamos float passando 255. Faça como você se sentir mais confortável e achar melhor. O legal é vermos se isso fará alguma diferença em nosso modelo.

Não basta só dividir, certo, precisamos pegar o vetor, nosso array de imagens de treino e atribuir a ele mesmo. Com isso estamos dividindo isso pelo float de 255. Vamos rodar mais uma vez e ver o que acontece com a nossa perda. Daremos um Cmd + Enter, e acompanharemos a perda, que antes estava em 13.10, e agora em 0.48.

Então, fazer este processo de diminuir esta abrangência numérica que a nossa rede tem que processar ajuda muito na quantidade de informações que perdemos. Mantivemos os tons da imagem, todas as gradações entre os pixels, mas diminuímos todo esse tamanho que ela precisava processar, e vimos uma redução significativa na perda.

E esse processo que fizemos, de dividir as imagens de treino por 255 é chamado de Normalização. Vamos incluir um comentário para nos lembrarmos disso. Dentro do Deep Learning, tem pessoas que gostam muito dessa normalização, e acham que ela reduz significativamente a nossa perda, e como foi com as camadas que criamos, outras acham que ela não faz tanta diferença dependendo do modelo em uso, sendo às vezes desnecessária.

As opiniões divergem, e tem muito a ver com a experimentação. Poderíamos ter normalizado as imagens e não ter feito uma diferença significativa em nosso modelo. Então só se sabe disso, mesmo, na prática. Monte a sua rede, normalize, não normalize, compare e veja que resultados você obtém. Nesse vídeo focamos na nossa primeira camada, vamos ver o que podemos fazer ainda mais com nosso modelo!