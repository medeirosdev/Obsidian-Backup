Vamos começar criando nosso primeiro aplicativo Web do Blazor.
[[Blazor]]
Este módulo usa a [CLI (interface de linha de comando) do .NET](https://learn.microsoft.com/pt-br/dotnet/core/tools/), o [Visual Studio Code](https://code.visualstudio.com/) e o [Visual Studio 2022](https://visualstudio.com/) para desenvolvimento local. Depois de concluir este módulo, você poderá aplicar os conceitos dele usando um ambiente de desenvolvimento como o Visual Studio para Mac (macOS) ou continuar o desenvolvimento usando o Visual Studio Code (Windows, Linux & macOS) ou o Visual Studio.

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
## Criar um aplicativo Blazor

Para configurar um projeto do Blazor e trabalhar com ele, usaremos o Visual Studio Code. O Visual Studio Code inclui um terminal integrado, o que facilita a criação de projetos. Se você não quiser usar outro editor de código, poderá executar os comandos deste módulo em um terminal.

1.  No Visual Studio Code, escolha **Arquivo**>**Abrir Pasta**.
    
2.  Crie uma pasta chamada **BlazorApp** na localização de sua preferência e escolha **Selecionar pasta**.
    
3.  No Visual Studio Code, abra o terminal integrado selecionando **Exibir**>**Terminal** no menu principal.
    
4.  Na janela do terminal, copie e cole o comando a seguir.
    
    CLI do .NETCopiar
    
    ```
    dotnet new blazorserver -f net6.0
    ```
    
    Este comando cria um projeto de servidor Blazor básico com todas as páginas e todos os arquivos necessários, juntamente com um arquivo de projeto C# chamado **BlazorApp.csproj**.
    
    Você já deverá ter acesso a esses arquivos.

-| bin
-| Data
-| obj
-| Pages
  -| _Host.cshtml
  -| Counter.razor
  -| Error.cshtml
  -| Error.cshtml.cs
  -| FetchData.razor
  -| Index.razor
-| Properties
-| Shared
  -| MainLayout.razor
  -| MainLayout.razor.css
  -| NavMenu.razor
  -| NavMenu.razor.css
  -| SurveyPrompt.razor
-| wwwroot
-| _Imports.razor
-| App.razor
-| appsettings.Development.json
-| appsettings.json
-| BlazorApp.csproj
-| Program.cs****

1.  O Visual Studio Code solicita que você instale os ativos necessários; selecione **Sim**.
    
    ![Captura de tela mostrando o Visual Studio Code solicitando a instalação de ativos necessários para compilar e depurar.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/missing-assets-visual-studio-code.png)
    

## Executar o aplicativo

1.  Na janela do terminal, copie e cole o seguinte comando para executar o aplicativo no **modo de inspeção**:
    
    CLI do .NETCopiar
    
    ```
    dotnet watch run
    ```
    
    Isso compilará e iniciará e, em seguida, recompilará e reiniciará o aplicativo sempre que você fizer alterações de código. O aplicativo deve ser aberto automaticamente no navegador padrão. Seu navegador pode avisar que o site não é seguro. É seguro continuar.
    
    ![Captura de tela mostrando o aplicativo do Blazor em execução em um navegador.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/hello-blazor.png)
    

Esse aplicativo Blazor será usado nos próximos exercícios.

# Componentes do Razor

200 XP

Agora que você tem o ambiente de desenvolvimento configurado, você vai explorar a estrutura de um projeto do Blazor e aprender a adicionar novas páginas.

## O que é o Razor?

O Razor é uma sintaxe de marcação que usa HTML e C# para escrever componentes da interface do usuário de aplicativos Web Blazor.

O Razor se baseia em ASP.NET e foi projetado para a criação de aplicativos Web.

## O que são os componentes do Razor?

Um arquivo Razor define o que compõe as partes da interface do usuário do aplicativo. Os componentes do Blazor são análogos aos controles de usuário no ASP.NET Web Forms.

Se você explorar o projeto, verá que a maioria dos arquivos é .razor.

Em tempo de compilação, cada componente do Razor é criado em uma classe do .NET. A classe inclui elementos comuns da interface do usuário como estado, lógica de renderização, métodos de ciclo de vida e manipuladores de eventos.

![Captura de tela do Contador.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/counter.png)

Selecione o botão **Clique aqui** para incrementar a contagem sem uma atualização de página. O incremento de um contador em uma página da Web normalmente exige a escrita em JavaScript, mas com o Blazor, é possível usar C#.

Encontre a implementação do componente Contador em `Pages/Counter.razor`.

Encontre a implementação do componente Contador em `Pages/Counter.razor`.

razorCopiar

```
@page "/counter"

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

Uma solicitação para `/counter` no navegador, conforme especificado pela diretiva `@page` no início, faz com que o componente `Counter` renderize o conteúdo.

Sempre que você clica no botão **Clique aqui**, acontece o seguinte:

-   O evento onclick é acionado.
-   O método IncrementCount é chamado.
-   A currentCount é incrementada.
-   O componente é renderizado para mostrar a contagem atualizada.

# Exercício – adicionar um componente

Concluído100 XP

-   4 minutos

Neste exercício, você adicionará um componente Razor à home page do aplicativo.

No Visual Studio Code, abra a pasta que contém o projeto BlazorApp criado no módulo 3.

## Adicionar o componente Contador à home page

1.  Expanda as pastas no gerenciador de projetos do Visual Studio Code.
    
2.  Clique em **Páginas** para exibir as páginas do Razor existentes.
    
3.  Selecione o arquivo **Index.razor** para abri-lo.
    
4.  Adicione um componente `Counter` à página adicionando um elemento `<Counter />` no final do arquivo `Index.razor`.
    
    razorCopiar
    
    ```
    @page "/"
    
    <h1>Hello, world!</h1>
    
    Welcome to your new app.
    
    <SurveyPrompt Title="How is Blazor working for you?" />
    
    <Counter />
    ```
    

Salve o arquivo. NO Visual Studio Code, execute o comando `dotnet watch run` executado no módulo anterior; isso reiniciará o aplicativo e o atualizará no navegador para que o componente `Counter` seja mostrado na home page. No Visual Studio, você pode selecionar o botão **Recarga Dinâmica** para reiniciar o aplicativo.

![Componente Contador na home page.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/counter-homepage.png)

## Modificar um componente

Os parâmetros de componente são especificados por meio de atributos ou do conteúdo filho, que permitem definir propriedades no componente filho. Defina um parâmetro no componente Contador para especificar quanto ele será incrementado a cada clique de botão:

-   Adicione uma propriedade pública a `IncrementAmount` com um atributo `[Parameter]`.
-   Altere o método `IncrementCount` para usar o `IncrementAmount` ao incrementar o valor de `currentCount`.

O seguinte código contido no arquivo **Counter.razor** mostra como fazer isso:

razorCopiar

```
@page "/counter"

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    private void IncrementCount()
    {
        currentCount += IncrementAmount;
    }
}
```

Em `Index.razor`, atualize o elemento `<Counter>` para adicionar um atributo `IncrementAmount` que altera o valor de incremento para dez, conforme mostrado pela última linha do seguinte código:

razorCopiar

```
@page "/"

<h1>Hello, world!</h1>

Welcome to your new app.

<SurveyPrompt Title="How is Blazor working for you?" />

<Counter IncrementAmount="10" />
```

O componente `Index` agora tem um contador próprio, que é incrementado em dez cada vez que o botão **Clique aqui** é selecionado, conforme mostrado na imagem a seguir. O componente `Counter` (`Counter.razor`) no `/counter` continua a ser incrementado em um.

![Home page com a atualização do Contador.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/counter-homepage-modify.png)
