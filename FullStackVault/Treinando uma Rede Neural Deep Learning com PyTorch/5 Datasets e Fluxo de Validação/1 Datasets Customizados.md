[00:00] Agora vamos trabalhar com nossos próprios dados. Primeiro, podemos partir do mesmo código que tínhamos feito antes, porque o início vai ser basicamente a mesma coisa. Iremos usar o imports, o dataloader, mas não iremos usar os datasets e transformers, porque eles são para trabalhar com datasets do dot vision.

[01:05] Podemos deixar os mesmos hiper parâmetros. Depois, temos a verificação se iremos usar CPU ou GPU. Estamos usando GPU. Agora, vamos conhecer a classe dataset que eu adicionei. Estamos usando o cuda.

[01:32] Dataset é uma super classe. Ela vai permitir que implementemos nosso próprio dataset interpretável pelo Pytorch, porque teremos todo aquele ferramental para criação de batchs, embaralhamento, carregamento inteligente da CPU.

[02:02] Iremos trabalhar com o dataset do bike sharing. Ele tem informações da estação do ano em que estamos, se é feriado ou não, o dia da semana, a temperatura, se está nublado. O que você tem que prever é quantas bicicletas vão ser alugadas dadas essas previsões do tempo. Temos que prever um valor contínuo de acordo com atributos que iremos receber.

[02:40] Em cima, tem como fazer o download. Iremos clicar no data folder e baixar no código o dataset. É só trabalhar como se fosse um terminal. Usamos um comando para fazer o download e para fazer o unzip. Ele vai baixar as informações, descompactar. Se você olhar, temos as informações zip e csv.

[03:40] Vamos usar o pandas para criar um dataframe, porque esses dados são tabulares por enquanto. Iremos ler do csv. Podemos ver os dados por dia ou por hora. Vou pegar por hora por ter mais dados.

[04:35] Temos a instância, que é só um index, a data, estação do ano, qual o ano que estamos olhando, se é dia útil, o dia da semana, o tempo. Tem várias condições e no final os alugueis pegos.

[05:30] Já que temos um único csv de treino e teste, vou separar em dois csv, um em dados de treino e outro de teste, para que possamos fazer o treino e validação. Vou usar a função randperm do Pytorch. Ele vai me dar uma permuta aleatória de valores de 0 a 9, se eu colocar 10, por exemplo. Vou usar essa função para pegar uma amostra aleatória dos dados e separar para teste, assim não pego em sequência e não tenho nenhum viés.

[06:33] Primeiro vou colocar uma raiz para que vocês usem as mesmas amostras que eu. Vou pegar alguns índices usando o randperm. Ele vai fazer uma permuta aleatória entre as 17 mil amostras. 80% do dataset vou pegar para treino. Estou selecionando as amostras daqueles índices que eu selecionei.

[07:30] Eu criei índices, que é uma permuta aleatória das nossas amostras entre 0 e 17 mil. Quero que o tamanho do meu treino seja de 80% e estou apagando do dataframe principal dentro da minha lista de índices os primeiros 80% da permuta aleatória.

[08:05] Para o teste, é só fazer a mesma coisa. Só que dessa vez a partir da posição train size até o final. O que eu fiz, quando criei os índices, ele é uma permuta aleatória de valores. Quando digo que quero de 0 a train size, estou dizendo para ele me dar os primeiros 13.900 valores aleatorizados. E depois os outros 3 mil valores. Assim pego valores aleatórios para teste.

[09:20] Basta eu salvar cada um desses dataframes em um csv separado, com index falso para não salvar os números, porque eles não são relevantes, e a mesma coisa para o teste.

[10:02] Temos 13.900 amostras de treino, 3.400 de teste. O dataframe de cada uma ficou dessa forma e temos o bike test e o bike train para trabalhar. Vamos ver agora o dataset. Da mesma forma que aprendemos a criar uma rede neural com init e forward, para o dataset precisamos apresentar init get item e len, que é a quantidade de amostras.

[10:37] Do mesmo jeito que já sabemos fazer, primeiro eu vou criar minha classe, que é meu dataset, que posso chamar de qualquer coisa. Só preciso dizer que isso é da classe dataset. Depois, faço a mesma coisa que fiz para criar uma rede neural, vou implementar a função init self def get item self, e o índice, depois o def len self.

[11:20] No init é quando vamos definir onde encontramos todas as amostras do dataset. Posso salvar onde é a raiz do dataset, uma lista das amostras que tenho disponível. Como todas minhas amostras estão no mesmo lugar, vou usar o init para carregar todos os dados do meu csv que vou criar como parâmetro, para poder criar um dataset de treino e passar o caminho do parâmetro.

[11:58] Eu li o csv. Na hora de pegar um item só, tenho a variável self.dados que vai ter todas as minhas amostras. Na hora de ler um dado, ele vai sortear um índice e vai mandar como parâmetro internamente para o get item qual o índice. É só você pegar o elemento ao qual ele se refere nos seus dados. Internamente, quando você instanciar o dataset e o dataloader, o Pytorch vai cuidar disso.

[12:52] Vou pegar as colunas 2 até 14, porque é onde tenho informações relevantes para o nosso problema. A coluna 1 é só um índice a coluna 2 é a coluna da instância, que é uma informação interna do dataset. Só preciso das informações que são relevantes para o problema, como o dia, a estação do ano, etc. E a coluna 15 é a resposta, não queremos ela. Ela vai representar nosso rótulo.

[14:00] No meu get item estou carregando só uma amostra. Não preciso me preocupar com carregar um batch, um conjunto de dados, porque o próprio Pytorch vai lidar com isso.

[14:27] Minha variável resposta vai ser o label. Depois retorno a tupla sample label. Quando pegamos o dataset, eu comentei com vocês que obrigatoriamente a saída dele vai ser uma tupla. Quando pego uma amostra do meu dataset, ele vai dar um tipo tupla, e o tipo do dado é uma classe mnist, estamos garantindo os mesmos requisitos. Quando eu instanciar esse dataset, ele vai ser uma classe do tipo bicicletinha, e não mais mnist. Quando eu pegar um item dele, vai me retornar uma tupla sample label.

[15:12] Na hora de dizer quantos dados eu tenho, que é o que essa função pede, é só retornar o tamanho da minha variável self.dados. Completamos todos os requisitos e vamos visualizar uma amostra.

[15:42] Vou copiar do mnist, porque é a mesma coisa para carregar. É a mesma ideia. Fazer train set, test set, chamar a classe do dataset que criamos e passar os parâmetros solicitados. No nosso caso, ele só pede um csv.

[16:42] Posso visualizar uma amostra dos meus dados. Nosso rótulo é um valor, foram 73 alugueis de bicicleta, dado que as condições do dia eram essas. Basta construir agora o dataloader. Posso copiar o mesmo que eu fiz para mnist, porque vai ficar idêntico. Não importa se eu fiz o dataset ou peguei um. Não preciso mudar absolutamente nada.

[18:18] Agora ele sabe que tenho um batch de 20 amostras e cada amostra tem 12 atributos, com 20 rótulos de tamanho 1. No próximo vídeo concluímos implementando a MLP e fazendo o fluxo de treino e validação.