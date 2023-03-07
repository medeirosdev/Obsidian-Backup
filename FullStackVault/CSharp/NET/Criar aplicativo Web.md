## Criar seu aplicativo
[[csharp.Net]]
Em seu prompt de comando, execute o seguinte comando para criar seu aplicativo:

Command promptCopy

```
dotnet new webapp -o MyWebApp --no-https -f net7.0
```

### O que este comando significa?

O comando `dotnet new` cria um novo aplicativo.

-   O parâmetro `webApp` seleciona qual modelo usar ao criar seu aplicativo.
-   O parâmetro `-o` cria um diretório chamado `MyWebApp` onde seu aplicativo é armazenado.
-   O sinalizador `--no-https` especifica a habilitação de HTTPS.
-   O parâmetro `-f` indica que você está criando um aplicativo .NET 7.

### Quais arquivos foram criados?

Vários arquivos foram criados no diretório `MyWebApp` para fornecer a você um aplicativo Web simples pronto para execução.

-   `Program.cs` contém o código de inicialização do aplicativo e a configuração de middleware.
-   O diretório `Pages` contém algumas páginas da Web de exemplo para o aplicativo.
-   `MyWebApp.csproj` define algumas configurações do projeto, como a versão do SDK do .NET para o destino.
-   O arquivo `launchSettings.json` dentro do diretório `Properties` define diferentes configurações de perfil para o ambiente de desenvolvimento local. Um número de porta variando entre 5000 e 5300 é atribuído automaticamente na criação do projeto e salvo neste arquivo.

Selecione o botão **Continuar** abaixo para ir para a próxima etapa.

## Executar seu aplicativo

No prompt de comando, navegue até o novo diretório criado na etapa anterior:

Command promptCopy

```
cd MyWebApp
```

Em seguida, execute o seguinte comando:

Command promptCopy

```
dotnet watch
```

Você deverá ver uma saída semelhante à seguinte:

Command prompt

```
watch : Hot reload enabled. For a list of supported edits, see https://aka.ms/dotnet/hot-reload. Press "Ctrl + R" to restart.
watch : Building...
Determining projects to restore...
All projects are up-to-date for restore.
MyWebApp -> C:\Projects\MyWebApp\bin\Debug\net6.0\MyWebApp.dll
watch : Started
info: Microsoft.Hosting.Lifetime[14]
Now listening on: http://localhost:5055
info: Microsoft.Hosting.Lifetime[0]
Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
Content root path: C:\Projects\MyWebApp\
```

O comando `dotnet watch` criará e iniciará o aplicativo e, em seguida, atualizará o aplicativo em execução sempre que você fizer alterações de código. Você pode parar o aplicativo a qualquer momento selecionando Ctrl+C.

Aguarde que o aplicativo exiba que está ouvindo em **http://localhost:<port number>** e que o navegador seja iniciado nesse endereço.

![A página inicial do seu site contém algum conteúdo de espaço reservado sobre ASP.NET.](https://dotnet.microsoft.com/static/images/screenshot-aspnet-tutorial-run.png?v=x7ZZjPGBfGn75DPzhFSdtTMJZBwVfG18fAvRlk-SdgA)

Parabéns, você criou e executou seu primeiro aplicativo Web .NET!

## Editar seu código

Abra o arquivo `Index.cshtml` localizado no diretório `Pages` em qualquer editor de texto.

Observação: verifique se você está abrindo a página cshtml e não a página cshtml.cs. Dependendo de como o sistema está configurado, o Windows poderá ocultar a extensão de arquivo.

Substitua todo o código pelo seguinte e salve o arquivo. As linhas de código realçadas mostrarão todas as alterações feitas por você.

Pages/Index.cshtmlCopy

```html
@page
@model IndexModel
@{
    ViewData["Title"] = "Home page";
}

<div class="text-center">
    <h1>Hello, world!</h1>
    <p>The time on the server is @DateTime.Now</p>
</div> 
 
```

Depois que essa alteração for salva, o comando `dotnet watch` aplicará a alteração ao aplicativo em execução e o atualizará no navegador, para que você possa ver a alteração no aplicativo em execução.

![Quando a página é atualizada, o novo conteúdo recém-adicionado por você aparecerá na página.](https://dotnet.microsoft.com/static/images/screenshot-aspnet-tutorial-run-modified.png?v=dL2Fay2NeqpSJ9HnrCq5MJAIFiuw3hDmlvDBY05EvAE)
