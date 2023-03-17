[00:00] Conforme já falei, esse curso é a continuação do primeiro curso dessa série e alguns passos de tratamento dessas variáveis que estão em formato dicionário, já fizemos no curso anterior e para não ficar repetitivo vou disponibilizar alguns códigos abaixo do vídeo para você rodar e executar.

[00:20] Basicamente você vai abrir nesses espaços todas variáveis que estão em dicionários em novas colunas, com as novas variáveis e você vai verificar variáveis também que às vezes não têm valor, que tem apenas um valor o tempo todo então não traz nenhuma informação relevante.

[00:39] Você vai excluir essas variáveis também, se você ficar com alguma dúvida sobre o que fazer em algum passo aconselho a voltar para o primeiro curso e assistir a parte onde você faz o tratamento desses dados.

[00:52] Apenas para recordar um pouco eu tenho variáveis do tipo dicionário aqui em cima, eu vou chamar uma variável de dicionários, uma lista com todos os valores dessas colunas, device trafficSource geoNetwork totals, uma lista com todas essas variáveis que vão ter de ser tratadas.

[01:51] Eu vou abrir todos os valores que têm aqui dentro em novas colunas e eu vou copiar o código para colocar, tem o código que vai fazer o tratamento dessas variáveis, você vai rodar aqui e executar.

[02:06] Ele está entrando dentro de casa uma dessas variáveis, abrindo todas as chaves em novas colunas, verificando se existem variáveis com apenas um valor e excluindo essas colunas.

[02:26] Após esse passo, você pode continuar fazendo o tratamento também parecido com o tratamento feito no outro curso. Ele está rodando, imprimiu quantos valores únicos para cada uma das variáveis - tem muitas variáveis que são dos produtos com dois valores em todas.

[02:49] Para ficar um pouco mais limpo o nosso notebook, eu posso limpar clicando em clear, para ele reduzir a quantidade de informação, mas ele já rodou então o nosso Dataframe visitas já tem colunas novas.

[03:08] E outra coisa que eu posso fazer, dentro do Dataframe visitas tem novas colunas, note que esse Dataframe direto do BigQuery tem diferença do primeiro que são duas colunas transaction revenue. Foi adicionada uma nova coluna TotalTransactionRevenue, precisa usar essa coluna no lugar da TransactionRevenue.

[03:41] Eu vou excluir essa coluna transaction revenue para ela não atrapalhar nossa base de dados, visitas.drop vou copiar o nome dela, axis vai ser igual a 1, inplace=True esse código que vai excluir essa coluna.

[04:17] Outra coluna que eu posso excluir é a coluna transactions, como essa coluna fala se existe uma transação naquela sessão, pode ter um vazamento de informação para nossa predição. Concorda comigo que se teve uma transação naquela sessão quer dizer que ele fez uma compra.

[04:40] Para fazer o nosso modelo enxergar uma informação futura é importante tirar aquela coluna transaction também, muito parecido com que fizemos no primeiro curso vamos deixar disponível o código, transformar a coluna TotalTransactionRevenues para o número um pouco mais real.

[05:04] Lembrando que ela é multiplicada por 1 milhão, você a converte para o valor real dividindo TotalTransactionRevenues por um milhão, certo, pode rodar esse código.

[05:16] Nos próximos passos você já começa a criar aquelas variáveis que você criou no primeiro curso, são as informações sobre a primeira visita do usuário, as informações sobre a última visita do usuário e assim por diante.
# Código do último vídeo

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/76724/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/76724/question)

Código mencionando no último vídeo do curso anterior.

```css
import json

# Transformando as chaves dos dicionários em novas colunas
for coluna in dicionarios:
  visitas = visitas.join(
    pd.DataFrame([json.loads(json.dumps(linha))
      for linha in visitas[coluna]]) , rsuffix=('_' + coluna) )
visitas.drop( dicionarios, axis=1, inplace=True)

# Corrigindo o formato das colunas com valores quantitativos
totals = df.totals[0].keys()
totals = list(totals)
for coluna in totals:
  visitas[coluna] = pd.to_numeric(visitas[coluna])

# Limpando os dados
visitas.drop('adwordsClickInfo', axis=1, inplace=True)
# Remove as colunas cujo domínio só tem um elemento
coluna_na = []
for coluna in visitas.columns:
  print(str(coluna) + ': ' + str(len(visitas[coluna].unique())))
  if len( visitas[coluna].unique()) == 1:
    coluna_na.append(coluna)
visitas.drop( coluna_na, axis=1, inplace=True)
```