00:00] Como último passo antes de entrar na modelagem, faremos alguma preparação da nossa base de dados, que vai ser igual à feita no primeiro curso. Então vou deixar o código embaixo também, mas basicamente você vai criar variáveis que fala o que aconteceu na primeira e na última visita.

[00:16] Vamos criar muitas variáveis baseadas nas informações que temos sobre a primeira e a última visita de cada usuário, além disso, vamos também identificar as colunas que são que são qualitativas, variáveis categóricas, vamos fazer o label transformando essas colunas em números.

[00:39] Você pode copiar o código que vou deixar, esse mesmo código bem parecido com que foi feito no primeiro curso. Vou transformar a visão de visitas para uma visão de usuário, vou criar aquela coluna com os totais, qual foi o canal que ela acessou a primeira visita, a última visita e assim por diante.

[01:11] E essa outra parte do código vai fazer o encoding dessas variáveis, além de remover as variáveis que são Id que não trazem informações realmente, fazer o drop dessas variáveis e criar uma variável y que vai ter a nossa variável resposta e a variável x.

[01:32] Além dessa última parte onde faz o encoding das nossas variáveis, qualquer dúvida nessa parte temos lá no primeiro curso, quando eu explico a lógica de criar variáveis considerando a primeira visita, a última visita, além das variáveis quantitativas também.

[01:52] Estamos fazendo encoding das variáveis, temos um warning que está substituindo um valor dentro do Dataframe e ao final deve ter uma variável x com todas as nossas variáveis explicativas e y que vai ser a nossa variável resposta.

[02:27] Ele terminou de rodar como há várias colunas nesse Dataframe essa operação pode demorar um pouco, então agora temos o nosso x com 2.271 variáveis, nosso modelo ficou muito grande 53.000 linhas.

[02:43] E o X.head com essas colunas que mostram o que aconteceu na primeira, o que aconteceu na última visita. Note que essa redução que tem no volume de linha é devido ao fato de estamos falando de usuários e não visitas.

[03:06] Esses usuários únicos que acessaram no site durante esse tempo. Nossa base está pronta para separar em teste, em treino e já começar a fazer a modelagem, que é o próximo vídeo.

# MultiLabelBinarizer

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/59709/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/59709/question)

Ao analisar os produtos comprados por clientes em uma loja, temos para cada cliente e data, uma lista do Python com os produtos que foram comprados.

Para passar a informação de uma forma que o modelo possa interpretar, podemos criar uma coluna para cada produto, e utilizar um valor binário(0,1) para identificar se aquele produto foi comprado em determinada linha:

![tabela com detalhes sobre os produtos comprados por clientes em diferentes datas, produtos que aparecem, macarrão, tomate, trigo, carne, ovos, cebola e alho](https://caelum-online-public.s3.amazonaws.com/1313-Data+Analytics%3A+Avan%C3%A7ando+em+Machine+Learning+no+Marketing+Digital/Screenshot_1.png)

Considerando a tabela acima, após o tratamento com MultiLabelBinarizer, quantos novas colunas teremos?

Selecione uma alternativa

-   Sete colunas.
    
-   Nove colunas.
    
-   Cinco colunas.
    
-   Onze colunas.