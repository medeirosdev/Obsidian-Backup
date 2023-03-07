# Saiba como adicionar rotas e usar outros comandos avançados

Concluído100 XP

-   4 minutos

Agora você sabe mais sobre o que é a API mínima e porque deve usá-la. Mas como criar seu aplicativo e lidar com coisas como parâmetros de rota, corpos postados e retorno de dados mais avançados do que uma cadeia de caracteres literal?

Para dar suporte às APIs RESTful, você precisa dar suporte ao uso de verbos HTTP e anexar esses verbos a rotas diferentes. Verbos diferentes têm significados diferentes. Respeite os significados dos verbos HTTP.

![[Pasted image 20230306105021.png]]

## Verbos HTTP na API mínima

Quando um cliente inicia uma solicitação, ele faz isso em direção a um ponto de extremidade do servidor. Imagine uma solicitação feita para o `GET http://localhost:3000/products`. O servidor verifica a solicitação para ver qual verbo HTTP é usado. Ele também precisa saber para onde está indo, o que é indicado por “/products”. O servidor tenta resolver a solicitação produzindo uma resposta.

 Observação

Como parte de uma solicitação, o servidor também pode tentar verificar as credenciais de autenticação enviadas pelo cliente. Essa atividade está fora do escopo deste módulo.

Uma API mínima manipula rotas e verbos HTTP oferecendo métodos de conveniência. Você pode mapear uma solicitação por rota e verbo HTTP, com a rota sendo "/products", em uma solicitação para `localhost:3000/products`. Veja um exemplo desse método de conveniência:

C#Copiar

```
app.MapGet("/products", () => data);
```

Esse código deve ser lido como se o cliente usasse o verbo HTTP GET para a rota `"/products"` e, em seguida, respondesse com `data`.

### GET: buscar um recurso

É bom conhecer dois casos principais quando o assunto é roteamento com solicitações GET:

-   **Somente a rota:** é uma rota que você já viu. Por exemplo:
    
    C#Copiar
    
    ```
    app.MapGet("/products", () => data);
    ```
    
-   **Usar um parâmetro de rota:** um parâmetro de rota é usado para localizar um recurso específico. Se "/products" significa uma lista de todos os produtos, `/products/1` indica um registro específico. O identificador exclusivo tem o valor _1_. Para lidar com essa solicitação, você precisa usar um curinga para fazer a correspondência. Usamos "{ID}" para capturar o "1" no exemplo anterior. Você também pode mapear o valor capturado para um parâmetro:
    
    C#Copiar
    
    ```
    app.MapGet("/products/{id}", (int id) => data.SingleOrDefault(product => product.Id == id));
    ```
    
    Nesse código, o parâmetro `id` capturou o parâmetro de rota que o cliente enviou, que é o _1_ em `/products/1`.

### POST: criar um recurso

Geralmente, você também deseja criar um recurso. Para a criação, você usaria o verbo HTTP POST. O método a ser usado é chamado `MapPost()`:

C#Copiar

```
app.MapPost("/products", (Product product) => /**/);
```

Observe como `product` é enviado para o lambda que manipula a solicitação. Imagine o JSON a seguir como o corpo enviado pelo cliente e que foi serializado pela estrutura. Imagine que o cliente enviou o seguinte JSON como seu corpo:

JSONCopiar

```
{
  "Name" : "New product",
  "Description": "a description"
}
```

Em seguida, esse JSON pode mapear esses campos para uma instância de objeto com a mesma forma. Veja uma classe `Product`, que corresponde ao corpo postado descrito:

C#Copiar

```
public record Product(int Id, string Name); 
```


### PUT: atualizar um recurso

O verbo PUT é usado para atualizar um recurso. A estrutura tem o método `MapPut()` por esse motivo. O método `MapPut()` é semanticamente semelhante a `MapPost()`. A ideia é que você, como um cliente, deve enviar um corpo postado com um recurso que contenha alterações. Você precisa que essas alterações sejam aplicadas a um recurso existente no servidor. Veja como usar `MapPut()`:

C#Copiar

```
app.MapPut("/products", (Product product) => /* Update the data store using the `product` instance */);
```

### DELETE: remover um recurso

Para dar suporte ao verbo HTTP DELETE, use `MapDelete()`. A ideia é que o cliente envie por um identificador exclusivo que ajudaria o servidor a identificar qual registro deve excluir. Veja um uso típico desse método:

C#Copiar

```
app.MapDelete("/products/{id}", (int id) => /* Remove the record whose unique identifier matches `id` */);
```

### Retornar uma resposta

Por padrão, quando você responde a certos tipos, a estrutura consegue reconhecer que esses tipos devem ser serializados como JSON. Veja alguns casos:

C#Copiar

```
app.MapGet("/products", () => products);
app.MapGet("/products/{id}", (int id) => products.SingleOrDefault(product => product.Id == id));
app.MapGet("/product", () => new { id = 1 });
```

Nesses casos, você recebe respostas JSON semelhantes a estes exemplos:

JSONCopiar

```
// app.MapGet("/products", () => products);
[{
  "id": 1,
  "name": "a product"
}, {
  "id": 2,
  "name": "another product"
}]

// app.MapGet("/products/{id}", (int id) => products.SingleOrDefault(product => product.Id == id));
[{
  "id": 1,
  "name": "a product"
}]

// app.MapGet("/product", () => new { id = 1 });
{
  "id": 1
}
```

Na próxima unidade, você adicionará rotas à API mínima.

