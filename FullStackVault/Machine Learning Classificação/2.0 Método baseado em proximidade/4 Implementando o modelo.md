[00:00] Vamos relembrar alguns pontos estudados até o momento. Primeiro temos o objetivo de classificar os clientes em potenciais candidatos a deixar ou não a Alura Voz. Depois aprendemos melhor o que é a classificação, como ela funciona, vimos também o primeiro modelo a ser aplicado nos nossos dados e toda a sua matemática por trás.

[00:22] Agora, finalmente, vamos implementá-lo nos nossos dados. Para começar vamos chamar a biblioteca SKLearn e dentro dessa biblioteca o pacote _model selection_ para que possamos dividir em treino e teste o nosso conjunto de dados.

[00:43] Você deve estar se perguntando para que dividir os nossos dados novamente. Primeiro, nós dividimos em X e Y, os dados de entrada e os dados de saída, que queremos utilizar para classificar os nossos clientes.

[00:57] Agora, nós vamos dividir todo o conjunto em treino e teste, isso significa que vamos primeiro a partir desse conjunto treinar a máquina, aquele aprendizado, treinar o algoritmo para que ele possa aprender a função KNN para depois com o novo conjunto de informações, o teste, poder treinar, testar se realmente o treino valeu a pena, se funcionou para que essa classificação não seja errônea, para que o aprendizado não seja afetado.

[01:34] Se simplesmente pegássemos os nossos dados e implementássemos o modelo sem dividir em treino e teste. `from sklearn.model_selection import train_test_split`, aqui está. Agora vamos colocar as variáveis para armazenar as nossas divisões em treino e teste.

[02:01] Primeiro: "x_treino, x_teste, y_treino, y_teste = train_test_split(X_normalizado, y, test_size=0.3, random_state=123)", temos quatro variáveis para receber as quatro informações a serem divididas. Chamamos a função `train_test_split` abre e fecha parênteses, chamamos o nosso conjunto e definimos o tamanho do nosso conjunto de teste.

[02:35] Por padrão em toda literatura e área de dados é 25%, até aqui a nossa função o padrão é 25%, mas é muito comum utilizar 30 também, o que é algo muito bom. Quanto maior o conjunto de teste, melhor fica a validação desses dados, o aprendizado desse modelo.

[02:59] Outra variável muito importante de definirmos é o `radom_state`, que é o estado de aleatoriedade. Isso significa que vamos definir um valor para que essa divisão aleatória possa ser reproduzida por você. Garantir a reprodutibilidade dos nossos resultados, porque se não determinássemos esse estado aleatório, toda vez que rodássemos essa célula, eu rodar aqui e você rodar aí, os nossos conjuntos seriam diferentes, porque essa divisão é aleatória.

[03:38] Vamos definir um estado para que o meu resultado seja igual ao seu. Conjunto definido, o `random_state=123` você pode definir qualquer valor, não tem um valor definido, mas aqui eu defini como 123.

[03:56] Agora, dados divididos, vamos partir para o treino e o teste do nosso modelo. Vamos começar com o treino, vamos chamar o nosso modelo KNN, que ele vem da biblioteca SKLearn, `from sklearn.neighbors import KNeighborsClassifier`, _import_ porque vamos importar as funções do modelo SKLearn que é o `KNeighborsClassifier`.

[04:27] Nós rodamos e pronto, todas as funções desse modelo estão aqui para utilizarmos no _notebook_. Agora vamos instanciar o modelo. Assim como instanciamos a função de normalização precisamos instanciar essa função do KNN, vamos chamar uma variável chamada `knn = KNeighborsClassifier(metric='euclidean')`.

[04:56] Definimos algumas informações, primeiro o nosso número de K. Por padrão na função são "K = 5", 5 vizinhos mais próximos que irão definir e classificar a nossa variável. Vou deixar assim, é um valor interessante para começarmos. Só que a métrica precisa ser definida e nós estamos trabalhando com a distância Euclidiana, vamos definir a métrica de distância como `metric = 'euclidian'`.

[05:29] Vamos rodar e aqui está o nosso modelo instanciado pronto para ser aplicado nos dados. Para fazer isso vamos treinar o modelo aplicando os conjuntos de treino `X_treino` e `Y_treino`, `knn.fit(X_treino, Y_treino)`.

[05:52] Lembra o nosso par XY? Aqui funciona da mesma forma, ele está pegando o modelo e treinando com as nossas informações de entrada e as informações de saída. Vamos rodar e perfeito, funcionou.

[06:08] Agora, vamos testar de fato esse modelo, vamos colocar em teste, ver se o aprendizado não está afetado, se está funcionando tudo direito. Vamos lá. Vamos criar uma variável para armazenar os resultados preditos, chamamos: `predito_knn = knn.predict(X_teste)`. E funcionou, o nosso modelo está testado.

[06:48] Vamos dar uma olhada melhor nesses resultados. Perfeito, aqui está o nosso resultado predito. Agora esse modelo está bom ou ruim, calma que vamos isso mais para frente, quais outras funções desconhecidas podem aplicar nesses dados.