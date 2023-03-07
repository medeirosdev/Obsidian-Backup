Criar uma API pode ser algo complexo, pois ela precisa dar suporte a vários recursos, como roteamento, autenticação e leitura e gravação em um armazenamento de dados. Para economizar tempo, você começa com as estruturas e modelos integrados ao .NET, que fornecem muitos dos recursos necessários. No entanto, essas estruturas podem exigir uma configuração considerável antes que você tenha uma API básica em funcionamento. Com a API mínima para o .NET 6, esse não é o caso. Você pode começar com apenas algumas linhas.

Para começar a API mínima, o principal requisito é usar pelo menos o .NET 6. Em seguida, você precisa de um editor de texto, como o Visual Studio, o Visual Studio Code, ou qualquer outro editor de texto de sua escolha. Por fim, você pode usar os sistemas operacionais Windows, macOS ou Linux.

## O que é a API mínima?

Se você desenvolveu uma API Web do .NET, terá usado uma abordagem com controladores. A ideia é ter um método da classe Controller, que representa vários verbos HTTP, para executar uma operação a fim de concluir uma tarefa específica. Por exemplo, `GetProducts()` retornaria produtos usando Get como um verbo HTTP.

Então, qual é a diferença entre a abordagem baseada em controlador e a API mínima?

-   **_Program.cs_ simplificado:** o modelo da API Web baseada em controlador conecta os controladores usando o método `AddControllers`. Além disso, ele conecta o Swagger para dar suporte ao OpenAPI. APIs mínimas não têm essa conexão por padrão, embora você possa adicionar o Swagger, se desejar.
    
-   **O roteamento parece um pouco diferente:** o roteamento parece ligeiramente diferente em comparação com uma API da Web baseada em controlador. Em uma API Web, para o roteamento, você escreve o código como demonstrado:-   C#Copiar
    
    ```
    app.UseRouting();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllers();
        // add my own routes
    });
    ```
    
    Com a API mínima, você adiciona a rota diretamente na instância `app`:
    
    C#Copiar
    
    ```
    app.MapGet("/todos", await (TodoDb db) => db.Todos.ToListAsync());
    app.MapPost("/todos", await (Todo todo) => {});
    app.MapPut("/todos", (Todo todo) => {});
    app.MapDelete("/todos/{id}", (int id) => {}});
    ```
    

A mesma funcionalidade ainda está lá. Você ainda configura um banco de dados, configura o CORS e adiciona a autenticação praticamente da mesma maneira com a qual está acostumado.

## Criar uma API com a API mínima

Com o .NET 6 instalado, este exemplo de comando cria um projeto mínimo de API:

BashCopiar

```
dotnet new web -o PizzaStore -f net6.0
```

A pasta _PizzaStore_ recém-criada contém seu projeto de API.

### Inspecionar os arquivos

Os arquivos gerados são muito semelhantes aos que você conseguiria com uma API baseada em controlador:

SaídaCopiar

```
bin/
obj/
appsettings.Development.json
appsettings.json
PizzaStore.csproj
Program.cs
```

Dentro de _PizzaStore.csproj_, há uma entrada como esta:

XMLCopiar

```
<PropertyGroup>
  <TargetFramework>net6.0</TargetFramework>
  <Nullable>enable</Nullable>
</PropertyGroup>
```

Esse código informa que você está usando o .NET 6.

### Compreender o código

_Program.cs_ contém seu código de API. Vamos examinar melhor um exemplo de programa:

C#Copiar

```
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();
app.MapGet("/", () => "Hello World!");
app.Run();
```

Se você usou versões anteriores do .NET, notará a falta de instruções `using`. Com o .NET 6, o compilador descobre as instruções `using` para você. Não é algo com o que você precise se preocupar.

 Observação

Conforme você adiciona mais recursos, como Entity Framework, por exemplo, você precisará adicionar instruções `using`. Mas, para uma API simples como o exemplo anterior, você ainda não precisa delas.

Nas duas primeiras linhas de código, você cria um construtor. No `builder`, você constrói uma instância de aplicativo `app`:

C#Copiar

```
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();
```

O construtor tem uma propriedade `Services`. Usando a propriedade `Services`, você pode adicionar recursos como CORS, Entity Framework ou Swagger. Aqui está um exemplo:

C#Copiar

```
builder.Services.AddCors(options => {});
```

Na propriedade `Services`, você informa à API que esse é um recurso a ser usado. Por outro lado, a instância `app` é mais usada. Portanto, você pode usar a instância `app` para configurar o roteamento, por exemplo:

C#Copiar

```
app.MapGet("/", () => "Hello World!");
```

Também é possível usar a instância `app` para adicionar middleware. Veja um exemplo de como você usaria uma funcionalidade como o CORS:

C#Copiar

```
app.UseCors("some unique string");
```

 Observação

O middleware geralmente é um código que intercepta a solicitação e executa verificações como a autenticação ou que garante que o cliente tenha permissão de executar essa operação de acordo com o CORS. Após a execução do middleware, a solicitação real é feita. Os dados são lidos ou gravados no repositório, e uma resposta é enviada de volta ao cliente de chamada.

Por fim, `app.Run()` inicia a sua API e a faz escutar solicitações do cliente.

Para executar seu código, você inicia seu projeto, como qualquer projeto .NET com `dotnet run`. Por padrão, isso significa que você tem um projeto em execução em _http://localhost:{PORT}_, em que `PORT` é um valor entre 5000 e 5300.

