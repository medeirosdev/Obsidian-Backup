[00:00] Agora vamos finalizar nosso código. Lembrando que o que estamos fazendo é um programa de regressão, onde dado que temos as informações como estação do ano, dia da semana, queremos saber quantas bicicletas foram alugadas. Queremos ajudar um negócio.

[00:27] Já carregamos os dados com nosso dataset customizado. Peguei dados da internet, completamente fora do Pytorch. Agora vamos construir a rede, para dado que temos o dataloader com os dados das bicicletas, como vamos prever quantas vão ser alugadas.

[00:50] Eu vou implementar o mesmo MLP das outras redes para vermos que entre classificação e regressão a modificação é mínima. A única diferença é que vamos manter as duas camadas escondidas, lembrando de ativar as camadas com ativações não lineares, e uma camada de saída.

[01:24] O que teremos na ponta da nossa rede é a quantidade de neurônios equivalente à quantidade de variáveis que queremos regredir. Nosso outsize, que antes era o número de classes, agora vai ser o número de variáveis que serão preditas. Queremos prever uma variável, que é quantas bicicletas serão alugadas, então vai ser igual a 1.

[01:56] O softmax já não faz mais sentido, porque o que ele vai fazer é transformar numa distribuição de probabilidades, o que vai fazer com que todas as probabilidades somem um. Só temos um neurônio, não queremos distribuição de probabilidades. Podemos deixar sem ativação ou colocar uma que garanta que vou conseguir prever que estão no range que queremos. São valores como 352, 156, etc. Se eu coloco uma tangente hiperbólica, uma sigmoide, ela vai definir um intervalo possível de valores que está entre 0 e 1. Posso deixar sem ativação e que a rede aprenda intervalos.

[02:48] Não preciso mais linearizar a entrada, porque minha entrada já vai ter uma dimensão só. Posso só fazer o forward normalmente. Não temos mais softmax, então é só a linear lá na ponta, sem ativação.

[03:06] O tamanho da entrada posso pegar do próprio conjunto de treino, ou sei que são 12, então tanto faz. Posso colocar manualmente ou pegar do train set. O train set 0, por exemplo, é um tensor que tem tanto dados, é uma tupla, e o rótulo. Se eu pegar o train set 00 vou ter só o dado. Se eu pego quantos atributos tem o dado, ele vai me dar o valor 12. É isso que quero no meu input size.

[04:12] Posso deixar o hidden size em 128 e o out size igual a 1. Não preciso mudar mais nada e minha rede vai funcionar normalmente.

[04:33] Podemos pegar o mesmo otimizador que definimos anteriormente, o adam, só que a loss vai ter que mudar. Vai ter que ser uma loss de regressão, como L1, e não esqueça de subir na GPU.

[05:10] Sobre fluxo de treinamento e validação. Vamos começar com treinamento que já fizemos e sabemos como é tranquilo de fazer. Depois podemos ver a parte da validação. No treino, temos a etapa do back propagation. A validação é só para testar a qualidade do modelo. Essa etapa do backward não vai existir, mas vamos colar o código de treinamento. Vai estar a mesma coisa que implementamos sem tirar nem por. O código é literalmente o mesmo. Só vou transformar numa função para facilitar.

[06:30] Vou passar de parâmetro para essa função tudo que ela precisa para fazer o treinamento. Vou passar o dataloader e a época. Vou fazer sem o for para que possamos fazer um treino e um teste por época. Farei o loop de épocas fora da função e a cada época vou fazer uma etapa de treino e uma de teste.

[07:24] Primeiro, precisamos mudar o model da rede. Iremos chamar o model.eval no início do código, porque precisamos informar as camadas que não vai mais ter cálculo de gradiente. Isso economiza processamento e memória, porque a rede deixa de salvar informações que são necessárias para o cálculo de gradiente. Isso é importante.

[07:47] Também tem o comando de contexto que vai dizer para o Pytorch que não vai haver cálculo de gradiente. Tudo isso é uma forma de garantir que só vamos usar os recursos necessários para fazer a validação. Primeiro você coloca a rede no modo eval, depois o contexto do torch, e aí você começa a iterar nos batchs. Também tiramos a etapa de backward porque não vai ter mais etapa de otimização nesse processo. Só o forward, cash dos dados na GPU e o forward lá embaixo.

[09:08] Existe um correspondente do net eval para garantir que a rede está no modo de treino. Ele chama net.train. Mesmo sendo padrão da rede, é interessante colocar no modo de treinamento e de avaliação.

[09:53] Só tem mais um detalhe que conversamos no vídeo anterior, que é como medir melhor as métricas do problema. Eu até coloquei uma sugestão de medir a acurácia do modelo, para ver o quanto estamos errando, acertando. No caso da regressão não temos acurácia, porque não estamos fazendo classificação, mas temos medidas de distância que vamos acompanhar.

[10:25] Vamos primeiro rodar para ver como o modelo vai convergir. Vamos criar o loop das épocas. Para cada época em range vamos fazer um treinamento, depois um teste. Iremos alternando entre um e outro.

[11:55] Vai demorar um pouco, mas uma coisa que já conseguimos interpretar é que como colocamos a loss como distância euclidiana, esses valores que tenho já são interpretáveis com a diferença entre valor de aluguel de bicicletas que estou prevendo e o valor real. Estou errando bastante, mas o modelo só começou. Conforme treinarmos ele vai errar cada vez menos.

[13:12] Eu deixei um código perdido para mostrar o resultado. Cheguei até errar por 38 bicicletas. Para quem começou errando 170 é bastante razoável. Eu criei um dataframe dos resultados concatenando minhas predições com o real. Minha predição era de alugar 352 bicicletas conforme as condições do dia. O valor real é 319. Está bem justo. Ele consegue prever pelo menos a escala de aluguéis. Quando são muitas bicicletas, ele dá um valor alto. Quando é menos, ele dá um valor mais baixo.

[14:56] Poderíamos transformar isso em um problema de classificação, poderíamos dizer se você vai alugar poucas ou muitas bicicletas, e o desempenho do modelo ia ser muito bom.

[15:17] Por fim, vou plotar o gráfico. A implementação que eu fiz fiquei salvando as perdas do treino e do teste de cada época. Aquela média que calculamos antes eu salvei aqui. Para fazer o plot, fiz um plot normal com os valores das perdas ao longo das épocas. O mesmo para o teste.

[16:27] É um gráfico de como sua loss se comportou ao longo das épocas. Em azul temos o treino e em laranja o teste. Para esse problema, vemos que o treino tem comportamento mais conservador, quase uma reta, enquanto o teste tem um comportamento mais instável.

[17:36] O fluxo de validação não otimiza enquanto enxerga as amostras de teste, então pelo fato disso acontecer, isso significa que as amostras não estão interferindo no aprendizado. Por isso precisamos garantir que nosso modelo está generalizando bem. À medida que o treino melhora, o teste também vai melhorar. Significa que fizemos um bom trabalho.