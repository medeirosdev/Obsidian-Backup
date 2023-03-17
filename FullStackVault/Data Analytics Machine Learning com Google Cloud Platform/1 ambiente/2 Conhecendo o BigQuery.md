[00:00] Olá, estamos com a nossa conta configurada, com os créditos ativados, vamos acessar o BigQuery. Para acessar alguma ferramenta dentro do Google Cloud você pode procurar ferramenta nessa barra lateral e o BigQuery está dentro de Big Data, pode clicar aqui ou nessa barra de pesquisa.

[00:17] Então, posso pesquisar aqui BigQuery e a primeira opção que aparece, tem algumas outras opções que ele está relacionado, vou clicar nessa primeira opção. Essa é a “cara” do BigQuery ferramenta muito simples, como disse no começo do curso é só uma ferramenta de DW – DataWare House, ou então uma ferramenta de bancos de dados analíticos diferente de bancos de dados operacionais.

[00:45] Vai servir muito bem para carregar grandes volumes de dados dentro e conseguir fazer querys, pesquisas e alguns cruzamentos; fazer alguns tipos de processamento nessas informações, mesmo que o volume de dados seja muito grande e no processamento muito poderoso.

[01:05] O BigQuery é capaz de processar peta bytes de dados, tem custo bem baixo e você não tem de se preocupar com nada de infraestrutura. Um custo altamente abstrato para quem está utilizando e funciona muito bem para as necessidades de ciência de dados quando você simplesmente quer ter a sua base de dados disponível, quer rodar querys diferentes, quer fazer todo esse trabalho sem ter de se preocupar em como o banco de dados está funcionando.

[01:32] Colocar o banco de dados de pé e assim por diante. Esse é o aspecto dele, é bem simples, se você clicar aqui, por exemplo, existem alguns conjuntos de dados públicos que estão disponíveis, clico neles e vocês podem ver uma quantidade enorme de bancos de dados públicos que estão dentro do BigQuery.

[01:52] Você pode acessar, fazer querys, começar a fazer exploração, fazer modelo em cima dessas informações, tem muita coisa legal. A base que vamos usar dentro desse curso é a base do Google Analytics da Google Mershandising Store.

[02:08] E ela está disponível dentro de um data set que vou acessar via querys, caso você não tenha muita experiência com SQL, vamos usá-lo poucas vezes nesse curso. Não vai ser nada muito complexo, apenas select bem simples, mas aconselho você caso tenha dúvidas, procure aqui dentro da Alura outros cursos de SQL para se aprofundar, que é muito legal saber para este tipo de trabalho de exploração.

[02:36] Como SQL é bem simples, acredito que a grande maioria vai conseguir entender tudo que estou fazendo. Porque, por exemplo, para dar uma olhada na tabela que vamos usar eu vou fazer select * - que significa todas as colunas dessa tabela que eu vou chamar - e vou passar aqui o nome da tabela que estou acessando.

[03:00] Em qual data set está e o nome da tabela; eu começo o nome da tabela com uma crase e essa tabela do Google Analytics está dentro de um data set do BigQuery que é bigquery-public-data.google_analytics_samples. Essa tabela está particionada - ela é dividida por dias.

[03:38] Eu vou pedir para trazer todas as tabelas de sessões e eu passar as sessions e um asterisco no final. Então traz todas as sessões para mim, é simples, select*FROM data set, tabela, qual partição e vou colocar só um limite aqui, como essa tabela é muito grande, para começar a trazer somente cem linhas.

[04:09] Posso executar essa query clicando em executar ou Control + enter, aqui do lado pode ver o tempo de processamento - quanto tempo está demorando para executar essa query solicitada. Demorou 6.8 segundos, processou 5.4 GB de dados e vai dar o resultado aqui embaixo.

[04:35] Então se vocês lembrarem da tabela usada no primeiro curso vocês vão notar semelhanças, por exemplo, visitId, visitStartTime, date e assim por diante, todas aquelas informações que você tinha naquele csv que disponibilizei no primeiro curso, estão aqui. Há um volume muito grande de informações e vamos conseguir através do BigQuery acessar essas informações.

[05:03] Mesmo no volume grande e o nosso próximo desafio vai ser preparar um notebook no Datalab para levar as informações que estão aqui no BigQuery para lá. E com query é bem simples.

[05:18] Notem que você apenas digitou a query, executou e as nossas informações já estão na tela, sem ter de configurar nenhum tipo de ferramenta complexa. No próximo passo vamos configurar o Datalab para começar a nossa exploração. Até lá!