[00:00] Olá então no primeiro módulo preparei um ambiente para começar a nossa exploração e já temos um BigQuery funcionando, já temos o nosso notebook do Datalab, com uma máquina bem potente por trás.

[00:10] Podemos começar a exploração, como vimos no primeiro curso, o primeiro passo da exploração é conseguir carregar a base de dados que, no primeiro caso estava lá no csv pequeno. Fiz um read csv e consegui trazer as informações para dentro do panda, para dentro do notebook.

[00:27] A nossa base de dados está aqui no BigQuery, dentro de uma tabela e executa uma query e ela simplesmente retorna BigQuery. Como que pegamos o resultado que está aqui no bigquery e leva ele lá para dentro Datalab?

[00:44] Podemos olhar os métodos dos pandas e tem algo bem legal dentro da parte de read, se eu apertar tab tem csv, Excel, json, html e assim por diante. Mas um dos métodos de read do pandas é o gbq que é o googlebigquery. Observe. Dentro do pandas tem método para fazer conexão direta com o carro googlebigquery.

[01:10] então eu consigo executar uma query que vai rodar lá dentro do BigQuery dentro de um código Python, dentro da biblioteca pandas e já retornar como um data frame.

[01:24] Vou criar um df do mesmo jeito que estamos acostumados a fazer, porém, agora no lugar de fazer a leitura de csv, vou selecionar gbd. E vamos ter de passar algumas “coisinhas” aqui para esse método funcionar. A primeira coisa que vou passar vai ser a query que iremos executar e será muito parecida com essa - SELECT * FROM ‘bigquery-public-data.google_analytics_sample.ga_+sessions_*.

[01:50] Não vamos simplesmente fazer um limite, vamos selecionar aqui select * from. Então para não colocar dentro e ficar muito grande, vou criar aqui uma variável e vou chamar de query que ela vai ser um texto simples, onde eu vou passar as informações a query que vai ser executada.

[02:13] Copiei a primeira que fizemos SELECT * FROM ‘bigquery-public-data.google_analytics_sample.ga_+sessions_*, note que o BigQuery é capaz de processar volume de dados muito grandes. Você viu que essa query gastou 5.4 Giga de Bytes processados, mas foi bem rápido.

[02:34] Note que esse dado está sendo processado lá no BigQuery e estou trazendo ele para um Dataframe do pandas, que está aqui no Datalab, está em outra máquina, lugares diferentes. Então por mais que o bigquery vai fazer a query rápida, o resultado dela para ser transferido para o Datalab vai ter de ser baixado via rede.

[02:56] Se você pegar um volume muito grande de dados vai ter um problema de demora para baixar essa informação. Então, para esse curso, para você não ter de esperar muito a informação ser baixada para o Datalab, vou selecionar um período no tempo das sessões que ocorreram lá na loja da Google Merchandising Store.

[03:21] Vamos pegar as seções que ocorreram entre WHERE a coluna date que mostra quando a sessão ocorreu, no meu caso eu vou pegar todas as sessões que ocorreram no mês de janeiro de 2017.

[03:41] Observe que a tabela de sessões do Google Analytics lá no bigquery fica disponível durante um ano, ele sempre mantém 365 dias de sessões. Então, hoje quando estou fazendo esse curso eu tenho disponível o mês de janeiro de 2017. Caso quando você for executar essa query o mês de janeiro de 2017 não esteja mais disponível, porque ele vai sendo excluído, apenas mude o mês aqui para um mês um pouco mais recente - se quiser pegar outubro, só mudar e pronto.

[04:19] Fique à vontade para pegar a base do tamanho que você quiser, selecionar que tipo de informação você quiser, basta mudar um pouco a sintaxe do SQL. Eu vou corrigir no lugar de aspas duplas é uma crase nesse final. Então, temos select* from bigquery public data Google Analytics e eu tenho somente o mês de janeiro.

[04:46] Então esse meu data set, minha tabela, todas as partições, vou executar. Tem uma aspa a mais no final. Note que query é simplesmente uma variável com string dentro, com texto basicamente e eu vou passar esse texto aqui dentro, então query é igual a query.

[05:17] A primeira coisa que eu preciso para executar é qual query que vai ser executada. Além disso, eu preciso passar qual é o projeto que essa query vai rodar. O nosso projeto, qual o projeto do seu usuário que essa query vai ser executada? Não criei o projeto, mas quando você cria a conta já é criado um primeiro projeto automaticamente e chama My First Project.

[05:40] Para descobrir o nome do projeto basta clicar aqui no nome My First Project, vem em Id, Id é essa reflected-mark, eu tenho o nome - ele vai gerar uma aleatório para você.

[05:55] Vou pegar essa Id e colocar dentro de aspas para ser um texto. Outra coisa que tem de passar é o dialeto. O que é isso? O bigquery tem duas sintaxes diferentes de SQL, o SQL Standard e o SQL Legacy. Estamos usando onde estamos chamando data set com essas crases, depois do nome tem ponto, algumas diferenças na sintaxe de como você escreve é o standard, que é um dos SQLs mais conhecidos, bem comum e é o usado nesse curso.

[06:35] Por último, usaremos um expediente bem parecido com o read csv que fizemos no primeiro curso, para identificar a coluna de visitId como string. Se você fez o primeiro curso, você lembra que ele identificou algumas colunas como número inteiro, então tivemos de executar isso de novo.

[06:53] Para não perdermos tempo vamos passar dtype= visit Id com I maiúsculo, dois pontos, objeto, para identificá-lo como uma string. Então, tenho a query que vai ser executada nessa variável, em qual projeto vai rodar, qual a sintaxe que vai executar e já estou falando identifique a coluna visitId como uma string.

[07:25] Eu posso executar isso e quando eu executo aqui, automaticamente essa query vai rodar lá no BigQuery. Faltou um ponto aqui que é basicamente colocar between. Estou falando “a data está entre 1º de Janeiro de 2017 e 31 de janeiro de 2017”. Faltou só colocar o comparador das datas.

[07:58] Vamos executar novamente, vamos tentar rodar de novo. Agora ele está executando, ok. Gerou um job lá dentro do BigQuery e essa query que descrevi dentro está sendo executada lá.

[08:15] Aqui é o tempo que está demorando para retornar os valores dessa query, quando ele terminar de executar vai começar a baixar os resultados para o notebook. Assim, está executando a query, agora já foi processada e ele processou 5.4 GB de dados e já fala quanto custou, notem como é barato, três centavos.

[08:36] Lembra que temos U$D 300,00 e agora ele está nessa fase de retorno de resultados, essa fase vai demorar um pouco, pode demorar até algo em torno de 15 a 20 minutos, vou pausar e volto para vermos os resultados dessa query.

[08:57] A query terminou de rodar, traz alguns resultados, a quantidade de linhas que ele trouxe 64.694. Quanto tempo demorou, quanto custou, algumas informações. Se olharmos o tamanho do data frame agora, ele ficou um Dataframe com 64.694.

[09:21] Eu posso olhar o meu cabeçalho, fizemos uma query dentro do Google Big Query e essa query já retornou como data frame do pandas e isso é muito legal. Não temos de fazer nada, nem trabalhar com nada de esquemas, tabelas, coisas desse tipo, já foi tudo identificado.

[09:42] Se vocês virem que tipo de informação temos, são informações bem parecidas com o que tínhamos no primeiro curso, dicionários de informações dos totais, dicionário de informações sobre tráfico, source, o que vamos ter de novo que vamos trabalhar um pouco nesse curso são as informações de hits que são informações bem ricas e vamos extrair alguns valores lá de dentro.

[10:08] Caso você tenha tido um resultado diferente, mesmo colocando o mesmo filtro que eu fiz aqui, não se assuste lembre-se de que essa base é uma base viva; o Google deixa o espaço de um ano de informação e pode ser que quando você for rodar essa base os dias que eu estou usando aqui já não estejam mais disponíveis.

[10:29] Então sinta-se à vontade para fazer o filtro do jeito que você quiser. Se você deixar um volume de linhas muito grande pode demorar um pouco mais para executar os testes que faremos.

[10:40] E se você deixar muito pequeno talvez a sua base não tenha uma população grande suficiente para treinar os algoritmos que iremos treinar. Teste diferentes tamanhos, teste o resultado em dias diferentes, mas lembre-se de que uma base diferente vai ter resultado de modelos de machine learning diferente.

[11:02] Então, nos próximos passos vamos começar a trabalhar com essa base, até lá.