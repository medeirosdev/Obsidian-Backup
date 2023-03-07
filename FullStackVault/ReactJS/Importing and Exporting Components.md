[[ReactJS]]
A magia dos componentes reside na reutilização: você pode criar componentes compostos por outros componentes. Mas, à medida que você aninha mais e mais componentes, geralmente faz sentido começar a dividi-los em arquivos diferentes. Isso permite que você mantenha seus arquivos fáceis de digitalizar e reutilizar componentes em mais lugares.
### Você vai aprender

-   O que é um arquivo de componente raiz
-   Como importar e exportar um componente
-   Quando usar o padrão e as importações e exportações nomeadas
-   Como importar e exportar vários componentes de um arquivo
-   Como dividir componentes em vários arquivos

## O arquivo do componente raiz [](https://beta.reactjs.org/learn/importing-and-exporting-components#the-root-component-file "Link para o arquivo do componente raiz")

No [Seu primeiro componente](https://beta.reactjs.org/learn/your-first-component), você fez um `Profile` componente e um `Gallery` componente que o processa:
![[Pasted image 20230301185415.png]]
Atualmente, eles vivem em um **arquivo de componente raiz,** nomeado `App.js` neste exemplo. No [Criar aplicativo de reação](https://create-react-app.dev/), seu aplicativo mora em `src/App.js`. Dependendo da sua configuração, seu componente raiz pode estar em outro arquivo. Se você usar uma estrutura com roteamento baseado em arquivo, como Next.js, seu componente raiz será diferente para cada página.

## Exportando e importando um componente [](https://beta.reactjs.org/learn/importing-and-exporting-components#exporting-and-importing-a-component "Link para exportar e importar um componente")

E se você quiser mudar a tela de pouso no futuro e colocar uma lista de livros de ciências lá? Ou colocar todos os perfis em outro lugar? Faz sentido se mover `Gallery` e `Profile` fora do arquivo do componente raiz. Isso os tornará mais modulares e reutilizáveis em outros arquivos. Você pode mover um componente em três etapas:

1.  **Fazer** um novo arquivo JS para colocar os componentes.
2.  **Exportar** seu componente de função desse arquivo ( usando [padrão](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/export#using_the_default_export) ou [nomeado](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/export#using_named_exports) exportações ).
3.  **Importar** no arquivo em que você usará o componente ( usando a técnica correspondente para importar [padrão](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/import#importing_defaults) ou [nomeado](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/import#import_a_single_export_from_a_module) exportações ).

Aqui ambos `Profile` e `Gallery` foram retirados `App.js` em um novo arquivo chamado `Gallery.js`. Agora você pode mudar `App.js` importar `Gallery` de `Gallery.js`:![[Pasted image 20230301185609.png]]
Observe como este exemplo está dividido em dois arquivos de componentes agora:

1.  `Gallery.js`:
    -   Define o `Profile` componente que é usado apenas no mesmo arquivo e não é exportado.
    -   Exporta o `Gallery` componente como **exportação padrão.**
2.  `App.js`:
    -   Importações `Gallery` como um **importação padrão** de `Gallery.js`.
    -   Exporta a raiz `App` componente como **exportação padrão.**

![[Pasted image 20230301185635.png]]
## Exportando e importando vários componentes do mesmo arquivo [](https://beta.reactjs.org/learn/importing-and-exporting-components#exporting-and-importing-multiple-components-from-the-same-file "Link para exportar e importar vários componentes do mesmo arquivo")

E se você quiser mostrar apenas um `Profile` em vez de uma galeria? Você pode exportar o `Profile` componente também. Mas `Gallery.js` já tem um _padrão_ exportar e você não pode ter _dois_ exportações padrão. Você pode criar um novo arquivo com uma exportação padrão ou adicionar um _nomeado_ exportação para `Profile`. **Um arquivo pode ter apenas uma exportação padrão, mas pode ter inúmeras exportações nomeadas!**

> Para reduzir a confusão potencial entre exportações padrão e nomeadas, algumas equipes optam por manter apenas um estilo ( padrão ou nomeado ) ou evitam misturá-las em um único arquivo. É uma questão de preferência. Faça o que funciona melhor para você!

Primeiro, **exportação** `Profile` de `Gallery.js` usando uma exportação nomeada ( no `default` palavra-chave ):

```
export function Profile() {  // ...}
```

Então, **importar** `Profile` de `Gallery.js` para `App.js` usando uma importação nomeada ( com os aparelhos encaracolados ):

```
import { Profile } from './Gallery.js';
```

Finalmente, **render** `<Profile />` do `App` componente:

```
export default function App() {  return <Profile />;}
```

Agora `Gallery.js` contém duas exportações: uma inadimplência `Gallery` exportação e um nome `Profile` exportação. `App.js` importa os dois. Tente editar `<Profile />` para `<Gallery />` e de volta neste exemplo:

![[Pasted image 20230301185739.png]]
Agora você está usando uma mistura de exportações padrão e nomeadas:

-   `Gallery.js`:
    -   Exporta o `Profile` componente como **exportação chamada `Profile`.**
    -   Exporta o `Gallery` componente como **exportação padrão.**
-   `App.js`:
    -   Importações `Profile` como um **importação chamada `Profile`** de `Gallery.js`.
    -   Importações `Gallery` como um **importação padrão** de `Gallery.js`.
    -   Exporta a raiz `App` componente como **exportação padrão.**

## Recapitular[](https://beta.reactjs.org/learn/importing-and-exporting-components#recap "Link para recapitulação")

Nesta página você aprendeu:

-   O que é um arquivo de componente raiz
-   Como importar e exportar um componente
-   Quando e como usar o padrão e denominadas importações e exportações
-   Como exportar vários componentes do mesmo arquivo
- 