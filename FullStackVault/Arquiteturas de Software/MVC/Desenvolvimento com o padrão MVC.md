[[MVC]]

Utilizando como base para o desenvolvimento de um projeto com o padrão MVC, o sistema financeiro citado anteriormente se aplica como um bom exemplo. Neste sistema teríamos uma interface gráfica para a entrada dos dados referentes ao cálculo e também uma opção que seleciona qual o tipo de cálculo o usuário irá executar. Também é necessário um botão que irá confirmar o pedido da execução do cálculo pelo usuário. O resultado encontrado deverá ser apresentado para o usuário e também ser salvo em uma base de dados. A partir destas informações, vamos primeiramente criar tal sistema utilizando o padrão de projeto MVC em uma plataforma Desktop.

### Sistema desktop utilizando o padrão MVC

A arquitetura básica do projeto terá três pacotes principais, sendo que cada pacote representa uma camada específica do padrão MVC. Inicialmente, para o leitor, esta divisão em pacotes tornará mais fácil a distinção entre as camadas.

A camada Model será definida pelo pacote ejm.appdesktop.model. Este pacote terá ainda mais três pacotes internos, sendo responsáveis por organizar as classes da aplicação que devem fazer parte apenas da camada de modelo, ou seja, a camada de negócios. A separação de classes entre pacotes é considerada uma boa prática porque reúne em um mesmo pacote classes com objetivos em comum.

O pacote ejm.appdesktop.model.entity terá a classe de entidade que representa uma tabela no banco de dados, suas referências e dependências. Sempre que for preciso criar uma nova classe referente a uma tabela do banco de dados, essa classe deverá ser criada dentro deste pacote.

Entidade ou Tabela: onde todos os dados de um banco de dados relacional são armazenados.

Bean: uma classe JavaBean, também conhecida como POJO (Plain Old Java Objects), possui um construtor, atributos privados e os métodos getters e setters públicos.

Classe de Entidade: é uma classe do tipo Bean que faz referência a uma entidade do banco de dados, e cada instância desta entidade representa uma linha (registro ou tupla) na tabela (entidade).

Teremos também o pacote ejm.appdesktop.model.dao, que representará as classes que possuem relação direta com as ações de CRUD utilizando o padrão DAO. Este é um padrão para persistência de dados que permite separar regras de negócio das regras de acesso a banco de dados. Em uma aplicação que utilize a arquitetura MVC, todas as funcionalidades de bancos de dados, tais como obter a conexão e as operações de CRUD, devem ser feitas por classes de DAO. Sempre que existir uma entidade deveremos implementar uma classe no pacote dao que a represente, assim, deixamos as regras de operações CRUD de cada entidade em uma classe específica do tipo DAO.

O último pacote referente à camada model a ser criado é o ejm.appdesktop.model.service, que possui classes com as regras de negócio da aplicação. É considerada uma boa prática ter uma classe do tipo service para cada entidade ou dao do projeto, podendo diminuir assim, a dependência das classes de entidades em relação às classes de CRUD, nos proporcionando maior facilidade de reuso e um código mais limpo. Veja que cada projeto possui objetivos diferentes, e deste modo as regras de negócios podem ser diferentes também. Por exemplo: uma classe do tipo Pessoa possui basicamente um construtor e métodos getters e setters. Caso uma instância da classe PessoaDao seja criada diretamente na classe Pessoa, existirá um alto grau de acoplamento entre Pessoa e PessoaDao. Com isso, se a classe Pessoa fosse reutilizada em um novo projeto que não possui acesso a banco de dados, haveria também a necessidade da classe PessoaDao neste novo projeto, isto porque, há uma instância de PessoaDao na classe Pessoa. Quando uma classe do tipo service é utilizada, esse acoplamento entre a entidade e a classe dao não se faz necessário. Isto se torna responsabilidade da classe service.

Neste momento vale ressaltar que algumas classes e métodos citados no artigo poderão não estar disponíveis nas listagens de códigos devido o foco ser o padrão MVC, porém o projeto apresentado estará acessível para download no site da revista em sua forma completa.

O objetivo do projeto é o desenvolvimento de um sistema financeiro que execute o cálculo de juros. Para isso, será criada uma classe de entidade que represente os atributos contidos nesta operação. Esta classe de entidade representará a tabela no banco de dados chamada Calculos, a qual armazena o resultado dos cálculos executados no sistema. Esta classe Calculo será implementada no pacote ejm.appdesktop.model.entity e pode ser visualizada na **Listagem 1**.

