## 📌 State Hook

Este exemplo renderiza um contador. Quando você clica no botão, ele incrementa o valor:
![[Pasted image 20230301192252.png]]
Aqui, `useState` é um _Hook_ (nós vamos falar sobre o que isso significa em instantes). Nós o chamamos dentro de um componente funcional para adicionar alguns states locais a ele. React irá preservar este state entre re-renderizações. `useState` retorna um par: o valor do state _atual_ e uma função que permite atualizá-lo. Você pode chamar essa função a partir de um manipulador de evento ou de qualquer outro lugar. É parecido com `this.setState` em uma classe, exceto que não mescla o antigo state com o novo. (Nós iremos mostrar um exemplo comparando `useState` com `this.state` em [Utilizando o State Hook](https://pt-br.reactjs.org/docs/hooks-state.html).)

O único argumento para `useState` é o state inicial. No exemplo acima, é `0` porque nosso contador começa do zero. Perceba que diferente de `this.state`, o state não precisa ser um objeto — apesar de que possa ser se você quiser. O argumento de state inicial é utilizado apenas durante a primeira renderização.

#### [](https://pt-br.reactjs.org/docs/hooks-overview.html#declaring-multiple-state-variables)
#### Declarando múltiplas variáveis de state

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

Você provavelmente já realizou obtenção de dados (data fetching), subscrições (subscriptions) ou mudanças manuais no DOM através de componentes React antes. Nós chamamos essas operações de “efeitos colaterais” (side effects ou apenas effects) porque eles podem afetar outros componentes e não podem ser feitos durante a renderização.

O Hook de Efeito, `useEffect`, adiciona a funcionalidade de executar efeitos colaterais através de um componente funcional. Segue a mesma finalidade do `componentDidMount`, `componentDidUpdate`, e `componentWillUnmount` em classes React, mas unificado em uma mesma API. (Nós mostraremos exemplos comparando `useEffect` com esses métodos em [Utilizando o Hook de Efeito](https://pt-br.reactjs.org/docs/hooks-effect.html).)
![[Pasted image 20230301195008.png]]
Quando você chama `useEffect`, você está dizendo ao React para executar a sua função de “efeito” após liberar as mudanças para o DOM. Efeitos são declarados dentro do componente, para que eles tenham acesso as suas props e state. Por padrão, React executa os efeitos após cada renderização — _incluindo_ a primeira renderização. (Falaremos mais sobre como isso se compara aos ciclos de vida das classes em [Utilizando o Hook de Efeito](https://pt-br.reactjs.org/docs/hooks-effect.html).)

Efeitos também podem opcionalmente especificar como “limpar” (clean up) retornando uma função após a execução deles. Por exemplo, este componente utiliza um efeito para se subscrever ao status online de um amigo e limpa-se (clean up) cancelando a sua subscrição:
![[Pasted image 20230301195056.png]]
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

> Explicação Detalhada
> 
> Você pode aprender mais sobre `useEffect` na sua página dedicada: [Utilizando o Hook de Efeito](https://pt-br.reactjs.org/docs/hooks-effect.html).