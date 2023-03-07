[Express](https://expressjs.com/)
[[NodeJS]]
Framework web rápido, flexível e minimalista para [Node.js](http://nodejs.org/)

# Instalação

Assumindo que já tenha instalado o [Node.js](https://nodejs.org/), crie um diretório para conter o seu aplicativo, e torne-o seu diretório ativo.

```console
$ mkdir myapp
$ cd myapp
```

Use o comando `npm init` para criar um arquivo `package.json` para o seu aplicativo. Para obter mais informações sobre como o `package.json` funciona, consulte [Detalhes do tratamento de package.json do npm](https://docs.npmjs.com/files/package.json).

```console
$ npm init
```

Este comando solicita por várias coisas, como o nome e versão do seu aplicativo. Por enquanto, é possível simplesmente pressionar RETURN para aceitar os padrões para a maioria deles, com as seguintes exceções:

```console
entry point: (index.js)
```

Insira `app.js`, ou qualquer nome que deseje para o arquivo principal. Se desejar que seja `index.js`, pressione RETURN para aceitar o nome de arquivo padrão sugerido.

Agora instale o Express no diretório `myapp` e salve-o na lista de dependências. Por exemplo:

```console
$ npm install express --save
```

Para instalar o Express temporariamente não o inclua na lista de dependências, omita a opção `--save`:

```console
$ npm install express
```

Módulos do Node instalados com a opção `--save` são incluídas na lista `dependencies` no arquivo `package.json`. Posteriormente, executando `npm install` no diretório `app` irá automaticamente instalar os módulos na lista de dependências.

# Exemplo Hello World

Este é essencialmente o aplicativo mais simples do Express que é possível criar. Ele é um aplicativo de arquivo único — _não_ é o que você iria obter usando o [Gerador Express](https://expressjs.com/pt-br/starter/generator.html), que cria a estrutura para um aplicativo completo com inúmeros arquivos JavaScript, modelos Jade, e subdiretórios para vários propósitos.

Primeiro crie um diretório chamado `myapp`, mude para ele e execute o `npm init`. Em seguida instale o `express` como uma dependência, de acordo com o [guia de instalação](https://expressjs.com/pt-br/starter/installing.html).

No diretório `myapp`, crie um arquivo chamado `app.js` e inclua o seguinte código:

```javascript

const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

O aplicativo inicia um servidor e escuta a porta 3000 por conexões. O aplicativo responde com “Hello World!” à solicitações para a URL raiz (`/`) ou _rota_. Para todos os outros caminhos, ele irá responder com um **404 Não Encontrado**.

O `req` (solicitação) e `res` (resposta) são os mesmos objetos que o Node fornece, para que seja possível chamar o `req.pipe()`, `req.on('data', callback)`, e qualquer outra coisa que desejaria fazer sem o envolvimento do Express.

Execute o aplicativo com o seguinte comando:

```console
$ node app.js
```

Em seguida, carregue [http://localhost:3000/](http://localhost:3000/) em um navegador para visualizar a saída

# Gerador de aplicativos do Express

Use a ferramenta geradora de aplicativos, `express`, para rapidamente criar uma estrutura básica de aplicativo.

Instale o `express` com o comando a seguir:

```console
$ npm install express-generator -g
```

Exiba as opções de comando com a opção `-h`:

```console
$ express -h

  Usage: express [options][dir]

  Options:

    -h, --help          output usage information
        --version       output the version number
    -e, --ejs           add ejs engine support
        --hbs           add handlebars engine support
        --pug           add pug engine support
    -H, --hogan         add hogan.js engine support
        --no-view       generate without view engine
    -v, --view &lt;engine&gt; add view &lt;engine&gt; support (ejs|hbs|hjs|jade|pug|twig|vash) (defaults to jade)
    -c, --css &lt;engine&gt;  add stylesheet &lt;engine&gt; support (less|stylus|compass|sass) (defaults to plain css)
        --git           add .gitignore
    -f, --force         force on non-empty directory
```

Por exemplo, o seguinte cria um aplicativo do Express chamado _myapp_ no diretório atualmente em funcionamento:

```console
$ express --view=pug myapp

   create : myapp
   create : myapp/package.json
   create : myapp/app.js
   create : myapp/public
   create : myapp/public/javascripts
   create : myapp/public/images
   create : myapp/routes
   create : myapp/routes/index.js
   create : myapp/routes/users.js
   create : myapp/public/stylesheets
   create : myapp/public/stylesheets/style.css
   create : myapp/views
   create : myapp/views/index.pug
   create : myapp/views/layout.pug
   create : myapp/views/error.pug
   create : myapp/bin
   create : myapp/bin/www
```

Em seguida instale as dependências:

```console
$ cd myapp
$ npm install
```

No MacOS ou Linux, execute o aplicativo com este comando:

```console
$ DEBUG=myapp:* npm start
```

No Windows, use este comando:

```console
> set DEBUG=myapp:* & npm start
```

Em seguida carregue `http://localhost:3000/` no seu navegador para acessar o aplicativo.

O aplicativo gerado possui a seguinte estrutura de diretórios:

```console
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.pug
    ├── index.pug
    └── layout.pug

7 directories, 9 files
```

A estrutura de aplicativo criada pelo gerador é apenas uma das várias maneiras de estruturar aplicativos do Express. É possível utilizar esta estrutura ou modificá-la para melhor se adequar às suas necessidades.

O _Roteamento_ refere-se à determinação de como um aplicativo responde a uma solicitação do cliente por um endpoint específico, que é uma URI (ou caminho) e um método de solicitação HTTP específico (GET, POST, e assim por diante). -> [[Roteamento Básico]]

Cada rota pode ter uma ou mais funções de manipulação, que são executadas quando a rota é correspondida.