### Introdução

Os Padrões de Projetos nos permitem reutilizar a experiência de outros desenvolvedores que tiveram problemas semelhantes e os solucionaram.

Os [Padrões de Projetos](http://www.devmedia.com.br/curso/padroes-de-projeto-em-java/25 "Curso de Padrões de Projeto em Java - DevMedia Cursos") também fornecem um vocabulário compartilhado com outros desenvolvedores. Quando temos um vocabulário, podemos nos comunicar muito mais facilmente com outros desenvolvedores e inspirar aqueles que não conhecem os padrões a começarem a aprendê-los. Quando se comunicamos com as nossas equipes usando simplesmente o nome de um padrão de projeto estamos automaticamente comunicando não apenas o nome de um padrão, mas sim um conjunto de qualidades, características e restrições que o padrão representa. Usando simplesmente o nome do padrão já comunicamos o design que temos em mente para uma determinada tarefa, além disso, não precisamos entrar em detalhes falando o que a classe faz, como se relaciona, com quem, etc, o padrão já deixa clara a ideia de como será feito, assim podemos nos comunicar mais rapidamente e com menos espaços para mal-entendidos.

O grande objetivo dos padrões de projetos é ajudar os desenvolvedores a estruturar os seus aplicativos de maneiras mais flexíveis, fáceis de entender e manter.

Abaixo será descrito um padrão de projeto bastante importante e muito utilizado, o padrão Observer. [O padrão Observer é utilizado quando se precisa manter os objetos atualizados quando algo importante ocorre.](http://www.devmedia.com.br/padroes-de-projeto-na-pratica-observer/5001 "Video: Padrões de Projeto na Prática – Observer")

### Funcionamento

O padrão Observer funciona como assinaturas de jornais e revistas, ou seja, temos uma editora que publica as edições e pessoas que assinam os jornais ou revistas dessa editora e sempre recebem as novas edições assim que elas são publicadas. Enquanto a pessoa é assinante ela continua recebendo as edições na sua casa. Se a pessoa cancelar a assinatura do jornal ou da revista ela para de receber as edições.

O padrão Observer funciona da mesma forma, no entanto, tem-se que a editora (que publica) é o chamado SUBJECT no Padrão Observer e os assinantes (que recebem as novas publicações) são os chamados OBSERVER.

Os OBSERVERs registram-se no SUBJECT para receber atualizações quando os dados do SUBJECT são alterados. Os OBSERVERs também podem cancelar o seu registro e dessa forma não receber mais nenhuma atualização do SUBJECT.

O Diagrama de classe abaixo mostra mais detalhes sobre o funcionamento do padrão Observer.

![Diagrama de classe do Padrão Observer](http://videos.web-03.net/artigos/Higor_Medeiros/PadraoObserver_Java/PadraoObserver_Java1.jpg)  

**Figura 1:** Diagrama de classe do Padrão Observer

No diagrama de classe acima nota-se a presença da interface Subject e da sua classe concreta ConcreteSubject que define o comportamento dos objetos para se registrarem (Attach) e também para serem removidos (Detach). O ConcreteSubject é quem implementa a interface Subject, além de definir os métodos da interface ele ainda define o seu próprio estado. O método notify() será utilizado para atualizar todos os observadores registrados sempre que o seu estado mudar. Do outro lado do diagrama tem-se o Observer e o ConcreteObserver que tem o método update() que é chamado quando o estado do Subject é alterado. A classe ConcreteObserver implementa a interface Observer, definindo assim o método update().

Podemos notar que aqui há uma relação UM-PARA-MUITOS, ou seja, temos UM Subject para MUITOS Observers.

A definição formal do Padrão Observer é: “O Padrão Observer define uma dependência um-para-muitos entre os objetos de modo que quando um objeto muda de estado, todos os seus dependentes são notificados e atualizados automaticamente”.

### Princípio da Ligação Leve

O padrão Observer adere ao principio de projeto em que se busca Designs levemente ligados entre objetos que interagem, isto é, eles interagem normalmente, no entanto sabem muito pouco um do outro.

O Subject sabe apenas que um Observer implementa uma interface comum a todos os Observers (interface Observer), apenas isso. O Subject não sabe a classe concreta que a implementa e nem sabe o que ela faz ou o qualquer outra coisa a respeito. Isto fica mais claro na implementação do padrão em que, como é de praxe dos padrões, programa-se para interface e não para classes concretas.

Essa ligação leve também proporciona mais flexibilidade ao padrão, pois como pode-se notar podemos adicionar novos Observers a qualquer momento e a única coisa que o Subject dependerá continua sendo uma lista de objetos que implementam Observer. Também podemos substituir Observers em tempo de execução ou remove-los e o Subject continuará se comportando da mesma forma e sem nenhuma alteração na sua estrutura.

Além disso, se alterarmos o Subject ou o Observer nota-se que não há nenhum impacto um no outro, eles apenas precisam continuar implementando as suas interfaces.

### Implementação no Java

O Java também fornece suporte para o padrão de projeto Observer. As API’s mais gerais são a interface Observer e a classe Observable no pacote java.util. Elas são bastante semelhantes ao que foi dito aqui, porém possuem bem mais recursos que podem ajudar a vida do desenvolvedor em algumas circunstâncias.

Em geral a classe Observable é como o nosso Subject discutido anteriormente, porém Observable é uma classe e não uma interface. Alguns dos métodos do Observable são addObserver(), deleteObserver(), notifyObservers(), setChanged(). A classe Observable nada mais faz do que monitorar todos os observadores e os notificar sobre alguma alteração no estado.

A interface Observer é como se fosse a nossa classe Observer definida anteriormente, essa interface ainda possui um método update() que será chamado pelo Subject quando o estado de Subject for alterado. No método update() será passado como parâmetro o Subject (quem está fazendo a notificação) ou ainda será passado o Subject e os dados para serem processados pelo Obsever. Outra forma de trabalhar seria chamar update() passando apenas o objeto Subject e esperar que o observador “puxe” os dados da Subject, dessa maneira não passaríamos nenhum dado para o Observer e sim esperaríamos que ele pegasse os dados diretamente no Subject que foi passado.

Um detalhe importante é que antes de Subject chamar o método update() do seus assinates (Observers) deve-se chamar o método setChanged() que seta o estado interno do objeto para true, ou seja, chamando o método diz-se que o estado foi alterado e os Observadores devem ser notificados. Quando este método de Subject é chamado aciona-se o método notifyObservers() chamando o método update() de cada Observador passando o objeto e os dados alterados. Após as notificações o setChanged() é novamente setado como falso e só chamará o método notifyObservers() novamente quando for acionado.