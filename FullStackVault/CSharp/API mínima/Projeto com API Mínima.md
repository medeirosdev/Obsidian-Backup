# Exercício – criar uma API mínima

Concluído100 XP

-   2 minutos

Você é desenvolvedor em uma empresa e vocês ouviram falar da nova API mínima. Seu gerente solicitou que você crie um projeto com ela para que vocês possam discutir se devem usá-la em seu próximo projeto.

 Observação

Este módulo usa a CLI (interface de linha de comando) do .NET e o Visual Studio Code para desenvolvimento local. Depois de concluir este módulo, você poderá aplicar os conceitos usando o Visual Studio (Windows), o Visual Studio para Mac (macOS) ou o desenvolvimento contínuo usando o Visual Studio Code (Windows, Linux & macOS).

Este módulo usa o SDK do .NET 6.0. Verifique se tem o .NET 6.0 instalado, executando o seguinte comando em seu terminal preferido:

CLI do .NETCopiar

```
dotnet --list-sdks
```

Saída semelhante à seguinte exibida:

ConsoleCopiar

```
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
6.0.100 [C:\program files\dotnet\sdk]
```

Verifique se uma versão que começa com `6` está listada. Se nenhum estiver listado ou o comando não for encontrado, [instale o SDK do .NET 6.0 mais recente](https://dotnet.microsoft.com/download).

## Fazer scaffold de um projeto

Primeiro, você precisa criar o scaffold de um projeto. Você instalou o .NET 6 e tudo está pronto para começar.

1.  Em um terminal, crie uma API Web em um diretório chamado _PizzaStore_ executando `dotnet new`:
    
    BashCopiar
    
    ```
    dotnet new web -o PizzaStore -f net6.0
    ```
    
2.  Alterne para o novo diretório _PizzaStore_.
    
    BashCopiar
    
    ```
    cd PizzaStore
    ```
    
3.  Execute o aplicativo chamando `dotnet run`. Ele cria e hospeda o aplicativo em uma porta de 5000 a 5300. Há uma porta selecionada para o HTTPS no intervalo de 7000 a 7300.
    
     Observação
    
    Se quiser substituir o comportamento de seleção de porta aleatória, você poderá definir as portas a serem usadas em _launchSettings.json_.
    
    BashCopiar
    
    ```
    dotnet run
    ```
    
    A saída pode ser semelhante ao seguinte no terminal:
    
    SaídaCopiar
    
    ```
    Building...
     info: Microsoft.Hosting.Lifetime[14]
           Now listening on: https://localhost:7200
     info: Microsoft.Hosting.Lifetime[14]
           Now listening on: http://localhost:5100
     info: Microsoft.Hosting.Lifetime[0]
           Application started. Press Ctrl+C to shut down.
     info: Microsoft.Hosting.Lifetime[0]
           Hosting environment: Development
     info: Microsoft.Hosting.Lifetime[0]
           Content root path: /<path>/PizzaStore
    ```
    
4.  No navegador, vá para a porta indicada. De acordo com o terminal _http://localhost:{PORT}_, você deve ver o texto "Olá, Mundo!"
    

Parabéns! Você criou uma API usando um modelo da API mínima.

## Adicionar Swagger

Use o Swagger para garantir que você tenha uma API autodocumentada, na qual os documentos são alterados conforme você altera o código.

1.  Pressione **Ctrl+C** para parar de executar a API.
    
2.  Instale o pacote Swashbuckle:
    
    BashCopiar
    
    ```
    dotnet add package Swashbuckle.AspNetCore --version 6.2.3
    ```
    
3.  Abra o projeto no Visual Studio Code:
    
    BashCopiar
    
    ```
    code .
    ```
    
4.  No Visual Studio Code, no painel do explorer, abra _PizzaStore.csproj_. Você deverá ter uma entrada parecida com esta:
    
    XMLCopiar
    
    ```
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.2.3" />
    ```
    

Em seguida, configure seu projeto para usar o Swagger.

1.  Abra _Program.cs_ e adicione o código realçado. Salve as alterações.
2. ![[Pasted image 20230306104903.png]]
1.  Abra _Program.cs_ e adicione o código realçado. Salve as alterações.
    
    C#Copiar
    
    ```
    using Microsoft.OpenApi.Models;
    
    var builder = WebApplication.CreateBuilder(args);
        
    builder.Services.AddEndpointsApiExplorer();
    builder.Services.AddSwaggerGen(c =>
    {
         c.SwaggerDoc("v1", new OpenApiInfo { Title = "PizzaStore API", Description = "Making the Pizzas you love", Version = "v1" });
    });
        
    var app = builder.Build();
        
    app.UseSwagger();
    app.UseSwaggerUI(c =>
    {
       c.SwaggerEndpoint("/swagger/v1/swagger.json", "PizzaStore API V1");
    });
        
    app.MapGet("/", () => "Hello World!");
        
    app.Run();
    ```

1.  Pressione **Ctrl+'** para abrir um terminal no Code. No novo terminal, execute o aplicativo novamente:
    
    CLI do .NETCopiar
    
    ```
    dotnet run
    ```
    
2.  Navegue até o ponto de extremidade swagger do aplicativo, _http://localhost:{PORT}/swagger_.
    
    Você deve ver o seguinte resultado:
    
    ![Captura de tela de uma interface do usuário do Swagger para a sua API.](https://learn.microsoft.com/pt-br/training/aspnetcore/build-web-api-minimal-api/media/swagger.png)
    
3.  No terminal, pressione **Ctrl+C** para encerrar o programa.
    

Você adicionou com êxito o suporte para OpenAPI à sua API mínima usando o Swagger!

