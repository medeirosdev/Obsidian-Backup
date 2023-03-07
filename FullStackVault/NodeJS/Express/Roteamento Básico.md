[[NodeJs]]
[[Express]]
O _[[Roteamento]]_ refere-se à determinação de como um aplicativo responde a uma solicitação do cliente por um [[endpoint]] específico, que é uma URI (ou caminho) e um método de solicitação HTTP específico (GET, POST, e assim por diante).

Cada rota pode ter uma ou mais funções de manipulação, que são executadas quando a rota é correspondida.

A definição de rotas aceita a seguinte estrutura:

```javascript

app.METHOD(PATH, HANDLER)
```

Onde:

-   `app` é uma instância do `express`.
-   `METHOD` é um [método de solicitação HTTP](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol).
-Ver mais sobre [[Método de solicitação HTTP]]
-   `PATH` é um caminho no servidor.
-   `HANDLER` é a função executada quando a rota é correspondida.

Este tutorial assume que uma instância de `express` chamada `app` está criada e o servidor está em execução. Caso não tenha familiaridade com a criação e inicialização de um aplicativo, consulte o [exemplo Hello world](https://expressjs.com/pt-br/starter/hello-world.html).

Os seguintes exemplos ilustram a definição de rotas simples.

Responder com `Hello World!` na página inicial:

```javascript

app.get('/', function (req, res) {
  res.send('Hello World!');
});
```

Responder a uma solicitação POST na rota raiz (`/`) com a página inicial do aplicativo:

```javascript

app.post('/', function (req, res) {
  res.send('Got a POST request');
});
```

Responder a uma solicitação PUT para a rota `/user`:

```javascript

app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user');
});
```

Responder a uma solicitação DELETE para a rota `/user`:

```javascript

app.delete('/user', function (req, res) {
  res.send('Got a DELETE request at /user');
});
```

Para obter mais detalhes sobre roteamento, consulte o [guia de roteamento](https://expressjs.com/pt-br/guide/routing.html).

# Entregando arquivos estáticos no Express

Para entregar arquivos estáticos como imagens, arquivos CSS, e arquivos JavaScript, use a função de middleware `express.static` integrada no Express.

Passe o nome do diretório que contém os ativos estáticos para a função de middleware `express.static` para iniciar a entregar os arquivos diretamente. Por exemplo, use o código a seguir para entregar imagens, arquivos CSS, e arquivos JavaScript em um diretório chamado `public`:

```javascript

app.use(express.static('public'));
```

Agora, é possível carregar os arquivos que estão no diretório `public`:

```javascript

http://localhost:3000/images/kitten.jpg
http://localhost:3000/css/style.css
http://localhost:3000/js/app.js
http://localhost:3000/images/bg.png
http://localhost:3000/hello.html
```

O Express consulta os arquivos em relação ao diretório estático, para que o nome do diretório estático não faça parte da URL.

Para usar vários diretórios de ativos estáticos, chame a função de middleware `express.static` várias vezes:

```javascript

app.use(express.static('public'));
app.use(express.static('files'));
```

O Express consulta os arquivos na ordem em que você configurar os diretórios estáticos com a função de middleware `express.static`.

Para criar um prefixo de caminho virtual (onde o caminho não existe realmente no sistema de arquivos) para arquivos que são entregues pela função `express.static`, [especifique um caminho de montagem](https://expressjs.com/pt-br/4x/api.html#app.use) para o diretório estático, como mostrado abaixo:

```javascript

app.use('/static', express.static('public'));
```

Agora, é possível carregar os arquivos que estão no diretório `public` a partir do prefixo do caminho `/static`.

```javascript

http://localhost:3000/static/images/kitten.jpg
http://localhost:3000/static/css/style.css
http://localhost:3000/static/js/app.js
http://localhost:3000/static/images/bg.png
http://localhost:3000/static/hello.html
```

Entretanto, o caminho fornecido para a função `express.static` é relativa ao diretório a partir do qual você inicia o seu `node` de processo. Se você executar o aplicativo express a partir de outro diretório, é mais seguro utilizar o caminho absoluto do diretório para o qual deseja entregar.

```javascript

app.use('/static', express.static(__dirname + '/public'));
```


# Perguntas mais frequentes

## Como eu devo estruturar meu aplicativo?

Não existe uma resposta definitiva para esta questão. A resposta depende da escala do seu aplicativo e o time que está envolvido. Para ser o mais flexível possível, o Express não faz suposições em termos de estrutura.

Rotas e outras lógicas específicas do aplicativo podem ficar em quantos arquivos quiser, em qualquer estrutura de diretórios que preferir. Visualize os seguintes exemplos para obter inspiração:

-   [Listagens de rota](https://github.com/expressjs/express/blob/4.13.1/examples/route-separation/index.js#L32-47)
-   [Mapa de rota](https://github.com/expressjs/express/blob/4.13.1/examples/route-map/index.js#L52-L66)
-   [Controladores com estilo MVC](https://github.com/expressjs/express/tree/master/examples/mvc)

Além disso, existem extensões de terceiros para o Express, que simplificam alguns desses padrões:

-   [Roteamento engenhoso](https://github.com/expressjs/express-resource)

## Como eu defino modelos?

O Express não tem noção de banco de dados. Este conceito é deixado para módulos do Node de terceiros, permitindo que você faça a interface com praticamente qualquer banco de dados.

Consulte [LoopBack](http://loopback.io/) para uma estrutura baseada no Express que é centrada em modelos.

## Como posso autenticar usuários?

Autenticação é outra área muito opinada que o Express não se arrisca a entrar. Você pode usar qualquer esquema que desejar. Para um esquema simples com nome de usuário / senha, consulte [este exemplo](https://github.com/expressjs/express/tree/master/examples/auth).


## Quais mecanismos de modelo o Express suporta?

O Express suporta qualquer mecanismo de modelo que esteja em conformidade com a assinatura `(path, locals, callback)`. Para normalizar interfaces e o armazenamento em cache de mecanismo de modelo, consulte o projeto [consolidate.js](https://github.com/visionmedia/consolidate.js) para obter suporte. Mecanismos de modelo não listados podem ainda assim suportar a assinatura do Express.

## Como manipulo respostas 404?

No Express, respostas 404 não são o resultado de um erro, portanto o middleware manipulador de erros não irá capturá-las. Este comportamento é porque uma resposta 404 simplesmente indicam a ausência de trabalho adicional para fazer; em outras palavras, o Express executou todas as funções de middleware e rotas, e descobriu que nenhuma delas respondeu. Tudo que você precisa fazer é incluir uma função de middleware no final da pilha (abaixo de todas as outras funções) para manipular uma resposta 404:

```javascript

app.use(function(req, res, next) {
  res.status(404).send('Sorry cant find that!');
});
```

## Como configuro um manipulador de erros?

Você define middlewares de manipulação de erros da mesma forma que outros middlewares, exceto que com quatro argumentos ao invés de três; especificamente com a assinatura `(err, req, res, next)`:

```javascript

app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

Para obter mais informações, consulte [Manipulação de erros](https://expressjs.com/pt-br/guide/error-handling.html).

## Como renderizar um HTML simples?

Você não faz! Não há necessidade de se “renderizar” HTML com a função `res.render()`. se você tiver um arquivo específico, use a função `res.sendFile()`. Se estiver entregando muitos ativos a partir de um diretório, use a função de middleware `express.static()`.