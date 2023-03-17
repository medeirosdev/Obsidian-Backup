[00:00] Nós já temos o BigQuery funcionando, já testamos e fizemos a query, agora vamos preparar o Datalab - é o que você pode utilizar como notebook. Assim como temos o Júpiter, temos o Colab do Google também, será disponibilizado pelo Google para criar uma instância do Datalab uma máquina virtual por trás onde vai rodar esse notebook.

[00:28] Você vai poder escolher qual recurso dessa máquina. Para subir uma instância do Datalab primeiro precisa liberar algumas APIs dentro do Google código que são bloqueadas por padrão.

[00:43] Vou procurar Compute Engine API. Vou clicar nesse botão Compute Engine API e ativar, que vai fazer a conexão do Datalab com o Compute Engine – que é necessário para ele funcionar, vem desativado por padrão, questão de segurança.

[01:20] Aqui está ativando a API. A próxima API que você vai procurar é a do Cloud Source Repositories – como se fosse git hub do Cloud, é um sistema de repositório de código fonte do Google Cloud.

[01:47] Tudo que fazemos dentro do Datalab já fica salvo dentro de um repositório automaticamente, precisar ativar essa API para conseguir utilizar o Datalab. Vamos só aguardar terminar de ativar API, assim que isso aqui terminar de rodar você vai fazer ativação do Compute Engine do Cloud Source Repositories.

[02:15] Já ativou, demorou quase um minuto aqui no meu caso pode variar um pouco, agora vou ativar - essa tela depois que a API está ativada depois vamos ativar do Cloud Source Repositories, vou clicar aqui mesma coisa, vamos clicar em ativar e vou aguardar ela ficar ativa.

[02:45] No caso essa foi um pouco mais rápida, apenas alguns segundos já ativou. APIs já ativas, agora vamos acessar o Google Cloud Shell – nós clicamos e o ativamos, o Cloud Shell é uma instância que o Google disponibiliza para executar alguns comandos via linha de comando dentro do Google Cloud.

[03:18] Então é uma máquina mesmo, uma máquina Linux que ele deixa disponível para cada usuário dentro do dentro do Google Cloud e você pode usar para executar os comandos que você quer e algumas coisas via linha de comando, assim como o Datalab precisa fazer essa criação da instância via linha de comando, usa o Cloud Shell para isso.

[03:42] Para não precisarmos fazer da nossa máquina SDK do Google Cloud, então pode usar o Cloud Shell, está instanciando essa máquina mesmo que está por trás disso, estou dentro dessa máquina Linux.

[04:03] Posso dar um LS, tenho uma máquina que está com meu usuário e eu sei o nome do meu projeto, o Cloud Shell vai servir para fazer esses códigos, usar via linha de comando e para criar o Datalab existe um comando bem simples do Google Cloud que é “datalab create” – coloca o nome da máquina que você quiser, eu posso chamar de teste-alura.

[04:35] Antes de criar a máquina, vamos observar um ponto: uma das vantagens de usar o Datalab é você escolher a máquina que está por trás do seu notebook, então pode usar os créditos para criar uma máquina mais potente para processar nossos dados.

[04:55] Vamos ver dentro do Google Cloud quais tipos de máquina estão disponíveis. Vou fazer uma pesquisa tipos de máquinas Google Cloud, tipos de máquinas, documentação do Compute Engine se eu descer há os tipos de máquina – n1-stardard-1, n2-standard-2...

[05:23] Vemos quantidade de CPUs, quantidade de memória para cada uma dessas máquinas. Basicamente você pode escolher a máquina, é lógico que quanto mais recurso mais caro vai ser, mas como você vai utilizar por pouco tempo, só durante a exploração e quando deixar processando, pode escolher uma máquina que é um pouco mais potente mesmo para fazer esse trabalho.

[05:46] Mas também não precisa exagerar, talvez possa pegar essa máquina n1 stardard-8, sinta-se à vontade para escolher outra e testar outro tipo de máquina que você gostaria, eu vou escolher a 8 é uma máquina com 8 cpus e 30 GB de memória.

[06:04] Uma máquina bem potente. Eu vou voltar para o cloud Shell e copiar esse nome, e depois do create, antes do nome eu vou passar uma configuração que é machine-type. Eu posso dar Control + V para colar o nome da máquina que escolhi.

[06:30] Então, datalab create --machine-type n1-standard-8 teste-alura, vou dar enter e ele vai começar a instanciar essa VM já preparada para rodar o Datalab. Eu posso escolher a região também, tem regiões no Brasil south-america-east, vou escolher a 41 que é uma região no Brasil.

[07:14] Existe diferença de custos entre região, se você estiver preocupado com questão de custo pode dar uma olhada na documentação, qual região que tem um custo diferente ou se você quer que o dado não saia do Brasil, você pode colocar no Brasil e assim por diante.

[07:27] Seleciono a região 41 e ele vai começar a fazer toda a configuração para que essa máquina funcione. Eu vou deixar rodando aqui ele demora um certo tempo até criar essa máquina, vai me perguntar ainda para colocar senha, vou pausar e assim que tiver a próxima demanda para inserir alguma coisa eu retorno.

[08:00] Ele está pedindo para falar se quer continuar, porque ele vai gerar as chaves de ssh para fazer a conexão na máquina, eu vou colocar Y, ele vai pedir uma senha, eu vou deixar sem senha nessa máquina só de teste para evitar qualquer problema.

[08:22] Dou enter duas vezes e agora ele está terminando de criar essa máquina. Terminou de criar e ele está falando para gente clicar no Web Preview e mudar para porta 8081 - o Datalab está rodando na máquina, o nosso Cloud Shell acessou a máquina rodando acessível via porta 8081 dessa máquina, para isso basta clicar nesse botãozinho visualização da web.

[08:52] Clica em alterar porta e mudar para 8081, alterar e visualizar, assim você vai acessar essa porta e vai ver o que tem lá em uma outra página. Está rodando e nessa página tem o nosso notebook do Datalab.

[09:10] Lembrando que por trás desse notebook, bem parecido com Júpiter, com Colab, eu tenho o meu sistema de arquivos, posso clicar em um novo notebook, ele vai criar um novo notebook.

[09:27] Tem esse notebook com o sistema Linux, com 30 GB de memória RAM, 8 cores de CPU por trás e vai ficar bem potente. Por exemplo, é um notebook que tem aqui em Python 2, pode mudar para Python 3.

[09:43] Posso fazer aqui “import pandas as pd” o primeiro código normalmente de um modelo de exploração, pode fazer print(‘teste’), o notebook assim como vimos outros.

[10:11] “teste”, texto, código Python, mesmo jeito que basicamente parecido com o Júpiter e Colab temos o Datalab com uma máquina por trás. Na próxima aula você vai pegar os dados do BigQuery e trazer para fazer exploração, limpeza dos dados, criação de variáveis e treinar alguns modelos. Até lá!# Google Cloud Platform

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/data-analytics-google-cloud/task/59703/next)

-   [](https://cursos.alura.com.br/suggestions/new/data-analytics-google-cloud/59703/question)

No vídeo, conhecemos o Google Cloud Platform e algumas de suas ferramentas. É muito importante saber escolher a ferramenta mais adequada para cada tarefa.

Considere a situação onde o Google Cloud Platform é utilizado no dia a dia de uma empresa. Em quais das situações abaixo a ferramenta foi escolhida da melhor forma?

Selecione uma alternativa

-   Criação de Data Warehouse com as bases de cadastros de clientes, faturamento e CRM.
    
-   Exploração de dados e criação de visualizações no Google Datalab.
    
-   Utilização do Google BigQuery como banco de dados operacional para uma operação de faturamento.
    
-   Desenvolvimento de uma aplicação web com o Datalab.