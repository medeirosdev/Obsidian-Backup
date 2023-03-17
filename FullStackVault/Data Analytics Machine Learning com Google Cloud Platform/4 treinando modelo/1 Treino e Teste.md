[00:00] Chegamos na etapa de treinar o modelo, já temos nossa base preparada, fizemos vários tipos de transformações com a coluna de hits, com as colunas que mostraram quais informações os usuários na última sessão. Agora tem uma base grande, apenas de colunas temos 2.271 colunas.

[00:21] Muito relacionado que várias das colunas são os produtos que os usuários tiveram iteração nessa sessão. Temos nossa base dividida em x e y, podemos dividir em treino e teste, para isso vamos usar como no primeiro curso, a biblioteca do sklearning que faz essa divisão automaticamente.

[00:44] Vamos importar from sklearn.model_selection import train_test_split, aqui vou fazer X_train, X_test, y_train, y_test = train_test_split() aqui passo o meu X, o meu Y, coloco dentro também o tamanho da base de teste, vou colocar 0.3 que vai ficar 30% para teste e 70% para treino.

[01:44] Vou passar o random state para que ele faça a divisão sempre igual toda vez que rodar isso, vou setar a minha semente em 42, rodando agora podemos conferir como ficou, x_train, dentro de treino de 37.128 linhas e 2.271 colunas.

[02:17] Se der uma olhada, tem as colunas que preparamos com as informações por usuario, o y ele foi transformado dividido em partes, o y_train é uma série com valores que o usuario gastou naquela sessão, pode olhar o read e no próximo vídeo treinaremos o primeiro modelo que será uma regressão logística.