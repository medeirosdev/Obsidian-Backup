## [[JSX]]
```
const element = <h1>Hello, world!</h1>;
```

Esta sintaxe estranha de tags não é uma string, nem HTML.

É chamada JSX e é uma extensão de sintaxe para JavaScript. Recomendamos usar JSX com o React para descrever como a UI deveria parecer. JSX pode lembrar uma linguagem de template, mas que vem com todo o poder do JavaScript.
JSX produz “elementos” do React.
O React adota o fato de que a lógica de renderização é inerentemente acoplada com outras lógicas de UI: como eventos são manipulados, como o state muda com o tempo e como os dados são preparados para exibição.

Ao invés de separar _tecnologias_ artificialmente colocando markup e lógica em arquivos separados, o React [separa _conceitos_](https://pt.wikipedia.org/wiki/Separa%C3%A7%C3%A3o_de_conceitos) com unidades pouco acopladas chamadas “componentes” que contém ambos. Voltaremos aos componentes em [outra seção](https://pt-br.reactjs.org/docs/components-and-props.html). Mas, se você ainda não está confortável em usar markup em JS, [esta palestra](https://www.youtube.com/watch?v=x7cQ3mrcKaY) pode convencer você do contrário.

O React [não requer](https://pt-br.reactjs.org/docs/react-without-jsx.html) o uso do JSX. Porém, a maioria das pessoas acha prático como uma ajuda visual quando se está trabalhando com uma UI dentro do código em JavaScript. Ele permite ao React mostrar mensagens mais úteis de erro e aviso.
É seguro incorporar entradas de usuário em JSX:

```
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```

Por padrão, o React DOM [escapa](https://stackoverflow.com/questions/7381974/which-characters-need-to-be-escaped-on-html) quaisquer valores incorporados no JSX antes de renderizá-los. Assim, assegura que você nunca injete algo que não esteja explicitamente escrito na sua aplicação. Tudo é convertido para string antes de ser renderizado. Isso ajuda a prevenir ataques [XSS (cross-site-scripting)](https://pt.wikipedia.org/wiki/Cross-site_scripting).


## [[Componentes e Props]]
O React coloca a interatividade em primeiro lugar enquanto ainda usa a mesma tecnologia: **um componente React é uma função JavaScript que você pode _polvilhe com marcação
O React permite combinar sua marcação, CSS e JavaScript em componentes personalizados “ ”, **elementos reutilizáveis da interface do usuário para o seu aplicativo.** O código do índice que você viu acima pode ser transformado em um `<TableOfContents />` componente que você pode renderizar em todas as páginas. Sob o capô, ele ainda usa as mesmas tags HTML, como `<article>`, `<h1>`, etc.
Assim como nas tags HTML, você pode compor, solicitar e aninhar componentes para projetar páginas inteiras.
O `export default` prefixo é um [sintaxe JavaScript padrão](https://developer.mozilla.org/docs/web/javascript/reference/statements/export) ( não específico para Reagir ). Permite marcar a função principal em um arquivo para que você possa importá-la posteriormente de outros arquivos. ( Mais sobre importação em [Importando e Exportando Componentes](https://beta.reactjs.org/learn/importing-and-exporting-components)!)
Com `function Profile() { }` você define uma função JavaScript com o nome `Profile`.
![[Pasted image 20230301184607.png]]
As instruções de devolução podem ser escritas todas em uma linha, como neste componente:

```
return <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />;
```

Mas se sua marcação não estiver na mesma linha que a `return` palavra-chave, você deve envolvê-lo em um par de parênteses como este:

```
return (  <div>    <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />  </div>);
```
As instruções de devolução podem ser escritas todas em uma linha, como neste componente:

```
return <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />;
```

Mas se sua marcação não estiver na mesma linha que a `return` palavra-chave, você deve envolvê-lo em um par de parênteses como este:

```
return (  <div>    <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />  </div>);
```
### Como passar Props para funções
React components use _props_ to communicate with each other. Every parent component can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.
The props you can pass to an `<img>` tag are predefined (ReactDOM conforms to [the HTML standard](https://www.w3.org/TR/html52/semantics-embedded-content.html#the-img-element)). But you can pass any props to _your own_ components, such as `<Avatar>`, to customize them. Here’s how!

#### Passing props to a component [](https://react.dev/learn/passing-props-to-a-component#passing-props-to-a-component "Link for Passing props to a component")

In this code, the `Profile` component isn’t passing any props to its child component, `Avatar`:

```
export default function Profile() {  return (    <Avatar />  );}
```

You can give `Avatar` some props in two steps.

### Step 1: Pass props to the child component [](https://react.dev/learn/passing-props-to-a-component#step-1-pass-props-to-the-child-component "Link for Step 1: Pass props to the child component")

First, pass some props to `Avatar`. For example, let’s pass two props: `person` (an object), and `size` (a number):

```
export default function Profile() {  return (    <Avatar      person={{ name: 'Lin Lanying', imageId: '1bX5QH6' }}      size={100}    />  );}
```

### Note

If double curly braces after `person=` confuse you, recall [they’re merely an object](https://react.dev/learn/javascript-in-jsx-with-curly-braces#using-double-curlies-css-and-other-objects-in-jsx) inside the JSX curlies.

Now you can read these props inside the `Avatar` component.

### Step 2: Read props inside the child component [](https://react.dev/learn/passing-props-to-a-component#step-2-read-props-inside-the-child-component "Link for Step 2: Read props inside the child component")

You can read these props by listing their names `person, size` separated by the commas inside `({` and `})` directly after `function Avatar`. This lets you use them inside the `Avatar` code, like you would with a variable.

```
function Avatar({ person, size }) {  // person and size are available here}
```

Add some logic to `Avatar` that uses the `person` and `size` props for rendering, and you’re done.

Now you can configure `Avatar` to render in many different ways with different props. Try tweaking the values!
```import { getImageUrl } from './utils.js';

function Avatar({ person, size }) {
  return (
    <img
      className="avatar"
      src={getImageUrl(person)}
      alt={person.name}
      width={size}
      height={size}
    />
  );
}

export default function Profile() {
  return (
    <div>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi', 
          imageId: 'YfeOqp2'
        }}
      />
      <Avatar
        size={80}
        person={{
          name: 'Aklilu Lemma', 
          imageId: 'OKS67lh'
        }}
      />
      <Avatar
        size={50}
        person={{ 
          name: 'Lin Lanying',
          imageId: '1bX5QH6'
        }}
      />
    </div>
  );
}

```
Props let you think about parent and child components independently. For example, you can change the `person` or the `size` props inside `Profile` without having to think about how `Avatar` uses them. Similarly, you can change how the `Avatar` uses these props, without looking at the `Profile`.

You can think of props like “knobs” that you can adjust. They serve the same role as arguments serve for functions—in fact, props _are_ the only argument to your component! React component functions accept a single argument, a `props` object:
Usually you don’t need the whole `props` object itself, so you destructure it into individual props.

### Pitfall

**Don’t miss the pair of `{` and `}` curlies** inside of `(` and `)` when declaring props:

```
function Avatar({ person, size }) {  // ...}
```

This syntax is called [“destructuring”](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Unpacking_fields_from_objects_passed_as_a_function_parameter) and is equivalent to reading properties from a function parameter:

```
function Avatar(props) {  let person = props.person;  let size = props.size;  // ...}
```
https://react.dev/learn/passing-props-to-a-component
## [[Contexts]]
Em uma aplicação típica do React, os dados são passados de cima para baixo (de pai para filho) via props, mas esse uso pode ser complicado para certos tipos de props (como preferências locais ou tema de UI), que são utilizadas por muitos componentes dentro da aplicação. Contexto (context) fornece a forma de compartilhar dados como esses, entre todos componentes da mesma árvore de componentes, sem precisar passar explicitamente props entre cada nível.

Contexto (context) é indicado para compartilhar dados que podem ser considerados “globais” para a árvore de componentes do React. Usuário autenticado ou o idioma preferido, são alguns casos comuns

Contexto (context) é usado principalmente quando algum dado precisa ser acessado por _muitos_ componentes em diferentes níveis. Use contexto moderadamente uma vez que isto pode dificultar a reutilização de componentes.

**Se você apenas quer evitar passar algumas props por muitos níveis, [composição de componente](https://pt-br.reactjs.org/docs/composition-vs-inheritance.html) geralmente é uma solução mais simples que Contexto (context).**


## [[Hooks]]
_Hooks_ são uma nova adição ao React 16.8. Eles permitem que você use o state e outros recursos do React sem escrever uma classe.
```
import React, { useState } from 'react';

function Example() {
  // Declare uma nova variável de state, a qual chamaremos de "count"  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```
Essa nova função `useState` é o primeiro “Hook” que nós iremos aprender, mas este exemplo é só um gostinho. Não se preocupe se isso ainda não fizer sentido!
### 📌 State Hook

Este exemplo renderiza um contador. Quando você clica no botão, ele incrementa o valor:
```
import React, { useState } from 'react';
function Example() {
  // Declara uma nova variável de state, que chamaremos de "count"  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

Aqui, `useState` é um _Hook_ (nós vamos falar sobre o que isso significa em instantes). Nós o chamamos dentro de um componente funcional para adicionar alguns states locais a ele. React irá preservar este state entre re-renderizações. `useState` retorna um par: o valor do state _atual_ e uma função que permite atualizá-lo. Você pode chamar essa função a partir de um manipulador de evento ou de qualquer outro lugar. É parecido com `this.setState` em uma classe, exceto que não mescla o antigo state com o novo. (Nós iremos mostrar um exemplo comparando `useState` com `this.state` em [Utilizando o State Hook](https://pt-br.reactjs.org/docs/hooks-state.html).)

O único argumento para `useState` é o state inicial. No exemplo acima, é `0` porque nosso contador começa do zero. Perceba que diferente de `this.state`, o state não precisa ser um objeto — apesar de que possa ser se você quiser. O argumento de state inicial é utilizado apenas durante a primeira renderização.

#### [](https://pt-br.reactjs.org/docs/hooks-overview.html#declaring-multiple-state-variables)Declarando múltiplas variáveis de state

Você pode utilizar o State Hook mais de uma vez em um único componente:

```
function ExampleWithManyStates() {
  // Declara várias variáveis de state!
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
  // ...
}
```

A sintaxe de [desestruturação de arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Array_destructuring) nos permite atribuir diferentes nomes para as variáveis de state que declaramos chamando `useState`. Esses nomes não fazem parte da API `useState`. Em vez disso, React presume que se você chamar `useState` muitas vezes, você faz isso na mesma ordem a cada renderização. Mais tarde, voltaremos no porquê disso funcionar e quando será útil.

#### [](https://pt-br.reactjs.org/docs/hooks-overview.html#but-what-is-a-hook)
#### Mas, o que é um Hook?

Hooks são funções que permitem a você “ligar-se” aos recursos de state e ciclo de vida do React a partir de componentes funcionais. Hooks não funcionam dentro de classes — eles permitem que você use React sem classes. (Nós [não recomendamos](https://pt-br.reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy) reescrever seus componentes já existentes de um dia para o outro, mas você pode começar a usar Hooks nos novos se você quiser.)

React fornece alguns Hooks internos como `useState`. Você também pode criar os seus próprios Hooks para reutilizar o comportamento de state entre componentes diferentes. Vamos dar uma olhada nos Hooks internos primeiramente.
### Usando o StateHookS
### O que é um Hook?

Nosso novo exemplo começa importando o `useState` Hook do React:

```
import React, { useState } from 'react';
function Example() {
  // ...
}
```

**O que é um Hook?** Um Hook é uma função especial que te permite utilizar recursos do React. Por exemplo, `useState` é um Hook que te permite adicionar o state do React a um componente de função. Vamos aprender outros Hooks mais tarde.

**Quando eu deveria usar um Hook?** Se você escreve um componente de função e percebe que precisa adicionar algum state para ele, anteriormente você tinha que convertê-lo para uma classe. Agora você pode usar um Hook dentro de um componente de função existente. Vamos fazer isso agora mesmo!

> Nota:
> 
> Existem algumas regras especiais sobre onde você pode ou não utilizar Hooks dentro de um componente. Vamos aprender elas nas [Regras dos Hooks](https://pt-br.reactjs.org/docs/hooks-rules.html).
 chamamos o Hook `useState` dentro do nosso component:

```
import React, { useState } from 'react';

function Example() {
  // Declarar uma nova variável de state, na qual chamaremos de "count"  const [count, setCount] = useState(0);
```

**O que o `useState` faz?** Ele declara um variável state. Nossa variável é chamada de `count` mas poderíamos chamar de qualquer coisa, como `banana`. Esta é uma maneira de “preservar” alguns valores entre as chamadas de funções — `useState` é uma nova maneira de usar as mesmas capacidades que o `this.state` tem em uma classe. Normalmente, variáveis “desaparecem” quando a função sai mas variáveis de state são preservadas pelo React.

**O que passamos para o `useState` como argumento?** O único argumento para o Hook `useState()` é o state inicial. Diferente de classes, o state não tem que ser um objeto. Podemos manter um número ou uma string se for tudo que precisamos. No nosso exemplo, apenas queremos um número para quantas vezes o usuário clicou, então passamos 0 como state inicial para nossa variável. (Se quiséssemos guardar dois valores diferentes no state, chamaríamos `useState()` duas vezes.)

**O que `useState` retorna?** Ele retorna um par de valores: o state atual e uma função que atualiza o state. É por isso que escrevemos `const [count, setCount] = useState()`. Isto é similar ao `this.state.count` e `this.setState` em uma classe, exceto o fato de pegá-los em par. Se você não está familiarizado com a sintaxe que usamos, vamos voltar nisso [no final dessa página](https://pt-br.reactjs.org/docs/hooks-state.html#tip-what-do-square-brackets-mean).

Agora que sabemos o que o Hook `useState` faz, nosso exemplo deve fazer mais sentido:

```
import React, { useState } from 'react';

function Example() {
  // Declarar uma nova variável de state, na qual chamaremos de "count"  const [count, setCount] = useState(0);
```

Nós declaramos uma variável state chamada `count` e definimos ela para 0. O React vai lembrar o valor atual entre cada re-renderização e fornecer o valor mais recente para nossa função. Se quisermos atualizar o `count` atual, podemos chamar `setCount`.
#### Lendo o State

Em uma função, podemos usar `count` diretamente:

```
  <p>Você clicou {count} vezes</p>
```



### Hook de Efeito
Você provavelmente já realizou obtenção de dados (data fetching), subscrições (subscriptions) ou mudanças manuais no DOM através de componentes React antes. Nós chamamos essas operações de “efeitos colaterais” (side effects ou apenas effects) porque eles podem afetar outros componentes e não podem ser feitos durante a renderização.

O Hook de Efeito, `useEffect`, adiciona a funcionalidade de executar efeitos colaterais através de um componente funcional. Segue a mesma finalidade do `componentDidMount`, `componentDidUpdate`, e `componentWillUnmount` em classes React, mas unificado em uma mesma API. (Nós mostraremos exemplos comparando `useEffect` com esses métodos em [Utilizando o Hook de Efeito](https://pt-br.reactjs.org/docs/hooks-effect.html).)

Por exemplo, este componente define o título da página após o React atualizar o DOM:

```
import React, { useState, useEffect } from 'react';
function Example() {
  const [count, setCount] = useState(0);

  // Similar a componentDidMount e componentDidUpdate:  useEffect(() => {    // Atualiza o título do documento utilizando a API do navegador    document.title = `Você clicou ${count} vezes`;  });
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

Quando você chama `useEffect`, você está dizendo ao React para executar a sua função de “efeito” após liberar as mudanças para o DOM. Efeitos são declarados dentro do componente, para que eles tenham acesso as suas props e state. Por padrão, React executa os efeitos após cada renderização — _incluindo_ a primeira renderização. (Falaremos mais sobre como isso se compara aos ciclos de vida das classes em [Utilizando o Hook de Efeito](https://pt-br.reactjs.org/docs/hooks-effect.html).)

Efeitos também podem opcionalmente especificar como “limpar” (clean up) retornando uma função após a execução deles. Por exemplo, este componente utiliza um efeito para se subscrever ao status online de um amigo e limpa-se (clean up) cancelando a sua subscrição:

```
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  useEffect(() => {    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);    return () => {      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);    };  });
  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

Neste exemplo, o React cancelaria a subscrição da nossa `ChatAPI` quando o componente se desmontar, e também antes de reexecutar o efeito devido a uma renderização subsequente. (Se você quiser, há uma maneira de [dizer ao React para ignorar a nova subscrição](https://pt-br.reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects) se o `props.friend.id` que passamos para `ChatAPI` não tiver mudado.)

Assim como `useState`, você pode utilizar mais de um efeito em um componente:

```
function FriendStatusWithCounter(props) {
  const [count, setCount] = useState(0);
  useEffect(() => {    document.title = `Você clicou ${count} vezes`;
  });

  const [isOnline, setIsOnline] = useState(null);
  useEffect(() => {    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }
  // ...
```

Hooks permitem a você organizar efeitos colaterais _(side effects)_ em um componente por partes relacionadas (como adicionar e remover uma subscrição), em vez de forçar uma divisão baseada nos métodos de ciclo de vida.

### Usando o Effect Hook
O _Effect Hook_ (Hook de Efeito) te permite executar efeitos colaterais em componentes funcionais:

```
import React, { useState, useEffect } from 'react';
function Exemplo() {
  const [count, setCount] = useState(0);

  // Similar ao componentDidMount e componentDidUpdate:  useEffect(() => {    // Atualiza o título do documento usando a API do browser    document.title = `Você clicou ${count} vezes`;  });
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

Esse trecho de código é baseado no [exemplo de contador da página anterior](https://pt-br.reactjs.org/docs/hooks-state.html), mas nós adicionamos uma nova funcionalidade a ele: nós definimos o título do documento para ser uma mensagem customizada que inclua o número de cliques.

Buscar dados, configurar uma subscription, e mudar o DOM manualmente dentro dos componentes React são exemplos de efeitos colaterais. Esteja você acostumado ou não a chamar essas operações de “efeitos colaterais” (ou somente “efeitos”), você provavelmente já usou eles em seus componentes antes.

> Dica
> 
> Se você está familiarizado com os métodos do ciclo de vida do React, você pode pensar no Hook `useEffect` como `componentDidMount`, `componentDidUpdate`, e `componentWillUnmount` combinados.

Existem dois tipos comuns de efeitos colaterais nos componentes React: aqueles que não precisam de limpeza, e aqueles que precisam. Vamos ver as suas diferenças mais detalhadamente.

Efeitos Sem Limpeza

De vez em quando, nós queremos **executar algum código adicional depois que o React atualizou a DOM.** Requisições, mutações manuais do DOM e log são exemplos comuns de efeitos que não precisam de limpeza. Nós dizemos isso porque podemos executa-los e imediatamente esquecer deles. Vamos comparar como classes e Hooks nos permitem expressar tais efeitos colaterais.
Nós já vimos esse exemplo no topo da página, mas vamos dar uma olhada mais de perto:

```
import React, { useState, useEffect } from 'react';
function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {    document.title = `Você clicou ${count} vezes`;  });
  return (
    <div>
      <p>Você clicou {count} vezes</p>
      <button onClick={() => setCount(count + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

**O que o `useEffect` faz?** Usando esse Hook, você diz ao React que o componente precisa fazer algo apenas depois da renderização. O React ira se lembrar da função que você passou (nos referiremos a ele como nosso “efeito”), e chamá-la depois que realizar as atualizações do DOM. Nesse efeito, mudamos o título do documento, mas podemos também realizar busca de dados ou chamar alguma API imperativa.

**Por que `useEffect` é chamado dentro de um componente?** Colocando `useEffect` dentro do componente nos permite acessar o state `count` (ou qualquer outra prop) direto do efeito. Nós não precisamos de uma API especial para lê-los — já está no escopo da função. Hooks adotam as closures do JavaScript e evitam APIs especificas do React onde o JavaScript já provê uma solução.

**`useEffect` executa depois de toda renderização?** Sim! Por padrão, ele roda depois da primeira renderização _e_ depois de toda atualização. (Falaremos sobre [como customizar isso](https://pt-br.reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects) depois.) Em vez de pensar em termos de “montando” (“mounting”) e “atualizando” (“updating”), você pode achar mais fácil pensar que efeitos acontecem “depois da renderização”. React garante que o DOM foi atualizado na hora de executar os efeitos.

### [](https://pt-br.reactjs.org/docs/hooks-effect.html#detailed-explanation)
## [Renderização condicional](https://pt-br.reactjs.org/docs/conditional-rendering.html)
Em React, você pode criar componentes distintos que encapsulam o comportamento que você precisa. Então, você pode renderizar apenas alguns dos elementos, dependendo do estado da sua aplicação.

Renderização condicional em React funciona da mesma forma que condições funcionam em JavaScript. Use operadores de JavaScript como [`if`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/if...else) ou [operador condicional](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional) para criar elementos representando o estado atual, e deixe o React atualizar a UI para corresponde-los.

Considere esses dois componentes:

```
function UserGreeting(props) {
  return <h1>Welcome back!</h1>;
}

function GuestGreeting(props) {
  return <h1>Please sign up.</h1>;
}
```

Nós vamos criar um componente `Greeting` que mostra um dos outros dois componentes se o usuário estiver logado ou não:

```
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {    return <UserGreeting />;  }  return <GuestGreeting />;}
const root = ReactDOM.createRoot(document.getElementById('root')); 
// Try changing to isLoggedIn={true}:
root.render(<Greeting isLoggedIn={false} />);
```
Este exemplo renderiza um “greeting” diferente dependendo do valor da prop `isLoggedIn`.

Você pode usar variáveis para guardar elementos. Isto pode te ajudar a renderizar condicionalmente parte do componente enquanto o resto do resultado não muda.

Considere esses dois novos componentes representando os botões de Logout e Login:

```
function LoginButton(props) {
  return (
    <button onClick={props.onClick}>
      Login
    </button>
  );
}

function LogoutButton(props) {
  return (
    <button onClick={props.onClick}>
      Logout
    </button>
  );
}
```

No exemplo abaixo, nós vamos criar um [componente _stateful_](https://pt-br.reactjs.org/docs/state-and-lifecycle.html#adding-local-state-to-a-class) chamado `LoginControl`.

O componente irá renderizar o `<LoginButton />` ou `<LogoutButton />` dependendo do estado atual. Ele tambem irá renderizar `<Greeting />` do exemplo anterior:

```
class LoginControl extends React.Component {
  constructor(props) {
    super(props);
    this.handleLoginClick = this.handleLoginClick.bind(this);
    this.handleLogoutClick = this.handleLogoutClick.bind(this);
    this.state = {isLoggedIn: false};
  }

  handleLoginClick() {
    this.setState({isLoggedIn: true});
  }

  handleLogoutClick() {
    this.setState({isLoggedIn: false});
  }

  render() {
    const isLoggedIn = this.state.isLoggedIn;
    let button;
    if (isLoggedIn) {      button = <LogoutButton onClick={this.handleLogoutClick} />;    } else {      button = <LoginButton onClick={this.handleLoginClick} />;    }
    return (
      <div>
        <Greeting isLoggedIn={isLoggedIn} />        {button}      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root')); 
root.render(<LoginControl />);
```

[**Experimente no CodePen**](https://codepen.io/gaearon/pen/QKzAgB?editors=0010)

Declarar uma variável e usar uma declaração condicional `if` é uma ótima maneira de renderizar um componente, mas às vezes você pode querer usar uma sintaxe mais curta. Existem algumas maneiras para utilizar condições inline em JSX, explicadas abaixo.

##### [](https://pt-br.reactjs.org/docs/conditional-rendering.html#inline-if-with-logical--operator)If inline com o Operador Lógico &&

Você pode [incorporar expressão em JSX](https://pt-br.reactjs.org/docs/introducing-jsx.html#embedding-expressions-in-jsx) encapsulando em chaves. Isto inclui o operador lógico `&&` de JavaScript. Isto pode ser conveniente para incluir um elemento condicionalmente:

```
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&        <h2>          You have {unreadMessages.length} unread messages.        </h2>      }    </div>
  );
}

const messages = ['React', 'Re: React', 'Re:Re: React'];

const root = ReactDOM.createRoot(document.getElementById('root')); 
root.render(<Mailbox unreadMessages={messages} />);
```

[**Experimente no CodePen**](https://codepen.io/gaearon/pen/ozJddz?editors=0010)

Isto funciona porque em JavaScript, `true && expressão` são sempre avaliadas como `expressão`, e `false && expressão` são sempre avaliadas como `false`.

Portanto, se a condição é `true`, o elemento logo depois do `&&` irá aparecer no resultado. Se o elemento é `false`, React irá ignora-lo.

Observe que retornar uma expressão falsa ainda fará com que o elemento após `&&` seja pulado, mas retornará a expressão falsa. No exemplo abaixo, `<div>0</div>` será retornado pelo método de renderização.

```
render() {
  const count = 0;  return (
    <div>
      {count && <h1>Messages: {count}</h1>}    </div>
  );
}
```

######  [](https://pt-br.reactjs.org/docs/conditional-rendering.html#inline-if-else-with-conditional-operator)If-Else inline com Operador Condicional

Outro método para renderizar elementos inline é utilizar o operador condicional em JavaScript [`condição ? true : false`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Operador_Condicional).

No exemplo abaixo, nós o utilizaremos para renderizar condicionalmente um pequeno bloco de texto.

```
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      The user is <b>{isLoggedIn ? 'currently' : 'not'}</b> logged in.    </div>
  );
}
```

Pode também ser usado para expressões mais longas, embora o que está acontecendo seja menos óbvio:

```
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
      {isLoggedIn        ? <LogoutButton onClick={this.handleLogoutClick} />
        : <LoginButton onClick={this.handleLoginClick} />      }
    </div>  );
}
```

Assim como em JavaScript, você decide o estilo apropriado com base no que você e a sua equipe considera mais legível. Lembre-se que toda vez que condições se tornam muito complexas, pode ser um bom momento para [extrair componentes](https://pt-br.reactjs.org/docs/components-and-props.html#extracting-components).

######  [](https://pt-br.reactjs.org/docs/conditional-rendering.html#preventing-component-from-rendering)Evitando que um Componente seja Renderizado

Em casos raros você pode desejar que um componente se esconda ainda que ele tenha sido renderizado por outro componente. Para fazer isso, retorne `null` ao invés do resultado renderizado.

No exemplo abaixo, o `<WarningBanner />` é renderizado dependendo do valor da prop chamada `warn`. Se o valor da prop é `false`, o componente não é renderizado:

```
function WarningBanner(props) {
  if (!props.warn) {    return null;  }
  return (
    <div className="warning">
      Warning!
    </div>
  );
}

class Page extends React.Component {
  constructor(props) {
    super(props);
    this.state = {showWarning: true};
    this.handleToggleClick = this.handleToggleClick.bind(this);
  }

  handleToggleClick() {
    this.setState(state => ({
      showWarning: !state.showWarning
    }));
  }

  render() {
    return (
      <div>
        <WarningBanner warn={this.state.showWarning} />        <button onClick={this.handleToggleClick}>
          {this.state.showWarning ? 'Hide' : 'Show'}
        </button>
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root')); 
root.render(<Page />);
```