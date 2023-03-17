[00:00] Agora vai treinar o nosso modelo de xgboost que é uma biblioteca super utilizada nos dias de hoje, veremos como ela vai ficar no nosso modelo. Para isso, vamos garantir que ela está instalada.

[00:13] Vamos executar um comando do terminal de dentro do Datalab, para fazer isso basta colocar exclamação antes que ele vai entender como um comando que ele vai executar no terminal.

[00:24] Dentro do Python usamos o pip como gerenciador de pacotes, !pip install –upgrade xgboost, vou verificar se tem uma versão instalada e se tiver atualiza, se não tiver instala a última versão que está disponível no pip. No meu caso eu já tinha a última versão atualizada. É sempre bom vou rodar esse comando.

[00:47] Vamos importar é xgboost import XGBC classifier, importamos e como fizemos sklearn, istanciaremos, faremos o fit, predict. Vamos instanciar o xgboost classifier, vamos chamá-lo de xgb.

[01:18] Posso passar alguns parâmetros como pode no sklearn, os parâmetros que ele tem. No sklearn usamos o random, aqui vou passar o seed como 42 e vamos fazer uma coisinha um pouco diferente para ver que se pode mexer nos parâmetros para tentar melhorar nosso modelo.

[01:42] Eu vou mexer no n_estimators que é a quantidade de arrays que esse modelo vai rodar, eu vou colocar para fazer 300, o padrão é 100, quando fizemos o que o nosso modelo do GradienteBoost ele fez com 100 estimadores também.

[02:03] Eu vou fazer com 300, já instanciei meu classificador, agora vou treiná-lo, vamos passar exatamente a mesma base para sklearn, fit, ds, y_train_ds, vamos fazer o fit e vamos ver se essa mesma base usada vai funcionar aqui também no xgboost.

[02:52] Tivemos um problema, o xgboost está falando que os nomes das variáveis não são únicas e ele identificou que dentro da minha base de treino existiam colunas duplicadas. Fizemos todos esses testes no sklearn e ele não acusou isso.

[03:11] Podemos considerar como um ponto a favor xgboost identificar o que pode ser um problema para o meu modelo e já me falou. Para corrigir isso pegamos o X_train_ds e selecionar dentro dele somente as colunas que não são duplicadas.

[03:35] Vamos usar o lock para fazer um filtro dentro das colunas que queremos selecionar, o primeiro parâmetro são as linhas, eu quero trazer todas, eu vou colocar aqui :X_train_ds.coluns, que vai retornar os nomes das colunas e eu vou ver se é duplicado ou não.

[03:56] Com esse comando que vai retornar para cada coluna será duplicada ou não. Esse comando aqui vai trazer verdadeiro para as colunas que são duplicadas, só que eu quero que deixe para mim somente as que não são.

[04:13] Vou colocar na frente esse sinal que vai inverter. Vamos ver se vai dar certo, pode verificar o tamanho que ficou agora o nosso Dataframe, ao olhar o tamanho no shape eu tenho 2.270 eu tinha 2.271, então não foram muitas colunas apenas uma coluna duplicada e consegui remover.

[04:39] Também tem de fazer na base de teste, porque você vai fazer o predict, então vou substituir para teste e vamos deixar o teste também ajustado para o nosso xgboost, vamos rodar de novo.

[04:58] Enquanto ele roda pode pegar o restante do código aqui vai fazer exatamente igual, vamos só mudar os nomes, vamos calcular matriz de confusão, fazer o predict do mesmo jeito e também o classification report.

[05:16] Enquanto está rodando já ajusto os nomes. Vamos colocar um X aqui para identificar o xgboost, vou fazer sobre o teste, mantém a mesma base de teste para que a comparação seja justa.

[05:44] Como colocou mais árvores aqui e ele tende talvez a demorar até um pouco mais, vamos esperar ele rodar. Terminou de rodar, pode fazer o predict, mudou o nome, vamos mudar para xgb e vamos fazer o predict, analisar a matriz de confusão e classification report.

[06:13] Estamos acertando mais do que errando. Então, tem os nossos usuários que fizeram compras, acertamos 106 e erramos 97 que fizeram uma compra e não previ que fariam.

[06:40] Assim, 97 usuários com predição que eles não iam fazer uma compra e eles fizeram, enquanto 106 fizeram uma compra e a gente previu que eles iam fazer uma compra mesmo. O nosso precision foi para 0.68 - um bom ganho, além das outras métricas que subiram o recall e o f1-score.

[07:04] Tivemos uma melhora no xgboost colocando alguns estimadores a mais. Estamos acertando mais de 99% das vezes, acertamos 15.660 usuários que não fizeram compras de 15.000 ao 15710 usuários - que é a soma desses. Nosso modelo já está bom, estamos acertando bastante.

[07:38] O erramos de todos esses usuários foram esses 50 e esses 97, chegamos num modelo talvez bom já que consigamos usar para algum case. Caso vocês queiram praticar outras coisas aconselho a mexer nos estimadores, no Downsample, talvez outras técnicas de machine learning, com uma base de dados de tamanho diferente em cima, talvez criar outras variáveis.

# Para saber mais

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/59716/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/59716/question)

Uma nova alternativa para modelos de gradient boosting foi disponibilizada pelo scikit learn, o “HistGradientBoostingClassifier”. Esse algoritmo é baseado no [LightGBM](https://lightgbm.readthedocs.io/en/latest/) e promete ser muito mais rápido que o Gradient Boosting padrão do scikit learn para grandes datasets (>10.000 amostras).

Para utilizar o HistGradientBoostingClassifier basta acessar a documentação do Scikit learn e seguir os passos: [https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.HistGradientBoostingRegressor.html](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.HistGradientBoostingRegressor.html)![[digital-marketing-gcp-master.zip]]