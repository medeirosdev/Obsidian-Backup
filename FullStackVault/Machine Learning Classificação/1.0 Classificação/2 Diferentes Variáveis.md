[00:00] Antes de entrarmos de fato na definição de classificação, vamos entender melhor quais os tipos de variáveis que temos no nosso conjunto de dados.

[00:09] Quando estamos trabalhando com os dados podemos ter dois tipos de variáveis: as variáveis categóricas e as variáveis numéricas.

[00:16] Vamos retomar a nossa função _head_ para identificar melhor quais os tipos de variáveis que temos no nosso _Dataset_. Vamos lá.

[00:26] Primeiro, vamos conferir a variável que está aqui na tabela com o termo Cônjuge, temos sim e não. Podemos classificar nossos clientes como pessoas que possuem ou não possuem cônjuge, ou seja, possuem ou não parceiro, ou uma parceira. Isso representa uma forma de agrupamento por características em comum, isso quer dizer que temos a nossa primeira variável categórica.

[00:57] E as variáveis categóricas não representam somente aqueles agrupamentos por características em comum, mas também valores qualitativos. Como, por exemplo, a nossa variável dependentes, se a pessoa possui ou não filhos, se possui ou não alguém que dependa dela no plano, que ela assina aqui na nossa empresa. Temos outra variável categórica contendo sim e não.

[01:25] Agora, vamos conferir os meses de contrato. Nós temos o tempo que a pessoa permanece atualmente com o contrato em ativo, que ela está em contrato ainda com a nossa empresa. Temos aqui um mês, 34 meses, dois meses. Isso aqui são valores numéricos, meses de contrato é uma variável numérica que representa uma medida ou um conjunto infinito de valores.

[01:59] No nosso caso, meses de contrato é uma medida de tempo. Agora, atenção, temos um maior de 65 anos, ele também está contendo números, 0 e 1. Já sabemos que não é 0 e 1 é o sim. Maior de 65 anos é uma variável numérica? Nesse caso não, porque podemos agrupar nossos dados como pessoas idosas que contém mais de 65 anos e pessoas mais novas, não idosas ainda que possuam menos de 65 anos. Maior de 65 anos também é uma variável categórica, apesar de conter valores numéricos.

[02:47] Agora vamos olhar as outras variáveis, temos telefone fixo também contendo sim e não, também valor categórico, várias linhas telefônicas contendo sem serviço telefônico, não e sim. Temos o serviço de internet que é o tipo de serviço que a pessoa contrata, DSL, fibra óptica, podemos agrupar essas pessoas por tipo de serviço, também é uma variável categórica.

[03:16] Segurança online sim e não, também é uma variável categórica. Lembrando, que segurança online, backup _on-line_, seguro no dispositivo, TV a cabo, _streaming_ de filmes e suporte técnico dependem da pessoa assinar ou não o serviço de internet, são também variáveis categóricas. E tem aquela informação: sem serviço de internet, não e sim.

[03:44] Agora, tipo de contrato também, podemos agrupar os clientes por tipos de contrato, aqueles clientes que assinam mensalmente, os clientes que assinam um ano. Temos a forma pagamento online, os clientes que ainda preferem receber cartas pelo Correio ou receber o boleto no seu e-mail.

[04:04] A forma de pagamento, cheque digital, cheque em papel, débito em conta, crédito, é também uma variável categórica. Agora, conta mensal é uma variável numérica porque também representa uma medida de valor, dinheiro de custo. Ou seja, quanto que a pessoa está pagando todo mês para a nossa empresa.

[04:30] E, claro, a mais importante, o Churn. Que representa se a pessoa está ou não mais na nossa empresa, se ela assina ainda ou não, se ela é fidelizada ou não, sim e não. Também é uma variável categórica.

[04:47] Deu para entender melhor quais são os valores numéricos, quais são os valores categóricos? Afinal de contas, por que precisamos saber dessas informações? É simples, quando estamos trabalhando com algoritmo de Machine Learning, temos que sempre lembrar que a máquina aprende por números.

[05:12] Quando estamos trabalhando com valores categóricos precisamos pegar essas informações e transformar de uma forma que a máquina possa aprender ou classificar essas informações. Eu vou ensinar duas formas para você aprender a processar, transformar esses dados antes de fato criarmos algoritmo para a máquina classificar.

[05:41] A primeira forma é uma forma manual, quer dizer que vamos criar primeiro o dicionário com os respectivos valores atuais e o que queremos modificar, o novo valor. Depois vamos pegar essa informação e colocar com a função _replace_, substituir a partir desse dicionário as informações que contenham sins e nãos na nossa tabela.

[06:11] Vamos começar criando o dicionário. Vamos criar uma variável para armazenar essas informações do dicionário, `traducao_dic = {'Sim' : 1, 'Nao: 0}`, onde o 1 indica que queremos que todos os termos com sim na nossa base de dados seja substituída pelo valor 1 e todos os valores contendo o não, sem o til, colocamos 0.

[07:01] Agora, depois de colocar a criação desse dicionário vamos chamar a função para substituir o dicionário na nossa base de dados e armazenar esses dados modificados em uma variável. `dadosmodificados = dados` e como queremos alterar o conjunto de informações de algumas colunas, porque não são todas as colunas que contém sim e não, vamos abrir dois colchetes e colocar as colunas que realmente contém sim e não. Faremps:

```ini
dadosmodificados = dados [['Conjuge', 'Dependentes', 'TelefoneFixo', 'PagamentoOnline', 'Churn']]
```

Todas entre aspas e com vírgulas separando cada uma das colunas.

[07:49] Depois colocamos o ponto e chamamos a função _replace_ e entre parênteses colocamos o nosso dicionário.

```ini
dadosmodificados = dados [['Conjuge', 'Dependentes', 'TelefoneFixo', 'PagamentoOnline', 'Churn']].replace(traducao_dic)
```

Em seguida, rodamos a nossa ação.

[08:02] Aqui apareceu o nosso conjunto de colunas modificadas, dá para ver aqui todos os sins e nãos, 1 e 0, não tem nenhum sim e não mais escrito. Agora a máquina vai ser capaz de entender essas informações, porém havia outras colunas na nossa base de dados com informações além de sim e não como, por exemplo, o próprio serviço telefônico, se a pessoa tem ou não, sem serviço telefônico, o tipo de internet.

[08:35] Eu vou ensinar agora a segunda forma de lidar com essa informação, que é de forma automatizada utilizando a função `get_dummies`. Essa função vai pegar as colunas e identificar as categorias presentes nessas colunas. E a partir de um _loop_ vai pegar todas essas categorias presentes nas colunas e transformar em novas colunas cada uma dessas categorias contendo 1 e 0 ou _true_ e _false_, verdadeiras e falsos.

[09:18] Vamos começar criando uma variável também para armazenar esses novos dados modificados pela função `get_dummies´. Criamos`dummie_dados = pd.get_dummies`, estamos chamando a função`get_ dummies` da biblioteca Pandas. Abre a fecha parênteses e começamos colocando o conjunto de dados que queremos modificar.

[09:46] Colocamos `dados.drop` abre e fecha parênteses, abre e fecha colchetes e colocamos as colunas que não queremos que seja modificada pelo `get_dummies`, que são as colunas que já modificamos de forma manual. Queremos remover essas colunas dos dados para que elas não sejam novamente modificadas. Colocamos uma vírgula e definimos as informações como colunas `axis=1` e fecha parênteses.

```ini
dummie_dados = pd.get_dummies(dados.drop(['Conjuge', 'Dependentes', 'TelefoneFixo', 'PagamentoOnline', 'Churn'], axis=1))
```

[10:25] Depois que realizamos essa modificação nos dados nós temos duas variáveis contendo duas formas de dados modificados, temos os dados modificados, a variável e a variável `dummie_dados`. Porém, precisamos retornar o nosso conjunto de dados original, essas informações precisam estar juntas para podermos treinar a máquina.

[10:50] Para isso vamos juntá-las através da função concatenação. Vamos criar a variável `dados_final` para ser o nosso conjunto de dados final a ser trabalhado depois desse pré-processamento, igual a `pd.concat`. Estamos novamente chamando uma função da biblioteca Pandas. Abre e fecha parênteses, abre e fecha colchetes, colocamos as duas variáveis que queremos juntar as informações, `dadosmodificados, dummie_dados`, aí colocamos vírgula e definimos que queremos juntar essas duas variáveis por meio das suas colunas, definimos `axis=1`, sendo 1 colunas e 0 linhas.

```ini
dados_final = pd.concat([dadosmodificados, dummie_dados], axis=1)
```

[11:44] Vamos ver se deu certo. Chamamos a função _head_ para verificar, `dados_final.head()` e funcionou. Aqui temos todas as nossas variáveis modificadas agora com as variáveis categóricas com valores numéricos.

[12:05] Agora sim, você e os dados estão de fato prontos para entendermos melhor o que é a classificação.No conjunto de dados mostrado na aula, percebemos que nem todas as colunas nos transmitem o mesmo tipo de informação. Algumas possuem palavras como valores e outras possuem números. Devido a essa diferenciação podemos separar os dados em:

-   Quantitativo: representam os dados numéricos.
-   Qualitativo: representam dados que expressam qualidade, opinião ou ponto de vista.

Os dados quantitativos podem ser classificados em:

-   Discretos: representam uma contagem na qual os valores possíveis formam um conjunto finito ou enumerável. Por exemplo: número de filhos, quantidade de cursos realizados, quantidade de lugares frequentados.
-   Contínuos: podem assumir qualquer valor em um intervalo de valores. Por exemplo: altura, tempo.

Os dados qualitativos podem ser classificados em:

-   Nominais: não existe uma ordenação entre as categorias. Por exemplo: sexo, doente/sadio, cor dos olhos.
-   Ordinais: existe uma ordenação entre as categorias. Por exemplo: escolaridade, classe social.

De acordo com a classificação das variáveis apresentadas no conjunto de dados _telecom_dados.csv_ utilizado no curso, quais apresentam a classificação correta?

Selecione 2 alternativas

-   A variável “Minutos totais por dia” pode ser classificada como quantitativa contínua.
    
-   A variável “Estado” pode ser classificada como qualitativa ordinal.
    
-   A variável “Custo total do dia” pode ser classificada como quantitativa discreta.
    
-   A variável “Churn” pode ser classificada como qualitativa nominal.