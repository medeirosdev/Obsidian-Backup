- First : Crie as pastas com a arquitetura desejada, no caso crie as pastas:
- public, controllers, routes, models, db e views


- Primeiramente vá em Routes e crie a primeira Rota, e já coloque um direcionamento para a pasta controllers, já que os métodos dessa rota ficarão na pasta controller,
- Lembre-se de importar o model, router, controller no INDEX.JS
![[Pasted image 20230213135116.png]]
Depois vá até a pasta controllers
Crise uma classe desejada e crie métodos static dentro dessa classe, para depois ser chamada nas routers
![[Pasted image 20230213135320.png]]
Você pode ter criado a pasta products dentro de views com o template all dentro pra colocar, pode ser antes ou depois
Crie a conexão com o banco de dados!
![[Pasted image 20230214085018.png]]
O Models define o que vai ser tratado no projeto

## Como vamos inserir dados no banco de dados MongoDB
é um pouco diferente do sequelize
![[Pasted image 20230214085407.png]]
Criar o Models
![[Pasted image 20230214085951.png]]
Nesse caso, usaremos um método diferente do SQL, aqui usaremos métodos para inserir e criar a collection( como se fosse a tabela do SQL)

Crie no controller um método para visualizar a rota de criação do model
![[Pasted image 20230214090212.png]]
o createproduct irá renderizar a view de criar / registrar um produto
No arquivo de rotas, crie a rota através do router para ser exportado depois
![[Pasted image 20230214090344.png]]
veja, router.get('/create' + método create product) nessa view, no /create, irá herdar todos os métodos do createproduct

Agora crie a view 'create' com um formulário com método POST, com esse método forms irá enviar dados para uma rota, e no caso, teremos que criar uma rota POST na mesma /create para pegar esses métodos
![[Pasted image 20230214090727.png]]

agora vamos CAPTURAR essas informações do form 
Crie uma rota POST e já inseria o controller.métodonamepost
![[Pasted image 20230214091454.png]]
E agora vamos caracterizar eses método createProductPost e criar ele no arquivo controllers
![[Pasted image 20230214091716.png]]
nesse pegamos cada informação , juntamos num novo objeto e salvamos, esses métodos, o new product e o save( ) foram alterados lá atrás no Models