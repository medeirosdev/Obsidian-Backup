[[MVC]]
**O MVC é utilizado em muitos projetos devido a arquitetura que possui**, o que possibilita a divisão do projeto em camadas muito bem definidas. Cada uma delas, o Model, o Controller e a View, executa o que lhe é definido e nada mais do que isso.

A **utilização do padrão MVC** traz como benefício o isolamento das regras de negócios da lógica de apresentação, que é a interface com o usuário. Isto possibilita a existência de várias interfaces com o usuário que podem ser modificadas sem a necessidade de alterar as regras de negócios, proporcionando muito mais flexibilidade e oportunidades de reuso das classes.

Uma das características de um padrão de projeto é poder aplicá-lo em sistemas distintos. **O padrão MVC pode ser utilizado em vários tipos de projetos** como, por exemplo, desktop, web e mobile.

A comunicação entre interfaces e regras de negócios é definida através de um controlador, que separa as camadas. Quando um evento é executado na interface gráfica, como um clique em um botão, a interface se comunicará com o controlador, que por sua vez se comunica com as regras de negócios.

Imagine uma aplicação financeira que realiza cálculos de diversos tipos, como os de juros. Você pode inserir valores para os cálculos e também escolher que tipo de cálculo será realizado. Isto tudo é feito pela interface gráfica, que para o **modelo MVC é conhecida como View**. No entanto, o sistema precisa saber que você está requisitando um cálculo, e para isso, terá um botão no sistema que quando clicado gera um evento.

Este evento pode ser uma requisição para um tipo de cálculo específico como o de juros simples ou juros compostos. Fazem parte da requisição os valores digitados no formulário e a seleção do tipo de cálculo que o usuário quer executar sobre o valor informado. O evento do botão é como um pedido a um intermediador (Controller) que prepara as informações para então enviá-las para o cálculo. O controlador é o único no sistema que conhece o responsável pela execução do cálculo, neste caso, a camada que contém as regras de negócios. Esta operação matemática será realizada pelo Model assim que ele receber um pedido do Controller.

O Model realiza a operação matemática e retorna o valor calculado para o Controller, que também é o único que possui conhecimento da existência da camada de visualização. Tendo o valor em mãos, o intermediador o repassa para a interface gráfica que exibirá para o usuário. Caso esta operação deva ser registrada em uma base de dados, o Model se encarrega também desta tarefa.

![[Pasted image 20230207184525.png]]
Analisando a **Figura 1** podemos ver que o processo de fluxo do MVC é muito simples. O usuário interage com a interface gráfica que é a camada View. A interface gráfica interage com um intermediador que é o Controller, e este interage com o Model que executa as regras de negócios do sistema.

Mas por que usar a camada Controller? Não seria possível fazer a comunicação direta entre View e Model?

Sim, seria possível, mas esta prática não é recomendada por algumas razões. A ligação direta entre as duas camadas acarretaria para o código da interface duas responsabilidades, gerenciar a interface e também lidar com a lógica da camada Model. Isto aumentaria o acoplamento entre as duas camadas, deixando-as muito dependentes e assim, não seria possível a reutilização da interface com outro Model sem que fosse preciso modificar a camada de visualização.

Quando se utiliza a camada Controller, a dependência entre o Model e a View são reduzidas ao máximo, possibilitando um projeto mais flexível, expansível e facilita futuras alterações.