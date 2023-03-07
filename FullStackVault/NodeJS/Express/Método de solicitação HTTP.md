[[Express]]
O protocolo HTTP define um conjunto de **métodos de requisição** responsáveis por indicar a ação a ser executada para um dado recurso. Embora esses métodos possam ser descritos como substantivos, eles também são comumente referenciados como **_HTTP Verbs (Verbos HTTP)_**. Cada um deles implementa uma semântica diferente, mas alguns recursos são compartilhados por um grupo deles, como por exemplo, qualquer método de requisição pode ser do tipo [safe](https://developer.mozilla.org/pt-BR/docs/Glossary/safe), [idempotent](https://developer.mozilla.org/pt-BR/docs/Glossary/Idempotent) ou [cacheable (en-US)](https://developer.mozilla.org/en-US/docs/Glossary/Cacheable "Currently only available in English (US)").

[`GET`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/GET)

O método `GET` solicita a representação de um recurso específico. Requisições utilizando o método `GET` devem retornar apenas dados.

[`HEAD`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/HEAD)

O método `HEAD` solicita uma resposta de forma idêntica ao método `GET`, porém sem conter o corpo da resposta.

[`POST`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/POST)

O método `POST` é utilizado para submeter uma entidade a um recurso específico, frequentemente causando uma mudança no estado do recurso ou efeitos colaterais no servidor.

[`PUT`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/PUT)

O método `PUT` substitui todas as atuais representações do recurso de destino pela carga de dados da requisição.

[`DELETE`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/DELETE)

O método `DELETE` remove um recurso específico.

[`CONNECT`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/CONNECT)

O método `CONNECT` estabelece um túnel para o servidor identificado pelo recurso de destino.

[`OPTIONS`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/OPTIONS)

O método `OPTIONS` é usado para descrever as opções de comunicação com o recurso de destino.

[`TRACE`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/TRACE)

O método `TRACE` executa um teste de chamada _loop-back_ junto com o caminho para o recurso de destino.

[`PATCH`](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods/PATCH)

O método `PATCH` é utilizado para aplicar modificações parciais em um recurso.

### GET

Essa é a requisição mais comum de todas. Através dessa requisição nós pedimos a representação de um recurso: que pode ser um arquivo html, xml, json, etc.  
Um exemlo de requisição GET seria:

```
GET /entendendo-o-net-core-parte-3-o-coreclr/ HTTP/1.1  
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)  
Host: http://gabsferreira.com  
Connection: Keep-Alive  
```

### POST

O método POST é utilizado quando queremos **criar** um recurso. Quando usamos POST, os dados vão no corpo da requisição e não na URI.

### PUT

Requisita que um recurso seja "guardado" na URI fornecida. Se o recurso já existir, ele deve ser atualizado. Se não existir, pode ser criado.

### DELETE

Exclui o recurso especificado.

### TRACE

Devolve a mesma requisição que for enviada veja se houve mudança e/ou adições feitas por servidores intermediários.

### OPTIONS

Retorna os métodos HTTP suportados pelo servidor para a URL especificada.

### PATCH

Serve para atualizar **partes** de um recurso, e não o recurso todo.

### CONNECT

Converte a requisição de conexão para um túnel TCP/IP transparente, geralmente para facilitar a comunicação criptografada com SSL (HTTPS) através de um proxy HTTP não criptografado.

### HEAD

Retorna somente os cabeçalhos de uma resposta.

### Idempotência

Alguns métodos, como o GET, podem ser chamados **diversas** vezes seguidas sem problema nenhum: a resposta será sempre a mesma. Isso porque quando fazermos uma requisição do tipo GET não estamos **alterando** nada no servidor, somente consultando informações.  
Já quando estamos fazendo um POST estamos **criando** um novo recurso.  
Sabe quando você manda atualizar a página do seu navegador e ele pergunta se você quer realmente atualizar essa página? Que ele vai reenviaar as informações e tal? Então, essa página está fazendo uma requisição do tipo POST.  
Se executarmos a mesma requisição POST duas vezes, corremos o risco de criar dois recursos iguais.  
Na maioria das vezes não queremos isso né?

Os métodos que não alteram nada no servidor e que podemos chamar várias vezes são o que chamamos de métodos **idempotentes**.

GET, OPTIONS, HEAD, PUT, TRACE, CONNECT e DELETE são idempotentes.

E ai, ficou alguma dúvida? Quer saber mais sobre algo em específico?