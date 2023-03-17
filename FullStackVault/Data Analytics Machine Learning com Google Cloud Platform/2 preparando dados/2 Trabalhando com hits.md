[00:00] Agora que já carregou a nossa base, podemos começar a trabalhar com ela, mas antes disso, você notou que em alguns pontos desse curso vai demorar um pouco mais para processar.

[00:09] Um ponto importante trabalhando com Datalab é, caso você tenha de desligar o Datalab, fechar a aba e depois voltar, para você iniciar o Datalab novamente, basta abrir o Cloud Shell; digitar o Datalab connect e o nome da máquina. No caso da minha máquina teste-alura.

[00:37] Tenha certeza de que você está conectado no projeto que está utilizando, My First Project, se você quiser criar um outro projeto, só clicar e seguir os passos. Está falando o projeto que eu estou conectado, Id do projeto, caso você saia e tenha de voltar basta fazer Datalab connection test, o nome da sua máquina - a minha chama teste-alura.

[00:58] Voltando para nosso notebook há um ponto diferente do nosso curso. No primeiro curso não utilizei a coluna de hits, expliquei que os hits são cada iteração que o site faz com o Google Analytics. Todos os tipos de operações que são rastreados, por exemplo, se eu fizer o Google Analytics do Google Cloud Platform.

[01:25] Então, eu cliquei nessa parte e selecionei, cliquei em outra parte, todo tipo de evento que é rastreado, ele gera um hit de volta para o Google Analytics. Lembrando que estamos trabalhando com um e-commerce, um hit muito comum é de pessoas clicando em produtos, fazendo iterações com os produtos.

[01:45] Estamos tentando prever quanto esse usuário vai gastar, saber quais os produtos que ele clicou e teve iteração pode ser uma variável importante para o nosso modelo. Vou trabalhar agora com a coluna hits para conseguir gerar informação para o nosso modelo através de quais produtos o usuário teve iteração durante aquela sessão.

[02:10] Se você lembrar bem, cada coluna para linha no nosso data frame é uma sessão, se olhar, por exemplo, a sessão zero, a linha zero que é a primeira sessão que tem no data frame, você vai notar todas aquelas informações que você viu por usuário de cada sessão.

[02:35] Note que essas informações ainda estão guardadas em formato de chave valor e vamos tratar igual ao primeiro curso, mas temos aqui as informações do hits. Ela começa com esse símbolo que quer dizer que é uma lista, tem vários hits dentro da mesma sessão e é isso que vai ser um desafio para trabalhar.

[02:59] Se você olhar df.iloc ao invés da primeira linha somente o que tem dentro do primeiro hits, vai ver que eu tenho uma lista com vários dicionários dentro dessa lista. Esse caso aqui só tem um, mas eu posso ter vários dicionários dentro da lista e várias informações de dicionários.

[03:19] Então, você vai precisar pegar essa lista e quebrá-la, cada vez que achar um hit de um produto vai criar uma coluna nova para esse produto, porque um usuário pode fazer iterações com vários produtos dentro da mesma sessão.

[03:40] Quero ter no final uma tabela que por sessão eu saiba se o usuário interagiu com aquele produto ou não, preciso saber todos os produtos de uma só vez eu não posso também colocar no meu modelo uma variável que tenha todos os produtos dentro da mesma célula, dentro da mesma variável.

[04:02] Vou precisar criar uma coluna para cada produto e saber se tem uma iteração com aquele produto, aquela sessão ou não. No próximo vídeo você vai fazer o código para conseguir abrir essa lista em novas variáveis que vai falar quais produtos esse usuário teve iteração e mais outras informações sobre esse produto. Até lá!