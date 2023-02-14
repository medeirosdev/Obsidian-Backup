- São Bancos de dados focados em Documentos
- A Modelagem de dados com relacionamentos é opcional
- Não utilizamos queries e sim métodos de classes para trabalhar com os dados
- As tabelas não existem, temos as collections.
- MongoDB é um banco NoSQL

# O que são bancos de dados NoSQL?

Bancos de dados NoSQL são criados para modelos de dados específicos e têm esquemas flexíveis para a criação de aplicativos modernos. Os bancos de dados NoSQL são amplamente reconhecidos por sua facilidade de desenvolvimento, funcionalidade e performance em escala. Esta página inclui recursos para ajudar você a compreender melhor os bancos de dados NoSQL e a começar a usá-lo.

# Como funciona um banco de dados NoSQL (não relacional)?

Os bancos de dados NoSQL usam uma variedade de modelos de dados para acessar e gerenciar os dados. Esses tipos de banco de dados são otimizados especificamente para aplicativos que exigem modelos de grande volume de dados, baixa latência e flexibilidade. Esses requisitos são atendidos mediante o relaxamento de algumas restrições de consistência de dados dos outros bancos.

Considere o exemplo de modelagem do esquema para um banco de dados simples de livros:

-   Em um banco de dados relacional, um registro de livro é normalmente disfarçado (ou “normalizado”) e armazenado em tabelas separadas, e os relacionamentos são definidos por restrições de chave primária e externa. Neste exemplo, a tabela **Livros** têm colunas para **ISBN**, **Título do livro** e **Número da edição**, a tabela **Autores** têm colunas para **AuthorID** e **Nome do autor** e, finalmente, a tabela **Author-ISBN** tem colunas para **AuthorID** e **ISBN**. O modelo relacional é projetado para permitir que o banco de dados imponha a integridade referencial entre as tabelas no banco de dados, normalizadas para reduzir a redundância e geralmente otimizadas para armazenamento.  
    

-   Em um banco de dados NoSQL, um registro de livro é normalmente armazenado como um documento [JSON](http://json.org/). Para cada livro, o item, o **ISBN**, o **Título do livro**, o **Número de edição**, o **Nome do autor** e o **AuthorID** são armazenados como atributos em um único documento. Neste modelo, os dados são otimizados para desenvolvimento intuitivo e escalabilidade horizontal.  
    

# Por que você deve usar um banco de dados NoSQL?

Os bancos de dados NoSQL são ideais para muitos aplicativos modernos, como dispositivos móveis, Web e jogos, que exigem bancos de dados flexíveis, escaláveis, de alta performance e altamente funcionais para proporcionar ótimas experiências aos usuários.

-   **Flexibilidade:** os bancos de dados NoSQL geralmente fornecem esquemas flexíveis que permitem um desenvolvimento mais rápido e iterativo. O modelo de dados flexível torna os bancos de dados NoSQL ideais para dados semiestruturados e não estruturados.
-   **Escalabilidade:** os bancos de dados NoSQL geralmente são projetados para serem escalados horizontalmente usando clusters distribuídos de hardware, em vez de escalá-los verticalmente adicionando servidores caros e robustos. Alguns provedores de nuvem lidam com essas operações nos bastidores como um serviço totalmente gerenciado.
-   **Alta performance:** o banco de dados NoSQL é otimizado para modelos de dados específicos e padrões de acesso que permitem maior performance do que quando se tenta realizar uma funcionalidade semelhante com bancos de dados relacionais.
-   **Altamente funcional:** os bancos de dados NoSQL fornecem APIs e tipos de dados altamente funcionais criados especificamente para cada um de seus respectivos modelos de dados.
# Bancos de dados SQL (relacional) vs. NoSQL (não relacional)

Durante décadas, o modelo de dados predominante usado para desenvolvimento de aplicativos foi o modelo usado por bancos de dados relacionais, como Oracle, DB2, SQL Server, MySQL e PostgreSQL. Somente em meados dos anos 2000 que outros modelos de dados começaram a ser adotados e ter um uso mais significativo. Para diferenciar e categorizar essas novas classes de bancos e modelos de dados, o termo “NoSQL” foi criado. Muitas vezes, o termo “NoSQL” é usado de forma intercambiável com “não relacional”.

Embora existam muitos tipos de bancos de dados NoSQL com recursos variados, a tabela a seguir mostra algumas das diferenças entre os bancos de dados SQL e NoSQL.