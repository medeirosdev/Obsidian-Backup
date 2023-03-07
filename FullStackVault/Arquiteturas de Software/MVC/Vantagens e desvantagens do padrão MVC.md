
Como todo padrão de desenvolvimento de software, existem vantagens e desvantagens em utilizá-los. O padrão [[MVC]]oferece principalmente vantagens, mas pode também considerar-se que possui algumas desvantagens. Vamos relembrar algumas vantagens em desenvolver utilizando o padrão MVC:

-   Separação muito clara entre as camadas de visualização e regras de negócios;
-   Manutenção do sistema se torna mais fácil;
-   Reaproveitamento de código, principalmente da camada de modelo, que pode ser reutilizada em outros projetos;
-   As alterações na camada de visualização não afetam as regras de negócios já implementadas na camada de modelo;
-   Permite o desenvolvimento, testes e manutenção de forma isolada entre as camadas;
-   O projeto passa a ter uma melhor organização em sua arquitetura;
-   Torna o entendimento do projeto mais fácil para novos programadores que não participaram de sua criação.
-   As desvantagens são poucas, mas alguns desenvolvedores acabam não usando o padrão MVC por conta delas, veja algumas:
-   Em sistemas de baixa complexidade, o MVC pode criar uma complexidade desnecessária;
-   Exige muita disciplina dos desenvolvedores em relação à separação das camadas;
-   Requer um tempo maior para modelar o sistema.

Sempre que um sistema for desenvolvido, terá com certeza a necessidade de manutenção como melhorias ou correção de erros e também pode necessitar de varias atualizações. Embora alguns programadores achem que o padrão MVC é muito custoso para ser aplicado, ele se torna muito mais fácil quando há necessidades de executar manutenções e atualizações, já que possui sua estrutura bem definida e suas camadas separadas de forma a diminuir a dependência entre elas.