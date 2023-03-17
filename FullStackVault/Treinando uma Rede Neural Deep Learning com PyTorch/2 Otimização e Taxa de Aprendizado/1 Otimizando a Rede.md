[00:00] Agora vamos falar um pouco do processo de otimização. Já vimos como calcular a função de perda, a loss, que é uma métrica de quão bem o modelo foi em determinado teste. Como usar a loss para realizar a otimização do modelo?

[00:18] A analogia que se usa normalmente é um homem vendado descendo a montanha. O objetivo é chegar no vale, no ponto mínimo da montanha. Só que ele está vendado e a única coisa que ele pode fazer é dar um passo de cada vez, sentir se ele subiu ou desceu a montanha.

[00:55] Se ele der um passo para a frente, ele vai ver que desceu a montanha. Se ele tem que chegar no vale, é por ali que ele vai. Mas se ele tivesse dado um passo para trás, ele teria visto que está na posição de subida da montanha e mais longe do objetivo dele.

[01:20] Essa é a ideia, você vai dar passos vendados, e tem o objetivo de chegar no ponto mínimo do seu problema. Nosso objetivo é minimizar a função de perda. Pode ser maximizar também, mas vamos tratar como minimizar a distância entre a mão do Patrick e a tampa. Para isso, vamos alterar os pesos dos nossos modelos iterativamente e verificar o impacto de cada alteração na função de perda. Isso é o nosso jovenzinho andando passo a passo vendado.

[02:20] O que temos aqui é uma rede com duas entradas e um perceptron. À medida em que eu for alterando os valores, vou ter valores de loss diferentes, porque por exemplo, se o meu W1, W2 for valendo 40 e 10 respectivamente, tem uma perda de 800%. Se eu alterar o W2 para 70%, agora minha loss vai valer quanto? Basta calcular a diferença entre a loss anterior e a atual para descobrir que eu dei um passo na direção certa.

[03:54] Trazendo para o nosso contexto um passinho na montanha, é uma alteração de pesos. O medidor de altura é uma função da loss em relação aos pesos, e a montanha é a superfície de erro, mas ela é desconhecida, você está vendado, você não enxerga a montanha inteira.

[04:22] Medidor de altura é a função da loss em relação aos pesos. Para calcular se subiu ou desceu a montanha, calculamos a derivada dessa função. E estou trazendo algum matematiquês só porque vai ser importante lá na frente.

[04:40] Se temos a loss em relação ao peso, se eu tinha um peso W qualquer e ele me deu uma loss, e eu tinha outro peso qualquer que me deu outra loss. O que vai me dizer se eu desci ou subi é a derivada entre os dois pontos.

[05:22] Quando falamos de múltiplas dimensões, o vetor de derivadas parciais se chama gradiente. É uma palavra que você vai ver muito se for estudar mais sobre redes neurais. É o indicador se o passo que você deu nos pesos teve impacto positivo ou negativo.

[05:53] Basta entender que gradiente é o indicador se o passo melhorou ou piorou o modelo, e a otimização é o uso dessa informação para escolher a próxima alteração de pesos. A otimização vai ser a escolha dos próximos passos, da próxima alteração de pesos.

[06:30] O fluxo de treinamento é feito da parte forward, em que você opera a entrada na rede, e ele vai dar uma predição que você vai comparar com o rótulo, calculando a métrica de distância. Essa parte já vimos. O que ainda não vimos é o caminho de volta, do backpropagation. É onde vamos calcular o gradiente. Dado que alterei meus pesos, como ficou minha loss? E a atualização de pesos é como vou alterar W1 e W2 para continuar melhorando ou voltar a melhorar o modelo.

[08:16] O algoritmo clássico de otimização é a descida do gradiente. Outra palavra que você vai ouvir bastante. Consiste em subtrair o valor do gradiente, dos pesos W da rede. Se tenho pesos W qualquer, só vou subtrair esse peso pelo meu gradiente, dado que vou ter um multiplicador, extremamente importante.

[08:51] Esse gradiente vai ser um vetor de derivados que vai me dizer se meus pesos atuais em relação a última modificação que eu fiz foi uma melhora ou piora. Se eu subtrair esse valor do gradiente dos pesos atuais, vou seguir a direção contrária do gradiente. São detalhes de matematiquês, mas preciso ponderar esse gradiente por um tamanho de passos.

[09:22] A taxa de aprendizado somos nós que definimos no código. Antes de tudo, quero mostrar visualmente qual o impacto da taxa de aprendizado e por que interferimos nela.

[10:30] Vou colocar um step size quase zero e preste atenção em como os pesos vão ser alterados. Nós nem percebemos, porque é bem pouco. Aumentando a taxa de aprendizado, podemos ver a deslocação, porque aumentei o tamanho do passo, do peso, na hora de um novo teste.

[11:16] Se eu coloco o step size super alto, ele vai ficar louco. Basicamente, esse step size, a taxa de aprendizado, é um valor que definimos e interfere diretamente em como o modelo vai convergir.