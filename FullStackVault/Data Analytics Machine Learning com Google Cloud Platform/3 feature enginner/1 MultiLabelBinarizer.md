[00:00] Já temos nossas listas com as informações que precisamos. Vamos criar as colunas aqui no data frame que vai mostrar qual o total dos preços dos produtos que esse usuário iteragiu nessa sessão e quais foram os produtos.

[00:17] Precisa de uma coluna para cada produto, eu posso ter vários produtos, eu quero saber de todos esses produtos se ele iteragiu com esse ou aquele. Você precisa transformar essa lista de listas de produtos em informações 0 1, iteragiu ou não.

[00:41] Para ficar mais fácil de visualizar, vamos transformar essa lista em uma series do pandas para começar a colocar no formato de Dataframe, eu posso fazer s é igual a pd.Series e vou passar produto_sessao.

[01:08] Se eu olhar s, tenho uma series como se fosse uma coluna do Data Frame com várias listas vazias e eu tenho vários usuários que fizeram iteração; eu preciso transformar isso em várias colunas com cada valor desse, cada valor de produto aparecendo uma vez só.

[01:37] Um pouco complexo o que você precisa fazer, eu preciso saber para cada lista dessa todos os produtos mesmo que ele não apareça nessa linha e se é 0 ou se 1; ou seja, se tem um hit para aquilo ou não. Tem uma função, uma biblioteca já disponível dentro do sklearn que vai ajudar para isso que é o MultiLabelBinarizer - ele vai pegar minhas labels e vai transformar em colunas binárias de 0 ou 1, vamos ver com calma como que vai funcionar.

[02:13] Eu vou fazer from sklearn preprocessing import MultiLabelBinarizer, já importei a minha biblioteca e vamos ver como é que funciona. Bem parecido com os algoritmos de modelos dentro do sklearn eu vou instanciar em uma variável, vou chamar de mlb = MultiLabelBinarizer().

[03:02] Como os outros métodos do sklearn tenho uma função aqui dentro que é para fit_transform - ele vai entender qual é o padrão do meu dado, entender todas as labels e valores possíveis que essa variável pode ter.

[03:30] E ele já vai converter para cada um daqueles 0 ou 1 para aquele valor. Por exemplo, já criei o meu s e posso passá-lo dentro, vou deletar esse; tenho uma array com várias listas e cada lista dessas tem exatamente a quantidade de produtos que teve em todas essas sessões e fala se essa sessão teve iteração naquele produto não.

[04:07] Todos esses da primeira posição estão representando apenas um produto e todos esses aqui não tiveram iteração com esse produto e assim por diante. Podemos transformar esse em um Dataframe, chamando a função pd.DataFrame, esses vão ser os nossos dados do Dataframe, nesse caso vamos passar o nome das colunas no Dataframe e o mlb tem um atributo que são classes - que foi o que utilizou para fazer essas arrays.

[04:53] Posso passar esse atributo classes e tenho de passar o índice também, no caso do índice eu vou passar o mesmo do df lá de cima porque é do mesmo tamanho.

[05:15] Então, vou fazer df.index, DF esse F maiúsculo e eu tenho aqui o meu Dataframe com todos os códigos de produto e o valor 0 ou 1 para se aquele usuário, aquela sessão teve iteração com esse produto ou não.

[05:47] Ele está falando que essa sessão não teve iteração com esse produto, nem com esse ou este, já essa sessão teve com todos esses produtos.

[06:01] Pode salvar isso em um Dataframe, vamos chamar de df.produtos, que acabamos de verificar. Posso fazer o join desse Dataframe com o nosso Dataframe original que é o df.

[06:21] Vou fazer df = df.join(df_produtos), df.head(), note que eu tenho as mesmas colunas que eu tinha com várias colunas 01 dos produtos, ficou bem maior com 1.125 colunas.

[06:49] Lembrando que preço é apenas uma lista com vários valores (não é uma lista com outras listas dentro e vou criar várias colunas) vai ser uma coluna apenas. Eu posso simplesmente fazer df preço é igual preço sessão e consigo criar dentro do meu Dataframe uma última coluna.

[07:25] Vou dar df.head novamente, tenho o preço desse produto, já criamos o df com preço e com todos os produtos 0 ou 1 e podemos criar um df novo, onde vamos começar a fazer o fit enginer de todas as outras colunas como fizemos lá no nosso primeiro curso.

[07:54] Vou digitar, visitas = df.drop([‘hits’,‘customDimensions’]), essa coluna vai ter algumas informações customizadas da página e não vamos precisar dela nesse momento, por isso podemos tirá-la também.

[08:25] Já usei a coluna hits, a coluna customDimensions você não vai usar nessa parte, posso tirar, vou passar o axis=1. Vou criar um Dataframe visitas que não vai ter mais a coluna hits nem a coluna customDimensions. Vamos ver como fica.

[08:49] Beleza. Se observar visitas.head tem Dataframe, não tenho mais as colunas hits nem customDimension e pode seguir para o próximo passo que vai ser fazer um pouco parecido do tratamento feito no primeiro curso, até lá!

# Para saber mais

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/59710/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/59710/question)

O MultiLabelBinarizer é utilizado para casos onde temos várias labels dentro da mesma “ocorrência”. Em caso mais simples onde temos uma coluna com uma categoria por linha, uma forma bem simples de fazer esse tratamento é com o método “get_dummies” do Pandas.

```bash
pd.get_dummies(df[‘sx’])
```

![tabela com uma coluna sexo convertida em duas colunas com valores binarios para feminino e masculino](https://caelum-online-public.s3.amazonaws.com/1313-Data+Analytics%3A+Avan%C3%A7ando+em+Machine+Learning+no+Marketing+Digital/Screenshot_2.png)

No exemplo acima, para cada valor único da coluna “sx”, será criado uma coluna que é marcada com “1” quando há ocorrência do valor da coluna, e “0” quando não há.