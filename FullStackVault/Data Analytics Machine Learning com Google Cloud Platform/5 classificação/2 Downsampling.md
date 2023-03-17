[00:00] Temos um caso de uma base de dados desbalanceada onde há muitos usuários que não gastaram, essa primeira linha, e poucos usuários que fizeram uma compra. Quando treinamos modelo em cima de uma base de dados desbalanceada pode normalmente ter um resultado muito bom para categoria com maior frequência e um resultado ruim para categoria com pior frequência.

[00:26] Note que eu tive 203 usuários que fizeram compras e eu acertei 73 desses usuários, para ajustar um pouco base de dados e tenta melhorar o nosso modelo faremos um Downsample que é uma das técnicas possíveis para você trabalhar com base de dados desbalanceados e é muito simples.

[00:50] O Downsample vai reduzir a sua categoria, sua label, com maior frequência. Vai reduzir a quantidade de amostras dos usuários que não fizeram compras, seguindo a mesma lógica com algumas bibliotecas sklearn. Faremos o Downsample na base de treino.

[01:16] Porque a nossa base de teste tem de refletir a realidade do dia a dia, lembrando que temos a nossa base de X train, eu vou trazer de volta para essa base de treino a coluna resposta, porque é a que eu vou usar para dividir entre os usuários que não gastaram e gastaram.

[01:33] Vou colocar X_train revenue é igual Y_train, vou trazer de volta essa informação que tinha tirado lá atrás. Como eu já trabalhei com esse X_train várias apenas um warning, pode seguir X_train.head(), o meu revenue está no final.

[02:12] Ótimo, eu posso fazer uns Dataframes com os usuários que gastaram e os que não gastaram, o Dataframe dos usuários que gastaram vai ser usuários_com_gastos é igual X_train onde X_train.revenue maior que zero.

[02:39] O tamanho do Dataframe é de 459 usuários, e o dataframe dos usuários sem gastos vai ser onde X_train for menor ou igual a zero. O tamanho desse é de 36.669 usuários. Já pode pegar esse Dataframe de usuários sem gastos e diminuir ele para conseguir mexer um pouco na frequência de categorias entre os que gastaram e não gastaram.

[03:39] Vamos importar aqui do sklearn dentro de utils import resample, agora vou criar um Dataframe novo de usuário sem gastos, vou chamá-lo de usuário sem gastos ds que vai ser igual a resample e aqui dentro eu vou passar várias coisas.

[04:11] Primeira coisa que eu vou passar é qual o Dataframe que eu vou fazer vou fazer o resample em cima do usuário sem gastos, estou fazendo Downsample, vou pegar qual a categoria de maior frequência e vou falar quantas eu quero manter.

[04:32] Outra coisa que eu vou passar é o replace=False, isso quer dizer que quando eu tirar uma linha daquele Dataframe eu não vou repor com outra aleatoriamente. Tem que passar aqui mais algumas opções, a primeira outra opção que vai passar aqui vai ser quantos samples vamos manter.

[04:50] Assim, n_samples= eu tenho 36.669 usuários e eu vou fazer para esse teste que estou rodando eu vou reduzir apenas para 30, porque como a nossa base de dados é muito pequena. Vamos supor se eu quisesse 50% dos usuários com gastos e 50% sem gastos eu tinha que reduzir esses 36.669 para festa 459 usuários, assim eu teria uma base com algo em torno de 900 usuários.

[05:26] Nossa base ficaria muito pequena e poderia ter uma performance ruim, então talvez para consegui fazer uns 50/50 eu vou ter de pegar uma quantidade de usuários muito grande para mesmo depois de fazer um Downsample eu ainda ter uma amostra significativa.

[05:41] Para esse teste que estamos rodando, vamos deixar em 30.000, então estou reduzindo a quantidade de usuários sem gastos, como fizemos também lá nos modelos, vamos tentar um random_state para caso eu vou rode novamente, consiga a mesma aleatoriedade.

[06:02] Essas são as nossas configurações. Eu Posso rodar isso aqui, já rodou, se olhar o tamanho dessa base eu tenho 30 mil usuários, que foi o que eu pedi para que ele reduzir, ele selecionou 30.000 usuários aleatoriamente dentro dessa base de 36.669.

[06:35] Eu vou criar um X_train_ds com Downsample que vai ser a parte de usuários sem gastos com Downsample mais a parte de usuários com gastos. Vou fazer pd.concat()e vou colocar esses dois usuários juntos dentro desse novo Dataframe.

[07:11] Eu tenho de colocar uma lista, vou rodar, beleza. Eu tenho uma base de dados com 30.459 linhas que é a minha base de sem gasto de 30 mil e a minha base com 439.

[07:38] Fique à vontade caso você queira testar com outros tipos de frequências - reduzir para 10000, e entender como que o modelo se comporta conforme você vai mexendo.

[07:51] Além disso, pegar talvez período de tempo maior e testando como que o modelo comporta conforme você vai mexendo na frequência de cada categoria; no próximo vídeo vamos retreinar no modelo agora com Downsample.