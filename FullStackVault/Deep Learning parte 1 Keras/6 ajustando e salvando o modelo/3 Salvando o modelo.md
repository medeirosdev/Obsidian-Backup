Vimos em nossos gráficos que no de perda a de avaliação está muito alta, e a de treino está abaixando, então nosso modelo pode estar um pouco viciado quando chega perto da décima rodada, ou época. Então podemos manter onde está mais estável, por exemplo, entre a quarta e a sexta época.

Além disso, se observarmos o nosso gráfico de acurácia, a mesma coisa, a de treino está subindo, enquanto a de avaliação está subindo, mas de forma mais instável. Do mesmo modo, se mantivermos a quantidade de épocas num ponto mais intermediário, talvez seja melhor para o nosso modelo.

Lendo estes gráficos, iremos alterar as nossas épocas, de 10 para 5. Vamos rodar mais uma vez para verificar o resultado. Precisaremos dar um _reload_ no Notebook, importar o TensorFlow, carregar dataset. Rodaremos o modelo, geraremos os gráficos para vermos se houve melhora.

Pelo que vemos, a acurácia de treino ainda está maior que a de avaliação. Também, vamos executar este de perda, a parte boa é que esta perda da avaliação caiu um pouco mas depois ela subiu novamente lá pelo final do nosso ciclo, das nossas épocas. Então, o treino ainda está perdendo menos do que a avaliação.

Se trocarmos as épocas ao olharmos o gráfico não adiantou tanto, que outra técnica podemos usar?

Podemos alterar as nossas camadas do modelo, então para resolvermos este problema, lembra dos 256 neurônios ou unidades que tínhamos na camada intermediária? Para elas não ficarem tão viciadas, podemos indicar que elas adormecessem um pouco, e a cada dez unidades queremos que duas fiquem dormentes e não captem tanta informação.

Podemos fazer isto com a nossa rede e ver se isto traz alguma diferença para o nosso modelo. Após a vírgula, então, daremos um Enter e adicionaremos mais uma camada. O nome do que tira algumas unidades como se elas estivessem dormentes é dropout, então adicionamos esta camada. Abriremos e fecharemos parênteses, e dentro escolheremos o quanto queremos deixar adormecido.

Uma boa prática recomendada é 0.2, isto é, 20%, mais ou menos o mesmo que separamos para nosso validation. Então podemos acrescentar uma vírgula e rodar o modelo novamente para verificar quais são os novos resultados. Feito isso, podemos plotar os gráficos novamente para verificar quais as diferenças causadas pelo dropout.

Já está muito melhor, certo? Agora nossa acurácia de avaliação está maior do que a de treino, e se observarmos a nossa perda, nossa perda de avaliação está menor do que a de treino. Então, com uma linha em nosso modelo já conseguimos melhorar em muito o que está acontecendo. E esta nova camada, que deixou 20% das unidades dormentes também é um tipo de normalização, assim como fizemos com as imagens de treino.

Agora que nosso modelo está bem divertido, e parece estar funcionando bem, podemos salvá-lo. Para isso, após rodarmos ele criaremos uma nova célula e usaremos uma função do próprio Keras, save. Entre parênteses, passaremos o nome que queremos que o arquivo tenha. A extensão deste arquivo é comum ao lidarmos com muitos dados, e como lidamos com um dataset não muito grande, mas temos muitas variáveis e coisas acontecendo por baixo dos panos em nosso modelo, vamos usar este formato, que é h5.

Se executarmos, salvaremos o modelo. Agora podemos fazer o load do nosso modelo, e comparar com o que tínhamos antes para ver se deu certo. Na linha de baixo, declararemos uma variável chamada modelo_salvo, e faremos o carregamento do nosso modelo com load_model passando o nome modelo.h5.

Vamos executar e ver o que acontece?

Recebemos uma mensagem de erro indicando que load_model não está definido, e precisaremos importar esta função do Keras. O importe será do TensorFlow, de dentro dos modelos do Keras. Vamos rodar novamente e ver o que acontece. Nosso código está funcionando corretamente, e temos nosso modelo_salvo.

Agora, para garantirmos que isso deu certo, podemos ir até onde fazíamos nosso teste e incluir um predict com nosso modelo já salvo. Declararemos testes_modelo_salvo, iremos a mkodelo_salvo.predict passando imagens_teste. Embaixo, printaremos o resultado do teste, assim como o número da imagem de teste.

Vamos executar a célula, e podemos ver que o resultado teste dá 2, número da imagem de teste também, o resultado do teste modelo salvo também dá 2, assim como o número da imagem de teste. Está tudo certo, otimizamos e salvamos o nosso modelo.