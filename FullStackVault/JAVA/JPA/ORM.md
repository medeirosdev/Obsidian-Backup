**ORM (Object Relational Mapper) é uma técnica de mapeamento objeto relacional que permite fazer uma relação dos objetos com os dados que os mesmos representam**. Ultimamente tem sido muito utilizada e vem crescendo bastante nos últimos anos.

Este crescimento tem se dado principalmente pelo fato de muitos desenvolvedores não se sentirem a vontade em [escrever código SQL](https://www.devmedia.com.br/principais-instrucoes-em-sql/37262 "Principais Instruções em SQL") e pela produtividade que esta técnica nos proporciona. Existem ótimos ORM´s como [Hibernate](https://www.devmedia.com.br/guia/hibernate/38312 "Guia de Referência Hibernate"), [NHibernate](https://www.devmedia.com.br/introducao-ao-nhibernate-framework-para-mapeamento-objeto-relacional/28671 "Introdução ao NHibernate"), [Entity Framework](https://www.devmedia.com.br/entity-framework-tutorial/27764 "Entity Framework Tutorial") e etc.
Tudo começa como mostrado na **Figura 1.** Existem dois mundos: o relacional e o orientado a objetos.

No mundo relacional prevalecem princípios matemáticos com a finalidade de armazenar e gerenciar corretamente os dados, de forma segura e se trabalha com a linguagem SQL que é utilizada para dizer o banco de dados “O QUE?” fazer e não como fazer.

Já no mundo orientado a objetos trabalhamos com classes e métodos, ou seja, trabalhamos fundamentados na engenharia de software e seus princípios que nos dizem “COMO” fazer. O ORM é justamente, a ponte entre estes dois mundos, ou seja, é ele quem vai permitir que você armazene os seus objetos no banco de dados.

Para isto precisamos fazer um mapeamento dos seus objetos para as tabelas do banco de dados.

![Como o ORM trabalha](https://www.devmedia.com.br/imagens/articles/233575/ORM-Overview.png)

**Figura 2**. Como o ORM trabalha

A **Figura 2** nos traz uma ideia de como o ORM trabalha. Ele faz o mapeamento da sua classe para o banco de dados e cada ORM tem suas particularidades para gerar o [SQL](https://www.devmedia.com.br/guia/guia-completo-de-sql/38314 "Guia Completo de SQL") referente a inserção do objeto que corresponde a uma tabela no banco de dados e realizar a operação. Utilizando um ORM, também se ganha produtividade, pois deixa-se de escrever os [comando SQL](https://www.devmedia.com.br/comandos-basicos-em-sql-insert-update-delete-e-select/37170 "INSERT, UPDATE, DELETE e SELECT") para deixar que o próprio ORM, faça isto por você.

Bom pessoal, chegamos ao fim deste nosso artigo. Espero ter ajudado e contribuído de alguma forma para o crescimento profissional de cada leitor. Um abraço e até a próxima.