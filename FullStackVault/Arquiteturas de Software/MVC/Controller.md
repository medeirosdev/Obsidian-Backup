[[MVC]]
Já sabemos que as requisições são enviadas pela view e a lógica de negócios é representada pelo model. Para que haja a comunicação entre essas duas camadas de maneira organizada, é necessário construir a camada controller. Sua função é ser uma camada intermediária entre a camada de apresentação (View) e a camada de negócios (Model).

Deste modo, toda requisição criada pelo usuário deve passar pelo controller, e este então se comunica com o model. Se o model gerar uma resposta para essas requisições, ele enviará as respostas ao controller que por sua vez repassa à camada view.

O controlador serve como um intermediário que organiza os eventos da interface com usuário e os direciona para a camada de modelo, assim, torna-se possível um reaproveitamento da camada de modelo em outros sistemas já que não existe dependência entre a visualização e o modelo.
