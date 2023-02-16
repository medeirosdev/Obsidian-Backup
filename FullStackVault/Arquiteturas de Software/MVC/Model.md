[[MVC]] O model é a camada que possui a lógica da aplicação. Ele é o responsável pelas regras de negócios, persistência com o banco de dados e as classes de entidades. O model recebe as requisições vindas do controller e gera respostas a partir destas requisições.

Sempre que pensar em model, pense que ele terá conhecimento apenas dos dados armazenados no sistema e da lógica sobre eles. Estes dados podem estar armazenados em um banco de dados ou até mesmo em arquivos do tipo XML, TXT ou de qualquer outro tipo. É no model também que as operações de CRUD devem ser realizadas. Esta camada na verdade é responsável pelo motivo que a aplicação foi construída, ou seja, ela é o núcleo da aplicação.