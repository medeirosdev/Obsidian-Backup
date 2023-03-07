Seu primeiro projeto com a API mínima foi bem recebido. Agora sua empresa quer ver um aplicativo que faz algo mais, como gerenciar um recurso. O recurso a ser usado cabe a você. Você está com fome, então que tal comer uma pizza?

## Adicionar dados

Primeiro será necessário obter alguns dados. Para armazenar e gerenciar dados, você usará um repositório na memória.

1.  Usando o Visual Studio Code, crie um arquivo chamado _Db.cs_ na raiz do projeto e forneça a ele o seguinte conteúdo:
    
    C#Copiar
    
    ```
     namespace PizzaStore.DB; 
    
     public record Pizza 
     {
       public int Id {get; set;} 
       public string ? Name { get; set; }
     }
    
     public class PizzaDB
     {
       private static List<Pizza> _pizzas = new List<Pizza>()
       {
         new Pizza{ Id=1, Name="Montemagno, Pizza shaped like a great mountain" },
         new Pizza{ Id=2, Name="The Galloway, Pizza shaped like a submarine, silent but deadly"},
         new Pizza{ Id=3, Name="The Noring, Pizza shaped like a Viking helmet, where's the mead"} 
       };
    
       public static List<Pizza> GetPizzas() 
       {
         return _pizzas;
       } 
    
       public static Pizza ? GetPizza(int id) 
       {
         return _pizzas.SingleOrDefault(pizza => pizza.Id == id);
       } 
    
       public static Pizza CreatePizza(Pizza pizza) 
       {
         _pizzas.Add(pizza);
         return pizza;
       }
    
       public static Pizza UpdatePizza(Pizza update) 
       {
         _pizzas = _pizzas.Select(pizza =>
         {
           if (pizza.Id == update.Id)
           {
             pizza.Name = update.Name;
           }
           return pizza;
         }).ToList();
         return update;
       }
    
       public static void RemovePizza(int id)
       {
         _pizzas = _pizzas.FindAll(pizza => pizza.Id != id).ToList();
       }
     }
    ```
    

Agora que você tem o armazenamento de dados, vamos fazer com que a API o use em seguida.

## Conectar dados a rotas

Para conectar seu armazenamento na memória à API, faça o seguinte:

1.  **Adicione o namespace.** Essa adição é tão simples quanto adicionar a instrução `using` apropriada.
2.  **Configure as rotas.** Certifique-se de adicionar todos os mapeamentos de rota necessários para criar, ler, atualizar e excluir.
3.  **Invoque-o nas rotas.** Por fim, você precisa chamar o repositório na memória por cada rota e passar qualquer parâmetro ou corpo da solicitação, se aplicável.

Agora conecte os dados à sua API.

1.  Na parte superior do arquivo _Program.cs_, adicione a seguinte linha de código:
    
    C#Copiar
    
    ```
    using PizzaStore.DB;
    ```
    
2.  Logo antes de `app.Run()`, adicione o código a seguir:
    
    C#Copiar
    
    ```
    app.MapGet("/pizzas/{id}", (int id) => PizzaDB.GetPizza(id));
    app.MapGet("/pizzas", () => PizzaDB.GetPizzas());
    app.MapPost("/pizzas", (Pizza pizza) => PizzaDB.CreatePizza(pizza));
    app.MapPut("/pizzas", (Pizza pizza) => PizzaDB.UpdatePizza(pizza));
    app.MapDelete("/pizzas/{id}", (int id) => PizzaDB.RemovePizza(id));
    ```
    
3.  Verifique se você salvou todas as alterações. No terminal, execute o aplicativo:
    
    BashCopiar
    
    ```
    dotnet run
    ```
    
4.  No navegador, acesse _http://localhost:{PORT}/swagger_.
    
    Você deverá ver o seguinte processamento de página:
    
    ![Criar, ler, atualizar e excluir, Swagger](https://learn.microsoft.com/pt-br/training/aspnetcore/build-web-api-minimal-api/media/swagger-crud.png)
    

É isso! Você implementou totalmente sua API mínima. Você pode usar a interface do usuário do Swagger para testar cada uma de suas rotas.

