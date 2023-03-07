https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/7-exercise-razor-binding?pivots=vscode
[[Blazor]]
## Criar a página ToDo

1.  Criar a página ToDo:
    
    Com o Visual Studio Code e outros editores de texto, é possível criar o componente Razor na linha de comando com esta instrução:
    
    CLI do .NETCopiar
    
    ```
    dotnet new razorcomponent -n Todo -o Pages
    ```
    
    A opção `-n|--name` no comando anterior especifica o nome do novo componente Razor. O componente é criado na pasta `Pages` do projeto com a opção `-o|--output`.
    
     Importante
    
    Os nomes de arquivo do componente Razor exigem a primeira letra em maiúscula. Abra a pasta `Pages` e confirme se o nome de arquivo do componente `Todo` começa com uma letra maiúscula `T`. O nome de arquivo será `Todo.razor`.
    
2.  Abra o componente `Todo` e adicione uma diretiva `@page` do Razor ao início do arquivo com a URL relativa `/todo`.
    
    CSHTMLCopiar
    
    ```
    @page "/todo"
    
    <h3>Todo</h3>
    
    @code {
    
    }
    ```
    
3.  Salve o arquivo `Pages/Todo.razor`.

## Adicione o componente Todo à barra de navegação

O componente `NavMenu` é usado no layout do aplicativo. Layouts são componentes que permitem evitar a duplicação de conteúdo em um aplicativo. O componente `NavLink` fornece uma indicação na interface do usuário do aplicativo quando a URL do componente é carregada pelo aplicativo.

Na seção `<nav>...</nav>` do componente NavMenu, adicione o novo `<div>...</div>` a seguir e o componente `NavLink` ao componente `Todo`.

Em `Shared/NavMenu.razor`:

razorCopiar

```
<div class="@NavMenuCssClass" @onclick="ToggleNavMenu">
    <nav class="flex-column">

        ...

        <div class="nav-item px-3">
            <NavLink class="nav-link" href="todo">
                <span class="oi oi-list-rich" aria-hidden="true"></span> Todo
            </NavLink>
        </div>
    </nav>
</div>
```

Salve o arquivo `Shared/NavMenu.razor`. O navegador será atualizado automaticamente e agora terá a entrada Todo na barra de navegação:

![Elemento de navegação Todo adicionado.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/todo-nav.png)

## Criar um item Todo

Crie um arquivo na raiz do projeto (a pasta `BlazorApp`) chamado `TodoItem.cs` para manter uma classe C# que representa um item de tarefa pendente.

Use o seguinte código de C# para a classe `TodoItem`. Declare o `Title` como uma cadeia de caracteres que permite valor nulo usando `?`.

C#Copiar

```
public class TodoItem
{
    public string? Title { get; set; }
    public bool IsDone { get; set; } = false;
}
```

Você poderá precisar parar e reiniciar o processo `dotnet watch run` se ele não detectar o novo arquivo `TodoItem` e recompilar o projeto.

## Associar uma lista de TodoItems

Agora você está pronto para associar uma coleção de objetos `TodoItem` ao HTML no Blazor. Para isso, aplique as seguintes alterações ao arquivo `Pages/Todo.razor`:

-   Adicione um campo para os itens de tarefas pendentes ao bloco `@code`. O componente `Todo` usa esse campo para manter o estado da lista de tarefas pendentes.
-   Adicione marcação da lista não ordenada e um loop `foreach` para renderizar cada item de tarefa pendente como um item de lista (`<li>`).

CSHTMLCopiar

```
@page "/todo"

<h3>Todo</h3>

<ul>
    @foreach (var todo in todos)
    {
        <li>@todo.Title</li>
    }
</ul>

@code {
    private List<TodoItem> todos = new();
}
```

## Adicionar elementos de formulário para criar listas de tarefas pendentes

1.  O aplicativo requer elementos de interface do usuário para adicionar itens de tarefas à lista. Adicione uma entrada de texto (`<input>`) e um botão (`<button>`) abaixo da lista não ordenada (`<ul>...</ul>`):
    
    razorCopiar
    
    ```
    @page "/todo"
    
    <h3>Todo</h3>
    
    <ul>
        @foreach (var todo in todos)
        {
            <li>@todo.Title</li>
        }
    </ul>
    
    <input placeholder="Something todo" />
    <button>Add todo</button>
    
    @code {
        private List<TodoItem> todos = new();
    }
    ```
    
2.  Nada acontece quando o botão `Add todo` é selecionado, porque nenhum manipulador de eventos está anexado ao botão.
    
    Adicione um método `AddTodo` ao componente `Todo` e registre o método para o botão usando o atributo `@onclick`. O método C# `AddTodo` é chamado quando o botão é selecionado:
    
    razorCopiar
    
    ```
    <input placeholder="Something todo" />
    <button @onclick="AddTodo">Add todo</button>
    
    @code {
        private List<TodoItem> todos = new();
    
        private void AddTodo()
        {
            // Todo: Add the todo
        }
    }
    ```
    
3.  Para obter o título do novo item de tarefa pendente, adicione um campo de cadeia de caracteres `newTodo` no início do bloco `@code`:
    
    razorCopiar
    
    ```
    @code {
        private List<TodoItem> todos = new();
        private string? newTodo;
    
        // ... code continues ...
        }
    ```
    
    Modifique o elemento `<input>` para associar `newTodo` ao atributo `@bind`:
    
    razorCopiar
    
    ```
    <input placeholder="Something todo" @bind="newTodo" />
    ```
    
4.  Atualize o método `AddTodo` para adicionar o `TodoItem` com o título especificado à lista. Limpe o valor da entrada de texto configurando `newTodo` para uma cadeia de caracteres vazia:
    
    razorCopiar
    
    ```
    @page "/todo"
    
    <h3>Todo</h3>
    
    <ul>
        @foreach (var todo in todos)
        {
            <li>@todo.Title</li>
        }
    </ul>
    
    <input placeholder="Something todo" @bind="newTodo" />
    <button @onclick="AddTodo">Add todo</button>
    
    @code {
        private List<TodoItem> todos = new();
        private string? newTodo;
    
        private void AddTodo()
        {
            if (!string.IsNullOrWhiteSpace(newTodo))
            {
                todos.Add(new TodoItem { Title = newTodo });
                newTodo = string.Empty;
            }
        }
    }
    ```
    
5.  Salve o arquivo `Pages/Todo.razor`. O aplicativo é recompilado automaticamente no shell de comando. A página será recarregada no navegador depois que o navegador se reconectar ao aplicativo.
    
6.  É possível tornar o texto do título de cada item de tarefa pendente editável e adicionar uma caixa de seleção para ajudar o usuário a acompanhar os itens concluídos. Adicione uma entrada de caixa de seleção para cada item de tarefa pendente e associe o valor dele à propriedade `IsDone`. Altere `@todo.Title` para um elemento `<input>` associado a `todo.Title` com `@bind`:
    
    razorCopiar
    
    ```
    <ul>
        @foreach (var todo in todos)
        {
            <li>
                <input type="checkbox" @bind="todo.IsDone" />
                <input @bind="todo.Title" />
            </li>
        }
    </ul>    
    ```
    
7.  Atualize o cabeçalho `<h3>` para mostrar uma contagem do número de itens de tarefas pendentes que não foram concluídos (`IsDone` é `false`).
    
    razorCopiar
    
    ```
    <h3>Todo (@todos.Count(todo => !todo.IsDone))</h3>
    ```
    
8.  Salve o arquivo `Pages/Todo.razor`. O aplicativo é recompilado automaticamente no shell de comando. A página será recarregada no navegador depois que o navegador se reconectar ao aplicativo.
    
9.  Adicione, edite e marque itens de tarefas pendentes como concluídos para testar o componente.
    
    ![Página Todo concluída.](https://learn.microsoft.com/pt-br/training/modules/build-blazor-webassembly-visual-studio-code/media/todo-complete.png)
    

---


