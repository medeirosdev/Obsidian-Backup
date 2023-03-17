[00:00] Olá, seja bem-vindo ao segundo curso da série Machine Learning no Marketing Digital, meu nome é Júlio e eu serei o seu instrutor. Nesse curso você vai aprender técnicas avançadas para conseguir prever o comportamento de um usuário no nosso site.

[00:15] Assim como no primeiro curso, você vai continuar utilizando a base de dados da Google Merchandise Store, só que dessa vez vai utilizar a base de dados diretamente onde o Google disponibiliza, dentro do Google BigQuery. O Google BigQuery é a ferramenta de DataWare House do Google.

[00:32] E o Google disponibiliza ambiente para trabalhar com base de dados muito grandes e onde os dados da Google Merchandise Store vem dentro de um data set aberto para quem quer utilizar. No lugar de usar csv que tinha amostra das informações, vamos conectar diretamente no BigQuery e pegar as informações lá.

[00:50] Como o BigQuery está dentro da Google Cloud Platform você vai aprender a utilizar Google Cloud Platform para modelagem. Então você vai fazer a conta no Google Cloud Platform vai conectar no BigQuery e quando for fazer a modelagem sendo que agora tem um volume de dados maior, você vai aprender a utilizar o Datalab para isso.

[01:15] Datalab é a ferramenta de notebook do Google Cloud, com ele você vai conseguir uma máquina mais potente por trás do nosso notebook para trabalhar com a nossa base de dados muito grande. Nesse curso, além de técnicas de machine learning você vai aprender a começar a utilizar o Google Cloud para modelagem.

[01:33] Quando falar sobre técnicas de machine learning vamos aprender algumas coisas novas, primeiro você vai colocar o notebook diretamente com o BigQuery através do Python.

[01:46] Sem ter que fazer nenhuma conexão externa para isso, vai de dentro do notebook chamar as informações que estão dentro do BigQuery, quando chegarmos na parte de preparação dos dados vai trabalhar com a coluna hits; que foi uma coluna que ficou de fora no nosso primeiro curso.

[01:58] Essa coluna tem todas as informações sobre as iterações do usuário com o site e tem muita coisa rica para tentar melhorar nosso modelo, além de várias outras técnicas que você vai aprender também tem a preparação de dados, como feito no primeiro curso.

[02:14] Uma coisa interessante que faremos é mudar a pergunta do negócio e não só tentar prever quanto que o usuário vai gastar, mas ver como que o nosso modelo se comporta quando tenta prever se o usuário vai gastar ou não ao invés de quanto ele vai gastar. No final você vai aprender uma nova técnica que vai ser o XGBoost e vai ver se o nosso modelo melhora com essa técnica de gradient boosting, diferente do que você vinha utilizando.

[02:40] Lembrando, se você também não trabalha no marketing digital, esse curso estará recheado de ferramentas que você pode usar em diversos outros cases.

[02:50] Esse é o segundo curso da série, então aconselho você a fazer o primeiro curso e estar com os requisitos de Python para melhor aproveitar o curso. Temos bastante coisa para ver, o material está muito legal, então vamos para o curso!

[00:00] Agora vamos configurar nossa conta do Google Cloud, para isso eu vou acessar o console.cloud.google.com, e essa a tela inicial do Google Cloud, nela tem todas as ferramentas que Google disponibiliza por meio dessa plataforma.

[00:22] Isso se faz por ferramentas de computação, ferramentas de armazenamento, ferramentas de rede, Big Data, inteligência artificial e assim por diante. Para começarmos a utilizar essas ferramentas, vamos precisar logar com e-mail Gmail e você pode escolher o seu e-mail para logar.

[00:45] Vou colocar a minha senha e pronto estou logado dentro do Google Cloud, vocês notaram que loguei dentro do Google e começo a navegar dentro da ferramenta, sem ter de pagar nada.

[01:19] Então, fazer esse primeiro login e até alguns recursos vão ser gratuitos dentro da plataforma do Google Cloud, outros recursos não serão gratuitos, mas tem um porém, Google dá U$D300 gratuitos quando você ativa a avaliação gratuita.

[01:35] Então você vai clicar aqui em ativar avaliação gratuita para receber esses 300 dólares e fazer algumas coisas a mais com esses créditos que você vai receber. Vou clicar em ativar e eu vou seguir os passos para ativar esse faturamento, concordar e continuar, vou selecionar que tipo de pessoa eu sou, uma pessoa física.

[02:11] Vou colocar o meu CPF, data de nascimento, nome, linha, endereço e assim por diante, vou preencher essas informações, no final eu tenho que colocar o meu cartão, você não terá nenhuma cobrança no seu cartão enquanto você tiver os 300 dólares.

[02:31] Durante o curso vou ensinar também como você desativa o faturamento, como bloqueia o projeto para que você não tenha nenhuma cobrança indevida no seu cartão. Você terá de colocar o cartão para ativar o faturamento, mas enquanto você tiver os U$D300 ativos não terá nenhuma cobrança.

[02:50] Vou pausar o vídeo, vou colocar as minhas informações, vou passar para o próximo passo. Já terminei de colocar as informações do meu cartão, voltei para minha tela aqui do console e agora eu posso verificar quanto que eu tenho de crédito na minha conta.

[03:10] Todas as informações de faturamento estão disponíveis no menu esquerdo, faturamento, você pode acessar aqui e ver quanto de crédito que tem, o valor que você receber vai depender do valor da cotação do dólar no dia porque são 300 dólares que você recebe esse valor é convertido para reais.

[03:28] Lembrando que também qualquer cobrança que você tiver do Google Cloud vai ser em reais, para evitar qualquer problema com cobranças no cartão que você não estava esperando é muito importante estar atento a essa parte, conta de faturamento.

[03:46] Todos os projetos linkados essa conta de faturamento aparecem aqui, se por acaso você terminar esse curso no meio ou se você terminar esse curso e fizer outros e parar de mexer com a conta do Google Cloud é importante que você desative o faturamento.

[04:03] Assim evita que se esses créditos acabem e as cobranças sejam feitas automaticamente no cartão cadastrado. Lembre-se de que se acabarem os créditos a cobrança é feita automaticamente no cartão.

[04:16] Durante esse curso pode ficar tranquilo que você vai usar muito pouco e vai sobrar crédito, mas por via das dúvidas é melhor se você deixar o curso ou se você por acaso vier a fazer outros projetos ficar atento quanto você tem de crédito ainda.

[04:35] Se os créditos estiverem acabando desative o faturamento ou melhor ainda excluam os projetos para evitar qualquer custo adicional. Estamos com a nossa conta cadastrada e nos próximos passos vamos cadastrar as ferramentas para desenvolver esse modelo, até lá!

Neste curso usamos o Google Cloud Platform como plataforma de cloud para desenvolvimento, mas no mercado atual temos várias plataformas disponíveis – algumas com ampla variedade de ferramentas e outras mais focadas em um mercado específico. O mais legal é que a maioria fornece a possibilidade de começar a utilização sem nenhum custo.

Veja alguns exemplos de plataformas cloud para desenvolvimento:

-   [Azure](https://azure.microsoft.com/pt-br/)
-   [AWS](https://aws.amazon.com/pt/)
-   [Digital Ocean](https://www.digitalocean.com/)
-   [Heroku](https://www.heroku.com/)
-   [OpenShift](https://www.openshift.com/)

É muito importante escolher bem o ambiente de desenvolvimento entendo as necessidades do negócio, o tamanho da base, as habilidades técnicas e os recursos financeiros disponíveis.