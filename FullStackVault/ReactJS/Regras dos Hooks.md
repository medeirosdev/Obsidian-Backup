Hooks são funções JavaScript, mas eles impões duas regras adicionais:

-   Apenas chame Hooks **no nível mais alto**. Não chame Hooks dentro de loops, condições ou funções aninhadas.
-   Apenas chame Hooks **de componentes funcionais**. Não chame Hooks de funções JavaScript comuns. (Há apenas um outro lugar válido para se chamar Hooks — dentro dos seus próprios Hooks customizados. Iremos aprender sobre eles em breve.)

Nós fornecemos um [plugin de linter](https://www.npmjs.com/package/eslint-plugin-react-hooks) para assegurar essas regras automaticamente. Entendemos que essas regras podem parecer limitantes ou confusas a princípio, mas são essenciais para fazer com que os Hooks funcionem bem.

> Explicação Detalhada
> 
> Você pode aprender mais sobre essas regras na sua página dedicada: [Regras dos Hooks](https://pt-br.reactjs.org/docs/hooks-rules.html).### Use Hooks Apenas no Nível Superior

**Não use Hooks dentro de loops, regras condicionais ou funções aninhadas (funções dentro de funções).** Em vez disso, sempre use Hooks no nível superior de sua função React, antes de qualquer retorno antecipado. Seguindo essas regras, você garante que os Hooks serão chamados na mesma ordem a cada vez que o componente renderizar. É isso que permite que o React preserve corretamente o estado dos Hooks quando são usadas várias chamadas a `useState` e `useEffect` na mesma função. (Se você ficou curioso, iremos explicar isso melhor [abaixo](https://pt-br.reactjs.org/docs/hooks-rules.html#explanation).)

### [](https://pt-br.reactjs.org/docs/hooks-rules.html#only-call-hooks-from-react-functions)Use Hooks Apenas Dentro de Funções do React

**Não use Hooks dentro de funções JavaScript comuns.** Em vez disso, você pode:

-   ✅ Chamar Hooks em componentes React.
-   ✅ Chamar Hooks dentro de Hooks Customizados (Nós iremos aprender sobre eles [na próxima página.](https://pt-br.reactjs.org/docs/hooks-custom.html)).

Seguindo essas regras, você garante que toda lógica de estado (`state`) no componente seja claramente visível no código fonte.

## [](https://pt-br.reactjs.org/docs/hooks-rules.html#eslint-plugin)ESLint Plugin

Nós liberamos um plugin ESLint chamado [`eslint-plugin-react-hooks`](https://www.npmjs.com/package/eslint-plugin-react-hooks) que aplica essas duas regras. Se você desejar pode adicionar este plugin ao seu projeto, dessa forma:

Esse plugin está incluindo por padrão no [Create React App](https://pt-br.reactjs.org/docs/create-a-new-react-app.html#create-react-app).

```
npm install eslint-plugin-react-hooks --save-dev
```

```
// Sua Configuração ESLint

{
  "plugins": [
    // ...
    "react-hooks"
  ],
  "rules": {
    // ...
    "react-hooks/rules-of-hooks": "error", // Verifica as regras dos Hooks
    "react-hooks/exhaustive-deps": "warn" // Verifica as dependências de effects
  }
}
```

**Você pode pular para próxima página agora, onde explicamos melhor como escrever [seus próprios Hooks](https://pt-br.reactjs.org/docs/hooks-custom.html).** Nessa página continuaremos explicando o motivo por trás dessas regras.

## [](https://pt-br.reactjs.org/docs/hooks-rules.html#explanation)Explicação

Assim como [aprendemos anteriormente](https://pt-br.reactjs.org/docs/hooks-state.html#tip-using-multiple-state-variables), nós podemos usar diversos Hooks (States ou Effects) em um único componente:

```
function Form() {
  // 1. Use a variável de estado (state) name
  const [name, setName] = useState('Mary');

  // 2. Use um efeito para persistir o formulário
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });

  // 3. Use a variável de estado (state) surname
  const [surname, setSurname] = useState('Poppins');

  // 4. Use um efeito para atualizar o título
  useEffect(function updateTitle() {
    document.title = name + ' ' + surname;
  });

  // ....
}
```

Agora, como o React sabe qual o estado (`state`) correspondente ao `useState` chamado? A resposta é que o **React depende da ordem em que os Hooks são chamados.** Nosso exemplo funciona porque a ordem de chamada dos Hooks é a mesma sempre que o componente é renderizado:

```
// ------------
// Primeira renderização
// ------------
useState('Mary')           // 1. Inicializa a variável de estado (state) name com 'Mary'
useEffect(persistForm)     // 2. Adiciona um efeito para persistir o formulário
useState('Poppins')        // 3. Inicializa a variável de estado (state) surname com 'Poppins'
useEffect(updateTitle)     // 4. Adiciona um efeito para atualizar o título

// -------------
// Segunda renderização
// -------------
useState('Mary')           // 1. Lê a variável de estado (state) name (argumento ignorado)
useEffect(persistForm)     // 2. Substitui o efeito para persistir no formulário
useState('Poppins')        // 3. Lê a variável de estado (state) surname (argumento ignorado)
useEffect(updateTitle)     // 4. Substitui o efeito que atualiza o título

// ...
```

Enquanto a ordem dos Hooks chamados for a mesma entre as renderizações, o React pode associar um estado (`state`) local a cada um deles. Mas o que acontece se colocarmos uma chamada de Hook (por exemplo, o efeito `persistForm`) dentro de uma condição?

```
// 🔴 Nós estaremos quebrando a primeira regra por usar um Hook dentro de uma condição
if (name !== '') {
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });
}
```

A condição `name !== ''` é `true` na primeira renderização, então chamamos o Hook dentro da condição. Entretanto, na próxima renderização o usuário pode limpar o formulário, fazendo com que a condição seja `false`. Agora que pulamos este Hook durante a renderização, a ordem das chamadas dos Hooks foi alterada:

```
useState('Mary')           // ✅  1. Lê a variável de estado (state) name (argumento é ignorado)
// useEffect(persistForm)  // 🔴  Agora, este Hook foi ignorado!
useState('Poppins')        // 🔴  Na ordem era pra ser 2 (mas foi 3). Falha ao ler a variável de estado (state) surname
useEffect(updateTitle)     // 🔴  Na ordem era pra ser 3 (mas foi 4). Falha ao substituir o efeito
```

O React não saberia o que retornar na segunda chamada do Hook `useState`. O React esperava que a segunda chamada de Hook nesse componente fosse ao efeito `persistForm`, assim como aconteceu na renderização anterior, mas a ordem foi alterada. A partir daí, toda vez que um Hook for chamado depois daquele que nós pulamos, o próximo também se deslocaria, levando a erros.

**É por isso que os Hooks devem ser chamados no nível superior de nosso componente.** Se nós queremos executar um efeito condicional, nós podemos colocar a condição _**dentro**_ de nosso Hook:

```
useEffect(function persistForm() {
  // 👍  Legal! Agora não quebramos mais a primeira regra.
  if (name !== '') {
    localStorage.setItem('formData', name);
  }
});
```

**Note que você não precisa se preocupar com esse problema, se você usar a [regra fornecida no plugin do ESLint](https://www.npmjs.com/package/eslint-plugin-react-hooks)**. Mas agora você também sabe o _porquê_ dos Hooks funcionarem dessa maneira, e quais os problemas que essas regras previnem.