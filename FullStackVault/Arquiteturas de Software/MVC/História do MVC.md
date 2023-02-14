[[MVC]]
O artigo apresenta o que é um padrão de projeto e foca seu estudo no modelo Model-View-Controller citando as vantagens e desvantagens na sua utilização, exemplificando o uso correto das três camadas do **padrão MVC** numa aplicação desenvolvida para desktop – utilizando a API Swing – com base no modelo MVC, comentada e disponibilizada para o leitor.

A implementação de cada uma destas camadas proporciona aos desenvolvedores uma manutenção mais fácil e o possível reaproveitamento de classes e partes do projeto em projetos futuros.

O Engenheiro Civil Christopher Alexander criou o que se considera o primeiro padrão de projeto em meados da década de 70. É considerado um padrão de projeto uma solução já testada e documentada que resolva um problema específico em projetos distintos. Através do trabalho de Alexander, profissionais da área de desenvolvimento de software utilizaram tais conceitos para iniciar as primeiras documentações de padrões de projetos, tornando-as acessíveis para toda a área de desenvolvimento.

O então funcionário da corporação Xerox PARC, Trygve Reenskaug, iniciou em 1979 o que seria o nascimento do padrão de projeto MVC. A implementação original foi descrita no artigo "Applications Programming in Smalltalk-80: How to use Model-View-Controller". A ideia de Reenskaug gerou um padrão de arquitetura cujo objetivo é separar o projeto em três camadas independentes, que são o modelo, a visão e o controlador. Essa separação de camadas ajuda na redução de acoplamento e promove o aumento de coesão nas classes do projeto. Assim, quando o modelo MVC é utilizado, pode facilitar a manutenção do código e sua reutilização em outros projetos.

A seguir temos algumas vantagens quando utilizamos um ou mais padrões de projeto em desenvolvimento de software:

Baixo acoplamento: é o grau em que uma classe conhece a outra. Se o conhecimento da classe A sobre a classe B for através de sua interface, temos um baixo acoplamento, e isso é bom. Por outro lado, se a classe A depende de membros da classe B que não fazem parte da interface de B, então temos um alto acoplamento, o que é ruim.

Coesão: quando temos uma classe elaborada com um único e bem focado propósito, dizemos que ela tem alta coesão, e isso é bom. Quando temos uma classe com propósitos que não pertencem apenas a ela, temos uma baixa coesão, o que é ruim.


Documento Original
![[mvc (1).pdf]]