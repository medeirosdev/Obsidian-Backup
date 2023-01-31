O que é ainda mais empolgante é a funcionalidade construída no topo do núcleo da linguagem JavaScript. As APIs (Application Programming Interfaces - Interface de Programação de Aplicativos) proveem a você superpoderes extras para usar no seu código JavaScript.
[[JS]]
APIs são conjuntos prontos de blocos de construção de código que permitem que um desenvolvedor implemente programas que seriam difíceis ou impossíveis de implementar. Eles fazem o mesmo para a programação que os kits de móveis prontos para a construção de casas - é muito mais fácil pegar os painéis prontos e parafusá-los para formar uma estante de livros do que para elaborar o design, sair e encontrar a madeira, cortar todos os painéis no tamanho e formato certos, encontrar os parafusos de tamanho correto e _depois_ montá-los para formar uma estante de livros.

Elas geralmente se dividem em duas categorias.
![[Pasted image 20220417182528.png]]
**APIs de navegadores** já vem implementadas no navegador, e são capazes de expor dados do ambiente do computador, ou fazer coisas complexas e úteis. Por exemplo:

-   A [API DOM (Document Object Model)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) permite a você manipular HTML e CSS, criando, removendo e mudando HTML, aplicando dinamicamente novos estilos para a sua página, etc. Toda vez que você vê uma janela pop-up aparecer em uma página, ou vê algum novo conteúdo sendo exibido (como nós vimos acima na nossa simples demonstração), isso é o DOM em ação.
-   A [API de Geolocalização](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation) recupera informações geográficas. É assim que o [Google Maps](https://www.google.com/maps) consegue encontrar sua localização e colocar em um mapa.
-   As APIs [Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) e [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) permite a você criar gráficos 2D e 3D animados. Há pessoas fazendo algumas coisas fantásticas usando essas tecnologias web — veja [Chrome Experiments](https://www.chromeexperiments.com/webgl) e [webglsamples](https://webglsamples.org/).
-   [APIs de áudio e vídeo](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery) como [`HTMLMediaElement` (en-US)](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement "Currently only available in English (US)") e [WebRTC](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API) permitem a você fazer coisas realmente interessantes com multimídia, tanto tocar música e vídeo em uma página da web, como capturar vídeos com a sua câmera e exibir no computador de outra pessoa (veja [Snapshot demo](http://chrisdavidmills.github.io/snapshot/) para ter uma ideia).

### [Código interpretado x compilado](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#código_interpretado_x_compilado "Permalink to Código interpretado x compilado")

Você pode ouvir os termos **interpretado** e **compilado** no contexto da programação. JavaScript é uma linguagem interpretada — o código é executado de cima para baixo e o resultado da execução do código é imediatamente retornado. Você não tem que transformar o código em algo diferente antes do navegador executa-lo.

Linguagens compiladas, por outro lado, são transformadas (compiladas) em algo diferente antes que sejam executadas pelo computador. Por exemplo, C/C++ são compiladas em linguagem Assembly, e depois são executadas pelo computador.

JavaScript é uma linguagem de programação leve e interpretada. O navegador recebe o código JavaScript em sua forma de texto original e executa o script a partir dele. Do ponto de vista técnico, a maioria dos intérpretes modernos de JavaScript realmente usa uma técnica chamada **compilação just-in-time** para melhorar o desempenho; o código-fonte JavaScript é compilado em um formato binário mais rápido enquanto o script está sendo usado, para que possa ser executado o mais rápido possível. No entanto, o JavaScript ainda é considerado uma linguagem interpretada, pois a compilação é manipulada em tempo de execução, e não antes.### [Lado do servidor x Lado do cliente](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#lado_do_servidor_x_lado_do_cliente "Permalink to Lado do servidor x Lado do cliente")

Você pode também ouvir os termos **lado do servidor (_server-side_)** e **lado do cliente (_client-side_)**, especialmente no contexto de desenvolvimento web. Códigos do lado do cliente são executados no computador do usuário — quando uma página web é visualizada, o código do lado do cliente é baixado, executado e exibido pelo navegador. Nesse módulo JavaScript nós estamos explicitamente falando sobre **JavaScript do lado do cliente**.

Códigos do lado do servidor, por outro lado, são executados no servidor e o resultado da execução é baixado e exibido no navegador. Exemplos de linguagens do lado do servidor populares incluem PHP, Python, Ruby, e ASP.NET. E JavaScript! JavaScript também pode ser usada como uma linguagem _server__-side_, por exemplo, no popular ambiente Node.js — você pode encontrar mais sobre JavaScript do lado do servidor no nosso tópico [Websites dinâmicos - Programação do lado do servidor](https://developer.mozilla.org/en-US/docs/Learn/Server-side).
### [Código dinâmico x estático](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#código_dinâmico_x_estático "Permalink to Código dinâmico x estático")

A palavra **dinâmico** é usada para descrever tanto o JavaScript _client-side_ como o _server-side_ — essa palavra se refere a habilidade de atualizar a exibição de uma página web/app para mostrar coisas diferentes em circunstâncias diferentes, gerando novo conteúdo como solicitado. Código do lado do servidor dinamicamente gera novo conteúdo no servidor, puxando dados de um banco de dados, enquanto que JavaScript do lado do cliente dinamicamente gera novo conteúdo dentro do navegador do cliente, como criar uma nova tabela HTML com dados recebidos do servidor e mostrar a tabela em uma página web exibida para o usuário. Os significados são ligeiramente diferente nos dois contextos, porém relacionados, e ambos (JavaScript _server-side_ e _client-side_) geralmente trabalham juntos.

Uma página web sem atualizações dinâmicas é chamada de **estática** — ela só mostra o mesmo conteúdo o tempo todo.
## [Como você adiciona JavaScript na sua página?](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#como_você_adiciona_javascript_na_sua_página "Permalink to Como você adiciona JavaScript na sua página?")

O JavaScript é inserido na sua página de uma maneira similar ao CSS. Enquanto o CSS usa o elemento [`<link>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/link) para aplicar folhas de estilo externas e o elemento [`<style>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/style) para aplicar folhas de estilo internas, o JavaScript só precisa de um amigo no mundo do HTML — o elemento [`<script>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/script). Vamos aprender como funciona.

### [JavaScript externo](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#javascript_externo "Permalink to JavaScript externo")

Isso funciona muito bem, mas e se nós quiséssemos colocar nosso JavaScript em um arquivo externo? Vamos explorar isso agora.

1.  Primeiro, crie um novo arquivo na mesma pasta que está o arquivo HTML de exemplo. Chame-o de `script.js` — tenha certeza de que o nome do arquivo tem a extensão `.js`, pois é assim que ele será reconhecido como JavaScript.
2.  Agora substitua o elemento atual [`<script>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/script) pelo seguinte código:
    
    
    <script src="script.js" defer></script>

### [Estratégias para o carregamento de scripts](https://developer.mozilla.org/pt-BR/docs/Learn/JavaScript/First_steps/What_is_JavaScript#estratégias_para_o_carregamento_de_scripts "Permalink to Estratégias para o carregamento de scripts")

Há um considerável número de problemas envolvendo o carregamento de scripts na ordem correta. Infelizmente, nada é tão simples quanto parece ser! Um problema comum é que todo o HTML de uma página é carregado na ordem em que ele aparece. Se você estiver usando Javascript para manipular alguns elementos da página (sendo mais preciso, manipular o [Document Object Model](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents#the_document_object_model)), seu código não irá funcionar caso o JavaScript for carregado e executado antes mesmo dos elementos HTML estarem disponíveis.

Nos exemplos acima, tanto nos scripts internos ou externos, o JavaScript é carregado e acionado dentro do cabeçalho do documento, antes do corpo da página ser completamente carregado. Isso poderá causar algum erro. Assim, temos algumas soluções para isso.
#Bizu   #Erros 
No exemplo interno, você pode ver essa estrutura em volta do código:
```
document.addEventListener("DOMContentLoaded", function() {
  ...
});
```
Isso é um _event listener_ (ouvidor de eventos_)_, que ouve e aguarda o disparo do evento "DOMContentLoaded" vindo do _browser_, evento este que significa que o corpo do HTML está completamente carregado e pronto. O código JavaScript que estiver dentro desse bloco não será executado até que o evento seja disparado, portanto, o erro será evitado (você irá [aprender sobre eventos](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events) mais tarde).

No exemplo externo, nós usamos um recurso moderno do JavaScript para resolver esse problema: Trata-se do atributo `defer`, que informa ao _browser_ para continuar renderizando o conteúdo HTML uma vez que a tag `<script>` foi atingida.

```
<script src="script.js" defer></script>
```

Neste caso, ambos script e HTML irão carregar de forma simultânea e o código irá funcionar.

#Bizu #erros
### async e defer
Esses dois recursos são muito úteis na hora de carregar o documento e impedir erros, são colocados na tag
<Script> em <head> em html.
- usando o async : os scripts carregados com este irão baixar o script sem bloquear a renderização da pág e vão executar. _Não tem ordem específica, e eles não vão impedir o carregamento da página_  O melhor uso para ele é quando há muitos scripts rodando de forma independente, e cada um atua sem precisar do outro.
- `async` deve ser usado quando houver muitos scripts rodando no _background_, e você precisa que estejam disponíveis o mais rápido possível. Por exemplo, talvez você tenha muitos arquivos de dados de um jogo para carregar que serão necessários assim que o jogo iniciar, mas por enquanto, você só quer entrar e ver a tela de carregamento, a do titulo do jogo e o _lobby_, sem ser bloqueado pelo carregamento desses scripts.
- Usando o defer, eles irão rodar na exata ordem que aparecem no head. Todos os scripts com o atributo `defer` irão carregar na ordem que aparecem na página.


- Resumindo:
-   `async` e `defer` istruem o _browser_ a baixar os scripts numa _thread_ (processo) à parte, enquanto o resto da página (o DOM, etc.) está sendo baixado e disponibilizado de forma não bloqueante.
-   Se os seus scripts precisam rodar imediatamente, sem que dependam de outros para serem executados, use `async`.
-   Se seus scripts dependem de outros scripts ou do DOM completamente disponível em tela, carregue-os usando `defer` e coloque os elementos `<script>` na ordem exata que deseja que sejam carregados.
