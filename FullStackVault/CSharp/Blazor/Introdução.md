O Blazor permite que os desenvolvedores do C# usem as habilidades para criar aplicativos Web com o C# e o Microsoft.NET.
[[Blazor]]
Imagine que você esteja criando um aplicativo Web no cliente e já tenha uma equipe de desenvolvedores .NET. Imagine também que você deseja implantar seu aplicativo como um aplicativo Web progressivo. Então, os usuários poderão baixar o aplicativo e usá-lo offline.

Com o Blazor, os desenvolvedores poderão criar lógica de front-end e back-end para aplicativos Web com linguagens, estruturas e ferramentas comuns.

Usar a mesma linguagem para o código do front-end e do back-end poderá:

-   Acelerar o desenvolvimento de aplicativos.
-   Reduzir a complexidade do pipeline de build.
-   Simplificar a manutenção.
-   Permitir que os desenvolvedores compreendam e trabalhem nos códigos do cliente e do servidor.

# O que é Blazor?


As empresas que criam aplicativos Web normalmente contratam desenvolvedores para diferentes funções. Alguns desenvolvedores criam lógica de back-end no servidor. Outros criam aplicativos Web no cliente. Geralmente, esses desenvolvedores usam diferentes linguagens de desenvolvimento e tecnologias.

C# e Microsoft .NET são opções populares para a criação de lógica no servidor. Mas os aplicativos no cliente geralmente são criados com estruturas da interface do usuário da Web que normalmente usam JavaScript. O uso de várias linguagens e conjuntos de ferramentas requer vários conjuntos de habilidades e, muitas vezes, exige duas equipes separadas. Da mesma forma, o código para transferir e representar os dados precisa ser compilado em ambas as linguagens e mantido em sincronia.

Nesta unidade, você começará com uma introdução ao Blazor e aos componentes dele.

## O que é Blazor?

Os aplicativos Blazor são feitos de componentes reutilizáveis da interface do usuário da Web, criados usando C#, HTML e CSS. Com o Blazor, os desenvolvedores podem criar código para cliente e servidor com o C#. Eles também podem compartilhar código e bibliotecas com o código de cliente de front-end e a lógica de back-end. O uso do C# para todo o código simplifica o compartilhamento de dados entre o front-end e o back-end, a reutilização de código para acelerar o desenvolvimento e a manutenção.

Você pode usar o Blazor para gerar:

-   Código no servidor que gerencie interações da interface do usuário em uma conexão WebSocket.
-   Um aplicativo Web no cliente que é executado diretamente no navegador por meio do WebAssembly.

## O que é o WebAssembly?

O WASM (WebAssembly) é um padrão binário aberto. Ele define um formato de código portátil para programas projetados para execução em navegadores da Web. O WebAssembly é uma linguagem assembly textual com formato binário compacto para downloads rápidos e para desempenho quase nativo.

O WebAssembly fornece um destino de compilação para linguagens como C, C++ e Rust. Ele foi projetado para ser executado com o JavaScript, para que ambos trabalhem juntos. O WebAssembly também pode gerar aplicativos Web progressivos para serem baixados e executados offline.

## O que é o WebAssembly Blazor?

Com o WebAssembly Blazor, os desenvolvedores podem executar códigos .NET em um navegador. Ele é uma estrutura de aplicativo de página única que usa os padrões abertos do WebAssembly sem exigir plug-ins nem geração de código.

O código .NET executado por meio do WebAssembly no navegador é executado na área restrita de JavaScript do navegador. O código inclui toda a segurança e proteção que a área restrita fornece. Essa inclusão ajuda a evitar ações mal-intencionadas em um computador cliente.

![Diagrama do Blazor WebAssembly.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/blazor-webassembly.png)

O Blazor usa um runtime do .NET compilado em um módulo do WebAssembly que é baixado com um aplicativo. O módulo pode executar o código do .NET Standard que é incluído no aplicativo Blazor.

Um aplicativo Blazor WebAssembly é restrito aos recursos do navegador que o executa, mas pode acessar a funcionalidade completa do navegador por meio da interoperabilidade do JavaScript.

### Navegadores compatíveis com o WebAssembly Blazor

O WebAssembly Blazor exige um navegador moderno para dispositivos móveis ou para área de trabalho. Atualmente, os seguintes navegadores são compatíveis:

-   Microsoft Edge
-   Mozilla Firefox
-   Google Chrome
-   Apple Safari

### O que é o Blazor Server?

O Blazor Server dá suporte para hospedar os componentes do Razor no servidor em um aplicativo ASP.NET Core. As atualizações da interface do usuário são tratadas por uma conexão SignalR.

O runtime permanece no servidor e processa:

-   A execução do código C# do aplicativo.
-   O envio de eventos de interface do usuário do navegador para o servidor.
-   A aplicação das atualizações de interface do usuário aos componentes renderizados que são enviadas novamente pelo servidor.

A conexão usada pelo Servidor Blazor a fim de se comunicar com o navegador também é empregada para processar as chamadas de interoperabilidade do JavaScript.

![Diagrama do Blazor Server.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/blazor-server.png)

## Requisitos de desenvolvimento do Blazor

Você pode criar aplicativos Blazor usando a última versão do Visual Studio 2022, do Visual Studio para Mac ou do Visual Studio Code. Neste módulo, você usará Visual Studio Code.

Independentemente do ambiente de desenvolvimento, você precisará instalar o **SDK do .NET 6.0**. Ao trabalhar com o Visual Studio 2022, inclua a carga de trabalho "ASP.NET e desenvolvimento Web" para garantir que o SDK e as ferramentas do .NET 6.0 estejam disponíveis no Visual Studio. Após a instalação, você terá tudo que precisa para começar a criar aplicativos Blazor. No próximo exercício, você criará seu primeiro aplicativo Blazor com o Visual Studio Code ou o Visual Studio 2022.

---
