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

![[Pasted image 20230214095639.png]]

![[Pasted image 20230214095910.png]]
Criamos um método getProducts para receber todos os produtos e transformamos eles todos em array

agora vamos alterar no showproducts, no controllers
![[Pasted image 20230214100049.png]]
vamos renderizar products/all e passar { products }


Vamos criar uma View 
![[Pasted image 20230214100223.png]]
e iterar  cada produto com suas particularidades com o handlebars, com o each

![[Pasted image 20230214101648.png]]

Vamos criar a rota post para obter e filtrar pelo ID
![[Pasted image 20230214101920.png]]

Na pasta controller, vamos definir o método da rota :id , o getProduct
![[Pasted image 20230214102141.png]]
Vamos até a pasta models e criar  o método getProductById PARA conseguirmos o id através do contato com o banco de dados
![[Pasted image 20230214102620.png]]
utilizamos um import { ObjectId } para usar

Tem alguns dados errados e faltando nos prints, o prof corrigiu depois, -> olhar projeto original

----
![[Pasted image 20230215074458.png]]
![[Pasted image 20230215074657.png]]
Crie uma Rota POST para pegar o ID do dado
Agora vamos ao controller criar o método dentro da classe
![[Pasted image 20230215074932.png]]
Nisso, precisamos agora criar o método removeProductById para remover o dado na tabela
![[Pasted image 20230215081724.png]]
--
![[Pasted image 20230215083845.png]]
Vamos criar a rota para pegar o parâmetro id na url
![[Pasted image 20230215084111.png]]
Vamos ao controller
![[Pasted image 20230215084423.png]]
Agora na view preenchers os valores com os dados recebidos para serem editados![[Pasted image 20230215084500.png]]
![[Pasted image 20230215084746.png]]
vamos salvar a edição no form
Crie a rota

![[Pasted image 20230215085327.png]]


O método da rota
![[Pasted image 20230215085313.png]]
