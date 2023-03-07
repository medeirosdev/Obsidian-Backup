## Adicionar documentação com o Swagger

Você quer criar a documentação para sua API. A documentação vai atender a você mesmo, seus colegas e a qualquer desenvolvedor de terceiros que queira usar sua API. É importante manter a documentação em sincronia com a sua API à medida que ela é alterada. Uma boa abordagem é descrever a API de forma padronizada e garantir que ela seja autodocumentada. Ao _autodocumentar_, queremos dizer que, se o código for alterado, a documentação será alterada com ele.

O Swagger implementa a especificação OpenAPI. Este formato descreve suas rotas, mas também os dados aceitos e produzidos. A interface do usuário do Swagger é uma coleção com ferramentas que renderizam a especificação OpenAPI como um site e permitem que você interaja com sua API por meio desse site.

Para usar o Swagger e a interface do usuário do Swagger na API, você precisa fazer duas coisas:

-   **Instalar um pacote.** Para instalar o Swagger, especifique a instalação do pacote Swashbuckle:
    
    BashCopiar
    
    ```
    dotnet add package Swashbuckle.AspNetCore --version 6.1.4   
    ```
    
-   **Configure-o.** Depois que o pacote for instalado, configure-o por meio do seu código. Adicione algumas entradas diferentes:
    
    -   Adicione um namespace. Você precisará desse namespace quando você chamar mais tarde `SwaggerDoc()` e fornecer as informações de cabeçalho para a sua API.
        
        C#Copiar
        
        ```
        using Microsoft.OpenApi.Models;
        ```
        
    -   Adicione `AddSwaggerGen()`. Esse método configura informações de cabeçalho em sua API, como o que é chamado e o número da versão.
        
        C#Copiar
        
        ```
        builder.Services.AddEndpointsApiExplorer();
        builder.Services.AddSwaggerGen(c =>
           {
               c.SwaggerDoc("v1", new OpenApiInfo { Title = "Todo API", Description = "Keep track of your tasks", Version = "v1" });
           });
        ```
        
    -   Adicionar `UseSwagger()` e `UseSwaggerUI()`. Essas duas linhas de código informarão ao projeto de API para usar o Swagger e também onde encontrar o arquivo de especificação _swagger.json_.
        
        C#Copiar
        
        ```
        app.UseSwagger();
        app.UseSwaggerUI(c =>
           {
             c.SwaggerEndpoint("/swagger/v1/swagger.json", "Todo API V1");
           });
        ```
        

Isso é tudo o que está envolvido na criação de uma API mínima! Iniciar o projeto e a navegação para _http://localhost:5000/swagger_ exibe algo assim:

