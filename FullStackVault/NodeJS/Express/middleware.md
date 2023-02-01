## O que é middleware?
[[Express]]
O middleware é um software que diferentes aplicações usam para se comunicar umas com as outras. Ele oferece funcionalidade para conectar aplicações de modo inteligente e eficiente, para que você possa inovar mais rapidamente. O middleware atua como uma ponte entre diversas tecnologias, ferramentas e bancos de dados para integrá-los perfeitamente em um único sistema. O sistema único oferece um serviço unificado para seus usuários. Por exemplo, uma aplicação de frontend do Windows envia e recebe dados de um servidor de backend do Linux, mas os usuários da aplicação desconhecem a diferença.

## Por que o middleware é importante?

O middleware começou como uma ponte entre novas aplicações e sistemas herdados antes de ganhar popularidade na década de 1980. Os desenvolvedores inicialmente o usavam para integrar novos programas com sistemas anteriores sem reescrever o código. O middleware se tornou uma importante ferramenta de comunicação e gerenciamento de dados em sistemas distribuídos.

Os desenvolvedores usam middleware para dar suporte ao desenvolvimento de aplicações e simplificar os processos de design. Assim, eles ficam livres para se concentrar na lógica e nos recursos de negócios em vez da conectividade entre diferentes componentes de software. Sem o middleware, seria necessário criar um módulo de troca de dados para cada componente de software que se conecta à aplicação. Isso é desafiador, porque as aplicações modernas consistem em vários microsserviços ou pequenos componentes de software que interagem entre si. 

## Quais são os casos de uso do middleware?

Os casos de uso mais comuns do middleware são os seguintes:

### Desenvolvimento de jogos

Desenvolvedores de jogos usam middleware como mecanismo de jogos. Para que um jogo funcione, o software deve se comunicar com vários servidores de imagem, áudio e vídeo, além de sistemas de comunicação. O mecanismo de jogos facilita essa comunicação e torna o desenvolvimento de jogos mais eficiente.

### Eletrônica

Engenheiros eletrônicos usam middleware para integrar vários tipos de sensor a seus controladores. A camada do middleware permite que os sensores se comuniquem com o controlador por um framework comum de sistema de mensagens. 

### Desenvolvimento de software

Desenvolvedores de software usam middleware para integrar diferentes componentes de software a outras aplicações. O middleware oferece um padrão de [interface de programação de aplicações (API)](https://aws.amazon.com/what-is/api/) para gerenciar a entrada e a saída de dados necessárias do componente. A ligação interna com o componente não fica visível para o usuário. Os desenvolvedores usam as APIs para solicitar os serviços necessários dos componentes de software. 

### Transmissão de dados

Aplicações de software usam middleware para enviar e receber fluxos de dados de forma confiável. Os fluxos de dados são uma transmissão de alta velocidade de dados contínuos. Eles são importantes para transmissões confiáveis de vídeo e áudio.

### Aplicações distribuídas

Aplicações distribuídas são programas de software executados em diferentes computadores em uma rede. Elas geralmente consistem em aplicações frontend e backend. Aplicações frontend são softwares que você usa em um computador ou dispositivo móvel, como uma aplicação de mídia social. Por outro lado, aplicações de backend são programas de software que lidam com tarefas de processamento de dados, lógica de negócios e gerenciamento de recursos. O middleware se comunica entre as aplicações frontend e backend para que a aplicação distribuída funcione sem problemas.

## O que é arquitetura de middleware?

A arquitetura de software de middleware consiste em vários componentes que se comunicam para criar um pipeline de dados. Os dados migram de uma aplicação de conexão para outra por meio do middleware. O middleware processa os dados para compatibilidade. Os componentes comuns de software de middleware são os seguintes:

### Console de gerenciamento

O console de gerenciamento oferece aos desenvolvedores de software uma visão geral das atividades, regras de software e configurações do sistema de middleware.

### Interface do cliente

A interface do cliente é a parte externa do software de middleware que se comunica com as aplicações. Os desenvolvedores usam funções oferecidas pela interface do cliente para interagir com outras aplicações, bancos de dados ou outros microsserviços.

### Interface interna do middleware

A interface interna do middleware conecta o software, unindo os vários componentes. Os componentes de middleware usam a interface interna para funcionar de forma coesa com seu próprio protocolo. 

### Interface da plataforma

A interface do middleware garante que o programa de middleware seja compatível com várias plataformas. Ela contém componentes de software que funcionam com diferentes tipos de sistema operacional. 

### Gerenciador de contrato

O gerenciador de contrato define as regras para troca de dados no sistema de middleware. Também garante que as aplicações cumpram as regras ao enviar dados com o middleware. Ele envia um alerta, ou uma exceção, para a aplicação quando ela viola regras específicas. Por exemplo, o gerente de contrato retornará uma exceção se a aplicação enviar um número quando uma palavra for esperada. 

### Gerenciador de sessões

O gerenciador de sessões configura um canal de comunicação seguro entre as aplicações e o middleware. Ele garante que a comunicação flua perfeitamente e armazena registros de atividade de dados para relatórios. 

### Gerenciador de banco de dados

Alguns tipos de middleware também incluem um gerenciador de banco de dados. O gerenciador de banco de dados é responsável pela integração com diferentes tipos de banco de dados, conforme necessário. 

### Monitor de tempo de execução

O monitor de tempo de execução oferece monitoramento contínuo de movimentos de dados no middleware. Ele detecta e relata atividades incomuns aos desenvolvedores. 

## Como o middleware funciona?

O middleware abstrai o processo de comunicação subjacente entre componentes. Isso significa que a aplicação frontend se comunica apenas com o middleware e não precisa aprender a linguagem de outros componentes de software de backend. 

### Framework de sistema de mensagens

Um framework de sistema de mensagens facilita a troca de dados entre aplicações frontend e backend. Alguns frameworks comuns são:

-   JavaScript Object Notation (JSON)
-   Transferência Representacional de Estado (REST API)
-   Extensible Markup Language (XML)
-   Serviços da Web
-   Protocolo Simples de Acesso a Objetos (SOAP) 

Frameworks de sistemas de mensagens fornecem uma interface de comunicação comum para aplicações em diferentes plataformas operacionais e linguagens. As aplicações gravam e leem dados em um formato padronizado fornecido pelo framework do sistema de mensagens. 

### Exemplo de middleware

Por exemplo, um servidor web é um middleware que conecta sites ao banco de dados backend. Quando você envia um formulário em um site, seu computador envia a solicitação em XML ou JSON para o servidor da Web. Em seguida, o servidor da Web executa a lógica de negócios com base na solicitação, recupera informações de bancos de dados ou se comunica com outros microsserviços usando protocolos diferentes.

### Outras funções do middleware

Além de ser um intermediário entre aplicações de software, os programas de middleware também fazem o seguinte:

-   Fornecem um canal de comunicação seguro entre aplicações distribuídas, para que os sites enviem informações confidenciais com segurança para aplicações backend. 
-   Gerenciam o fluxo de tráfego e evitam sobrecarregar uma aplicação ou um servidor de arquivos específico.
-   Automatizam e personalizam as respostas à solicitação. Por exemplo, o middleware classifica e filtra os resultados antes de enviá-los para a aplicação frontend.

## O que é middleware de plataforma?

O middleware de plataforma permite o desenvolvimento de aplicações, fornecendo um sistema de ferramentas e recursos gerenciados. Desenvolvedores usam middleware de plataforma para compartilhar ou transferir recursos entre aplicações. A seguir, veja alguns exemplos de recursos de middleware de plataforma:

### Ambientes de tempo de execução

Um ambiente de tempo de execução é como um pequeno sistema operacional que permite que um programa de software seja executado. Por exemplo, as aplicações Java devem ser executadas no ambiente do tempo de execução Java. Desenvolvedores podem usar o [AWS Lambda](https://aws.amazon.com/lambda/) para configurar um ambiente de tempo de execução para qualquer linguagem de programação. 

### Servidores da Web

Um servidor da Web é um programa de computador que recebe, processa e responde a solicitações de sites. Os desenvolvedores da Web usam o [Amazon Lightsail](https://aws.amazon.com/lightsail/) para hospedar e gerenciar servidores Web para aplicações simples. 

### Sistemas de gerenciamento de conteúdo

O sistema de gerenciamento de conteúdo é um software que cria, modifica, armazena e publica informações digitais. Por exemplo, o WordPress é um sistema de gerenciamento de conteúdo de código aberto para a criação de sites. 

### Contêineres

Um contêiner é um pacote pronto para implantação dos códigos da aplicação e dos recursos necessários. Desenvolvedores usam o [Amazon Elastic Container Service (Amazon ECS)](https://aws.amazon.com/ecs/) para implantar, gerenciar e escalar aplicações em contêiner. 

## O que é middleware de plataforma?

O middleware de plataforma permite o desenvolvimento de aplicações, fornecendo um sistema de ferramentas e recursos gerenciados. Desenvolvedores usam middleware de plataforma para compartilhar ou transferir recursos entre aplicações. A seguir, veja alguns exemplos de recursos de middleware de plataforma:

### Ambientes de tempo de execução

Um ambiente de tempo de execução é como um pequeno sistema operacional que permite que um programa de software seja executado. Por exemplo, as aplicações Java devem ser executadas no ambiente do tempo de execução Java. Desenvolvedores podem usar o [AWS Lambda](https://aws.amazon.com/lambda/) para configurar um ambiente de tempo de execução para qualquer linguagem de programação. 

### Servidores da Web

Um servidor da Web é um programa de computador que recebe, processa e responde a solicitações de sites. Os desenvolvedores da Web usam o [Amazon Lightsail](https://aws.amazon.com/lightsail/) para hospedar e gerenciar servidores Web para aplicações simples. 

### Sistemas de gerenciamento de conteúdo

O sistema de gerenciamento de conteúdo é um software que cria, modifica, armazena e publica informações digitais. Por exemplo, o WordPress é um sistema de gerenciamento de conteúdo de código aberto para a criação de sites. 

### Contêineres

Um contêiner é um pacote pronto para implantação dos códigos da aplicação e dos recursos necessários. Desenvolvedores usam o [Amazon Elastic Container Service (Amazon ECS)](https://aws.amazon.com/ecs/) para implantar, gerenciar e escalar aplicações em contêiner. 

## O que é middleware na computação em nuvem?

A computação em nuvem envolve a criação e a implantação de aplicações nativas da nuvem em diferentes infraestruturas. Os desenvolvedores usam middleware para acessar recursos de nuvem sem serem sobrecarregados pela complexidade de gerenciar as infraestruturas. Os desenvolvedores implantam aplicações em nuvem em contêineres em uma hospedagem baseada na nuvem escalável, como o [Amazon Elastic Compute Cloud (Amazon EC2)](https://aws.amazon.com/ec2/).

## Como a AWS oferece suporte à tecnologia de middleware?

A [integração de aplicações na AWS](https://aws.amazon.com/products/application-integration/) é um conjunto de serviços que são uma alternativa acessível ao middleware convencional para computação em nuvem. Os desenvolvedores usam os serviços para se comunicar entre componentes desacoplados em microsserviços, sistemas distribuídos e aplicações sem servidor. Por exemplo:

-   O [AWS Step Functions](https://aws.amazon.com/step-functions/) é um serviço de fluxo de trabalho visual que permite aos desenvolvedores criar aplicações distribuídas, automatizar processos de TI e negócios e criar pipelines de dados e machine learning com produtos da AWS.
-   O [Amazon Simple Notiﬁcation Service (Amazon SNS)](https://aws.amazon.com/sns/) é uma alternativa ao middleware orientado por mensagens. Ele fornece serviços de mensagens para aplicações.
-   O [Amazon EventBridge](https://aws.amazon.com/eventbridge/) é um barramento de eventos com tecnologia sem servidor que os desenvolvedores usam para integrar aplicações em nuvem aos produtos da AWS.  

Comece a usar o middleware na AWS [criando uma conta da AWS](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html?nc2=h_ct&src=header_signup) hoje mesmo.