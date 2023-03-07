# Vinculação de dados e eventos
[[Blazor]]
Concluído100 XP

-   6 minutos

Você definiu a interface do usuário para seu aplicativo Web. Agora, explore como adicionar lógica ao aplicativo. Em um aplicativo Blazor, você pode adicionar o código C# em arquivos .cs separados ou embutidos nos componentes Razor.

## Code-behind de C# em arquivos separados

No Blazor, é possível adicionar arquivos C# diretamente ao projeto de aplicativo, assim como em outros projetos do .NET. Normalmente chamado de _code-behind_, essa técnica usa arquivos de código separados para armazenar a lógica do aplicativo. Arquivos separados são uma excelente estratégia quando sua lógica de negócios é complexa, é longa ou tem várias classes.

Para uma lógica simples, você nem sempre precisa criar arquivos .cs.

## C# embutido em componentes

É uma prática comum combinar HTML e C# em um único arquivo de componente do Razor. Para componentes simples com requisitos de código mais leves, essa abordagem funciona bem. Para adicionar código a um arquivo Razor, você deverá usar diretivas.

## O que são diretivas do Razor?

As diretivas do Razor são marcações de componente usadas para adicionar C# embutido com HTML. Com as diretivas, os desenvolvedores pode definir instruções únicas, métodos ou blocos de código maiores.

### Diretivas de código

As diretivas de código devem ser familiares aos desenvolvedores que usaram o Razor no MVC ou em páginas.

Você pode usar `@()` para adicionar uma instrução C# simples embutida com HTML. Se você precisar de mais códigos, use a diretiva `@code` para adicionar várias instruções delimitadas por parênteses.

Adicione também uma seção `@functions` ao modelo para métodos e propriedades. Elas são adicionadas à parte superior da classe gerada, onde o documento pode referenciá-las.

### Diretiva de página

A diretiva `@Page` é uma marcação especial que identifica um componente como uma página. Use essa diretiva para especificar uma rota. A rota é mapeada para uma rota de atributo, que o mecanismo do Blazor reconhece para registrar e acessar a página.

## Associação de dados do Razor

Nos componentes do Razor, você pode fazer associação de dados de elementos HTML com campos e propriedades do C# ou com valores de expressão do Razor. A associação de dados permite a sincronização bidirecional entre o HTML e o Microsoft .NET.

Os dados são enviados por push do HTML para o .NET quando um componente é renderizado. Como os componentes são renderizados após a execução do código do manipulador de eventos, as atualizações de propriedade são refletidas na IU imediatamente após o disparo de um manipulador de eventos.

Use a marcação `@bind` para associar uma variável em C# a um objeto HTML. Você define a variável em C# pelo nome como uma cadeia de caracteres em HTML. Você verá um exemplo de vinculação de dados no exercício a seguir.