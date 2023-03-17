## Componentes: blocos de construção da interface do usuário [](https://beta.reactjs.org/learn/your-first-component#components-ui-building-blocks "Link para componentes: blocos de construção da interface do usuário")

Na Web, o HTML nos permite criar documentos estruturados ricos com seu conjunto interno de tags, como `<h1>` e `<li>`:

```
<article>  
<h1>My First Component</h1>  
<ol>   
<li>Components: UI Building Blocks</li>    
<li>Defining a Component</li>    
<li>Using a Component</li>  
</ol>
</article>
```

Esta marcação representa este artigo `<article>`, sua posição `<h1>`, e um índice ( abreviado ) como uma lista ordenada `<ol>`. A marcação como essa, combinada com o CSS para estilo e o JavaScript para interatividade, fica atrás de todas as barras laterais, avatar, modal, menu suspenso — todas as partes da interface do usuário que você vê na Web.

O React permite combinar sua marcação, CSS e JavaScript em componentes personalizados “ ”, **elementos reutilizáveis da interface do usuário para o seu aplicativo.** O código do índice que você viu acima pode ser transformado em um `<TableOfContents />` componente que você pode renderizar em todas as páginas. Sob o capô, ele ainda usa as mesmas tags HTML, como `<article>`, `<h1>`, etc.

Assim como nas tags HTML, você pode compor, solicitar e aninhar componentes para projetar páginas inteiras. Por exemplo, a página de documentação que você está lendo é composta de componentes de reação:

```
<PageLayout>  
<NavigationHeader>    
<SearchBar />    
<Link to="/docs">Docs</Link>  
</NavigationHeader>  
<Sidebar />  
<PageContent>   
<TableOfContents />    
<DocumentationText />  </PageContent></PageLayout>
```

À medida que seu projeto cresce, você notará que muitos de seus projetos podem ser compostos reutilizando os componentes que você já escreveu, acelerando seu desenvolvimento. Nosso índice acima pode ser adicionado a qualquer tela com `<TableOfContents />`! Você pode até iniciar seu projeto com os milhares de componentes compartilhados pela comunidade de código aberto React, como [Chakra UI](https://chakra-ui.com/) e [UI material.](https://material-ui.com/)

## Definindo um componente [](https://beta.reactjs.org/learn/your-first-component#defining-a-component "Link para definir um componente")

Tradicionalmente, ao criar páginas da web, os desenvolvedores da web marcavam seu conteúdo e depois adicionavam interação borrifando em algum JavaScript. Isso funcionou muito bem quando a interação era agradável na web. Agora é esperado para muitos sites e todos os aplicativos. O React coloca a interatividade em primeiro lugar enquanto ainda usa a mesma tecnologia: **um componente React é uma função JavaScript que você pode _polvilhe com marcação_.** Aqui está o que parece ( você pode editar o exemplo abaixo ):
![[Pasted image 20230301184437.png]]
### Etapa 1: Exportar o componente [](https://beta.reactjs.org/learn/your-first-component#step-1-export-the-component "Link para a Etapa 1: Exportar o componente")

O `export default` prefixo é um [sintaxe JavaScript padrão](https://developer.mozilla.org/docs/web/javascript/reference/statements/export) ( não específico para Reagir ). Permite marcar a função principal em um arquivo para que você possa importá-la posteriormente de outros arquivos. ( Mais sobre importação em [Importando e Exportando Componentes](https://beta.reactjs.org/learn/importing-and-exporting-components)!)

### Etapa 2: defina a função [](https://beta.reactjs.org/learn/your-first-component#step-2-define-the-function "Link para a etapa 2: defina a função")

Com `function Profile() { }` você define uma função JavaScript com o nome `Profile`.
![[Pasted image 20230301184607.png]]
### Etapa 3: adicionar marcação [](https://beta.reactjs.org/learn/your-first-component#step-3-add-markup "Link para a etapa 3: adicionar marcação")

O componente retorna um `<img />` tag com `src` e `alt` atributos. `<img />` está escrito como HTML, mas na verdade é JavaScript sob o capô! Essa sintaxe é chamada [JSX](https://beta.reactjs.org/learn/writing-markup-with-jsx), e permite incorporar marcação dentro do JavaScript.

As instruções de devolução podem ser escritas todas em uma linha, como neste componente:

```
return <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />;
```

Mas se sua marcação não estiver na mesma linha que a `return` palavra-chave, você deve envolvê-lo em um par de parênteses como este:

```
return (  <div>    <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />  </div>);
```

![[Pasted image 20230301184628.png]]
![[Pasted image 20230301184646.png]]
### O que o navegador vê [](https://beta.reactjs.org/learn/your-first-component#what-the-browser-sees "Link para o que o navegador vê")

Observe a diferença no invólucro:

-   `<section>`é minúsculo, então React sabe que nos referimos a uma tag HTML.
-   `<Profile />` começa com um capital `P`, então o React sabe que queremos usar nosso componente chamado `Profile`.

E `Profile` contém ainda mais HTML: `<img />`. No final, é isso que o navegador vê:

```
<section>  <h1>Amazing scientists</h1>  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" /></section>
```

### Aninhando e organizando componentes [](https://beta.reactjs.org/learn/your-first-component#nesting-and-organizing-components "Link para componentes de nidificação e organização")

Os componentes são funções JavaScript regulares, para que você possa manter vários componentes no mesmo arquivo. Isso é conveniente quando os componentes são relativamente pequenos ou estão intimamente relacionados entre si. Se esse arquivo estiver lotado, você sempre poderá se mover `Profile` para um arquivo separado. Você aprenderá como fazer isso em breve no [página sobre importações.](https://beta.reactjs.org/learn/importing-and-exporting-components)

Porque o `Profile` componentes são renderizados dentro `Gallery`— mesmo várias vezes! — podemos dizer que `Gallery` é um **componente pai,** renderizando cada `Profile` como uma criança “ ”. Isso faz parte da magia do React: você pode definir um componente uma vez e usá-lo em quantos lugares e quantas vezes quiser.
![[Pasted image 20230301184738.png]]
Quando um componente filho precisa de alguns dados dos pais, [passe por adereços](https://beta.reactjs.org/learn/passing-props-to-a-component) em vez de aninhar definições.
![[Pasted image 20230301184836.png]]

