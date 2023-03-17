[00:00] Agora você pode começar a criar variáveis com a coluna hits. Para acessar os valores dos produtos, dentro dessa coluna hits, pode pegar, por exemplo, um usuário que teve várias iterações. O usuário 365 que eu já verifiquei que teve iterações com produtos, desce na chave produto e eu tenho aqui uma lista com vários dicionários que são os produtos que esse usuário teve iteração.

[00:35] O primeiro produto tem: o nome do produto, o SKU do produto, o preço e assim por diante, embaixo eu tenho um outro produto SKU diferente, preço diferente, outros produtos e assim por diante.

[00:52] Como que você vai pegar essa informação? Lembrando que tem uma lista, eu tenho de escolher qual índice dessa lista eu vou acessar, se eu acessar o primeiro índice, eu tenho o primeiro valor dessa lista, o primeiro hit de dentro dessa lista.

[01:15] Temos e posso acessar a parte de produto desse dicionário, para acessar um valor no dicionário eu passo a chave e posso acessar a parte product e agora eu não tenho mais aquele dicionário. Eu tenho outra lista com vários produtos, então seleciona de novo o primeiro valor da lista e eu tenho somente o primeiro produto, posso acessar productSKU.

[01:53] Eu tenho o SKU do primeiro produto do primeiro hit da primeira sessão. Para organizar isso pegando todos os produtos de todos os hits de todas as sessões vai ter de criar um loop e entrando em cada step desse igual você já verificou aqui.

[02:14] Vamos criar um loop, mas temos de armazenar essas coisas dentro de algumas listas para criar variáveis na nossa tabela. Você vai criar produtos_sessao, vai ser uma lista vazia nesse momento e vai iterar primeiro dentro de cada linha do df hits.

[02:38] Vou fazer for linha in df.hits e vou iterar dentro de cada linha em df.hits. Posso iterar dentro de cada hit que dentro dessa sessão. Assim, vou fazer for hit in linha: e vou verificar quais são os produtos que foram iterados dentro desse hit.

[03:12] Note que como eu vou fazer essa iteração e colocar dentro de uma lista, eu vou criar uma lista separada para armazenar todos os produtos daquele hit. Então, produtos_hit = lista vazia.

[03:34] Vou colocar todos os valores dentro de uma lista depois pegar essa lista e colocar numa lista maior, depois na próxima sessão fazer a mesma coisa e vai armazenando dentro dessa lista produtos_sessao várias listas, com todos os produtos daquele hit.

[03:48] Eu já estou dentro do hit, posso fazer for produto in hit product, assim, estou acessando cada produto dentro de hit product e vou fazer o append desse produto, de cada um desses produtos na minha lista com todos os hits, append produto.

[04:38] Podemos passar SKU, para saber todos os produtos vamos considerar o SKU como código único desse produto, código único para cada um dos produtos. Estou criando uma lista de produtos hit com todos SKU de produtos que tiveram iteração dentro daquele hit.

[04:59] Eu preciso fazer uma append na produto_sessão.append produtos hit. Dentro de produtos_sessao para cada sessão vai ter uma lista de produtos que tiveram iterações em cada hit.

[05:33] Se eu executar, eu vou ter todos os SKUs dentro desse produto, para deixar isso um pouco mais completo vamos fazer a mesma coisa só que para preço, espaço, então, preços_sessao, vou criar uma outra preços_hit e eu vou fazer o append do mesmo jeito.

[06:15] Vou fazer append em preços e pegar ao invés de product SKU vou pegar o preço, que pode verificar qual é o nome dessa chave, productPrice, colocar e vamos fazer o append do mesmo jeito que fizemos, produtos_sessao.append em preços_sessao.

[06:56] Para o caso de preços como eu vou ter uma lista com vários preços, em vez de ter um preço para cada produto depois eu tenho de ter uma lista com esses valores de preço, você pode de fazer uma forma diferente. Já que esse é um valor quantitativo, pode fazer a soma de todos esses preços no hit.

[07:20] Você pode fazer o append dessas iterações do hit, de todos os preços desse hit, pode executar, vamos olhar o que há dentro de cada uma dessas listas, vamos ver o tamanho primeiro, produtos_sessao, total do tamanho do data frame: 64.694 .

[08:03] O primeiro valor que eu tenho pode ser que ele seja vazio, porque esse primeiro como você viu não teve muitas iterações; se olhar o valor 365 que é aquele que tínhamos visto lá em cima, tem uma lista com vários produtos que tiveram iteração.

[08:26] Nosso objetivo que era pegar todos os produtos que teve iteração na sessão foi alcançado, na lista de preços tem esse valor que é o total, a soma de todos esses produtos que teve iteração.

[08:50] No próximo vídeo criaremos as variáveis com essa lista que você fez; então você vai criar as colunas aqui no nosso Dataframe que vai dizer se esse usuário teve iteração com o produto x ou não, até lá!