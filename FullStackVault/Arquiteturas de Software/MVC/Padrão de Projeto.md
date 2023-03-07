[[MVC]]

Alexander descreveu um padrão como sendo um problema que se repete inúmeras vezes em um mesmo contexto e que contenha uma solução para resolve-lo de tal modo que esta solução seja utilizada em diversas situações. O termo padrões de projeto ou , descreve soluções para problemas recorrentes no desenvolvimento de sistemas de software orientados a objetos. O Factory é um destes padrões e é baseado em uma interface para criar objetos e deixar que suas subclasses decidam que classe instanciar. Deste modo, utiliza-se o conceito de fábrica de objetos quando um objeto é utilizado para a criação de outros objetos. Algo assim foi implementado no Framework Hibernate para a criação de uma espécie de fábrica de sessões, ou seja, na criação de uma única SessionFactory teríamos acesso a vários objetos do tipo Session.

Padrões de projeto são estabelecidos por um nome, problema, solução e consequências. O nome deve ser responsável por descrever o problema, a solução e as consequências. Quando alguém na equipe de um projeto se refere a um padrão pelo nome, os demais membros da equipe devem relacionar este nome com um problema encontrado, a solução e as consequências na utilização de tal padrão. Encontrar um nome para um novo padrão é considerada uma etapa difícil, já que o nome deve proporcionar a ideia para a qual o padrão foi criado. O problema descreve quando devemos aplicar o padrão, qual o problema a que se refere e seu contexto. A solução descreve os elementos que fazem parte da implementação, as relações entre eles, suas responsabilidades e colaborações. Uma solução não deve descrever uma implementação concreta em particular e sim proporcionar uma descrição abstrata de um problema e como resolvê-lo. As consequências são os resultados, vantagens e desvantagens ao utilizar o padrão e são importantes para avaliar as alternativas descritas bem como proporcionar uma ideia de custos e benefícios ao aplicá-lo.

Um exemplo existente e muito utilizado de padrão é o Data Access Object, ou simplesmente DAO. Foi uma solução encontrada para resolver problemas referentes à separação das classes de acesso a banco de dados das classes responsáveis pelas regras de negócio.

Já o **conceito principal do modelo MVC é utilizar uma solução já definida para separar partes distintas do projeto reduzindo suas dependências ao máximo**.

Desenvolver uma aplicação utilizando algum padrão de projeto pode trazer alguns dos seguintes benefícios:

-   Aumento de produtividade;
-   Uniformidade na estrutura do software;
-   Redução de complexidade no código;
-   As aplicações ficam mais fácies de manter;
-   Facilita a documentação;
-   Estabelece um vocabulário comum de projeto entre desenvolvedores;
-   Permite a reutilização de módulos do sistema em outros sistemas;
-   É considerada uma boa prática utilizar um conjunto de padrões para resolver problemas maiores que, sozinhos, não conseguiriam;
-   Ajuda a construir softwares confiáveis com arquiteturas testadas;
-   Reduz o tempo de desenvolvimento de um projeto.

Nos dias atuais existem diversos padrões e cada um possui uma função bem específica dentro da estrutura do projeto. Deste modo, podemos utilizar em um mesmo projeto de software mais de um padrão simultaneamente. Poderíamos fazer uso simultâneo, por exemplo:

-   Do Factory para criar uma fábrica de sessões com o banco de dados;
-   O DAO para separar as classes de CRUD das regras de negócios e
-   O **MVC para dividir e diminuir a dependência entre módulos do sistema**.

CRUD: A sigla tem origem na língua inglesa para Create, Retrieve, Update e Delete, em português teria o significado de Criar, Recuperar, Atualizar e Excluir. São as quatro operações básicas em um banco de dados.