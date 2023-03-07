[[Express]]
Imagine uma rede de internet, corporativa ou em sua residência mesmo. Nela, estão conectados diversos dispositivos, como computadores, notebooks, smartphones e tablets. Estes aparelhos, sejam móveis ou não, são considerados endpoints. Neste artigo, te explico o que é e como gerenciar e cuidar da segurança de uma estrutura de endpoint.![[Pasted image 20230131184602.png]]

Para entender mais detalhadamente o que é um endpoint, é preciso entender o que significa o termo: em tradução livre, seria algo como “ponto de extremidade” ou “ponto final”. Por consequência, todo dispositivo que está conectado em alguma rede é um endpoint. Em geral, a expressão é usada por equipes de TI que gerenciam redes corporativas.

Equipamentos que são usados como intermediários numa conexão, por exemplo, roteadores, switches ou gateways de rede não são considerados endpoints.

## Segurança para endpoints

Por se tratar de um dispositivo conectado à rede, um endpoint transfere dados e, por isso, está sujeito a falhas de seguranças e ataques virtuais. Dessa forma, é importante que haja um bom gerenciamento de segurança da informação.

Um _**endpoint**_ de um _web service_ é a URL onde seu serviço pode ser acessado por uma aplicação cliente.

Uma _**API**_ é um conjunto de rotinas, protocolos e ferramentas para construir aplicações.

**_API_s podem existir sem _endpoints_**. Na [lista de APIs do windows](https://docs.microsoft.com/en-us/windows/win32/apiindex/windows-api-list) você pode verificar que a grande maioria trata de conteúdo local - como exibir janelas, ou como gerenciar o _input_ de teclado e mouse.

**_Endpoints_ também podem existir sem _API_s**. Imagine uma implementação simples, que retorna apenas a data e hora do servidor; a simplicidade da operação não exige a implementação de uma _API_ exclusivamente para isso.

Hoje em dia é comum se referir a uma coleção de _endpoints_ pertencentes a um dado serviço como _API_, por proximidade e acoplamento; em muitos casos o serviço é desenhado e planejado tendo em mente a exposição via _endpoints_.

Um modelo típico de implementação pode ser interpretado assim:

[![inserir a descrição da imagem aqui](https://i.stack.imgur.com/YyYgT.png)](https://i.stack.imgur.com/YyYgT.png)

Onde _endpoints_ são interfaces entre a _API_ e a aplicação consumidora.