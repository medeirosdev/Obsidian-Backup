[[middleware]]
[[NodeJS]]
[[Express]]

Funções de _Middleware_ são funções que tem acesso ao [objeto de solicitação](https://expressjs.com/pt-br/4x/api.html#req) (`req`), o [objeto de resposta](https://expressjs.com/pt-br/4x/api.html#res) (`res`), e a próxima função de middleware no ciclo solicitação-resposta do aplicativo. A próxima função middleware é comumente denotada por uma variável chamada `next`.

Funções de middleware podem executar as seguintes tarefas:

-   Executar qualquer código.
-   Fazer mudanças nos objetos de solicitação e resposta.
-   Encerrar o ciclo de solicitação-resposta.
-   Chamar o próximo middleware na pilha.

Se a atual função de middleware não terminar o ciclo de solicitação-resposta, ela precisa chamar `next()` para passar o controle para a próxima função de middleware. Caso contrário, a solicitação ficará suspensa.

O exemplo a seguir mostra os elementos de uma chamada de função de middleware:

![[Pasted image 20230201084037.png]]

Aqui está um exemplo de um simples aplicativo “Hello World” do Express, para o qual serão definidas duas funções de middleware:

```javascript

var express = require('express');
var app = express();

app.get('/', function (req, res) {
  res.send('Hello World!');
});

app.listen(3000);
```

## Desenvolvimento

Aqui está um exemplo simples de uma função de middleware chamada “myLogger”. Esta função apenas imprime “LOGGED” quando uma solicitação para o aplicativo passa por ela. A função de middleware é designada para uma variável chamada `myLogger`.

```javascript

var myLogger = function (req, res, next) {
  console.log('LOGGED');
  next();
};
```

Observe a chamada acima para `next()`. A chamada desta função chama a próxima função de middleware no aplicativo. A função `next()` não faz parte do Node.js ou da API Express, mas é o terceiro argumento que é passado para a função de middleware. A função `next()` poderia ter qualquer nome, mas por convenção ela é sempre chamada de “next”. Para evitar confusão, sempre use esta convenção.

Para carregar a função de middleware, chame `app.use()`, especificando a função de middleware. Por exemplo, o código a seguir carrega a função de middleware do `myLogger` antes da rota para o caminho raiz (/).

```javascript
var express = require('express');
var app = express();

var myLogger = function (req, res, next) {
  console.log('LOGGED');
  next();
};

app.use(myLogger);

app.get('/', function (req, res) {
  res.send('Hello World!');
});

app.listen(3000);
```

Sempre que o aplicativo recebe uma chamada, ele imprime a mensagem “LOGGED” no terminal.

A ordem de carregamento do middleware é importante: funções de middleware que são carregadas primeiro também são executadas primeiro.

Se `myLogger` é carregada após a rota para o caminho raiz, a chamada nunca chegará a ela e o aplicativo não imprimirá “LOGGED”, pois o manipulador de rota do caminho raiz encerra o ciclo de solicitação-resposta.

A função de middleware `myLogger` simplesmente imprime uma mensagem, e em seguida passa a solicitação para a próxima função de middleware na pilha chamando a função `next()`.

O próximo exemplo inclui uma propriedade chamada `requestTime` ao objeto da solicitação. Iremos chamar esta função de middleware de “requestTime”.

```javascript

var requestTime = function (req, res, next) {
  req.requestTime = Date.now();
  next();
};
```

O aplicativo agora usa a função de middleware `requestTime`. Além disso, a função de retorno de chamada do caminho raiz usa a propriedade que a função de middleware inclui no `req` (o objeto da solicitação).

```javascript

var express = require('express');
var app = express();

var requestTime = function (req, res, next) {
  req.requestTime = Date.now();
  next();
};

app.use(requestTime);

app.get('/', function (req, res) {
  var responseText = 'Hello World!';
  responseText += 'Requested at: ' + req.requestTime + '';
  res.send(responseText);
});

app.listen(3000);
```

Ao fazer uma solicitação para a raiz do aplicativo, o aplicativo agora exibe o registro de data e hora da sua solicitação no navegador.

Como você tem acesso ao objeto da solicitação, ao objeto de resposta, à próxima função de middleware na pilha, e à API completa do Node.js, as possibilidades com as funções de middleware são ilimitadas.

Para obter mais informações sobre middlewares no Express, consulte: [Usando middlewares no Express](https://expressjs.com/pt-br/guide/using-middleware.html).

https://expressjs.com/pt-br/guide/using-middleware.html
