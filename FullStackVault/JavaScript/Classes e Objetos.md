[[JS]]
## O que são [[classes]] e objetos?

A linguagem JavaScript é projetada com base em um simples paradigma [[linguagem orientada a objeto]]. Um objeto é uma coleção de propriedades, e uma propriedade é uma associação entre um nome (ou _chave_) e um valor. Um valor de propriedade pode ser uma função, que é então considerada um _método_ do objeto. Além dos objetos que são pré-definidos no browser, você pode definir seus próprios objetos.**

## Objetos e propriedades
Um objeto em JavaScript tem propriedades associadas a ele. Uma propriedade de um objeto pode ser explicada como uma variável que é ligada ao objeto. Propriedades de objetos são basicamente as mesmas que variáveis normais em JavaScript, exceto pelo fato de estarem ligadas a objetos. As propriedades de um objeto definem as características do objeto. Você acessa as propriedades de um objeto com uma simples notação de ponto:

```
nomeDoObjeto.nomeDaPropriedade
```

Como as variáveis em JavaScript, o nome do objeto (que poderia ser uma variável normal) e um nome de propriedade diferem em maiúsculas/minúsculas (por exemplo, cor e Cor são propriedades diferentes). Você pode definir uma propriedade atribuindo um valor a ela. Por exemplo, vamos criar um objeto chamado `meuCarro` e dar a ele propriedades chamadas `fabricacao`, `modelo`, e `ano`, conforme mostrado a seguir:

```
var meuCarro = new Object();
meuCarro.fabricacao = "Ford";
meuCarro.modelo = "Mustang";
meuCarro.ano = 1969;
```

Propriedades não definidas de um objeto são [`undefined`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/undefined) (e não [`null`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/null)).

```
meuCarro.semPropriedade; //undefined
```

Propriedades de objetos em JavaScript podem também ser acessadas ou alteradas usando-se notação de colchetes. Objetos são às vezes chamados de _arrays associativos_, uma vez que cada propriedade é associada com um valor de string que pode ser usado para acessá-la. Então, por exemplo, você poderia acessar as propriedades do objeto `meuCarro` como se segue:

```
meuCarro["fabricacao"] = "Ford";
meuCarro["modelo"] = "Mustang";
meuCarro["ano"] = 1969;
```

Imagine que você comprou um carro recentemente e decide modelar esse carro usando programação orientada a objetos. O seu carro tem as características que você estava procurando: um motor 2.0 híbrido, azul escuro, quatro portas, câmbio automático etc. Ele também possui comportamentos que, provavelmente, foram o motivo de sua compra, como acelerar, desacelerar, acender os faróis, buzinar e tocar música. Podemos dizer que o carro novo é um _objeto_, onde suas características são seus _atributos_ (dados atrelados ao objeto) e seus comportamentos são ações ou _métodos_.

Seu carro é um objeto seu mas na loja onde você o comprou existiam vários outros, muito similares, com quatro rodas, volante, câmbio, retrovisores, faróis, dentre outras partes. Observe que, apesar do seu carro ser único (por exemplo, possui um registro único no Departamento de Trânsito), podem existir outros com exatamente os mesmos atributos, ou parecidos, ou mesmo totalmente diferentes, mas que ainda são considerados _carros_. Podemos dizer então que seu objeto pode ser classificado (isto é, seu _objeto pertence à uma classe_) como um carro, e que seu carro nada mais é que uma _instância_ dessa _classe_ chamada "carro".
![[Pasted image 20220417220602.png]]
Assim, abstraindo um pouco a analogia, uma classe é um conjunto de características e comportamentos que definem o conjunto de objetos pertencentes à essa classe. Repare que a classe em si é um conceito abstrato, como um molde, que se torna concreto e palpável através da criação de um objeto. Chamamos essa criação de [[instanciação da classe]], como se estivéssemos usando esse molde (classe) para criar um objeto.

## Encapsulamento, herança e polimorfismo: as principais características da POO

As duas bases da **POO** são os conceitos de classe e objeto. Desses conceitos, derivam alguns outros conceitos extremamente importantes ao paradigma, que não só o definem como são as soluções de alguns problemas da **programação estruturada**. Os conceitos em questão são o _encapsulamento_, a _herança_, as _interfaces_ e o _polimorfismo_.

### Encapsulamento

Ainda usando a analogia do carro, sabemos que ele possui atributos e métodos, ou seja, características e comportamentos. Os métodos do carro, como acelerar, podem usar atributos e outros métodos do carro como o tanque de gasolina e o mecanismo de injeção de combustível, respectivamente, uma vez que acelerar gasta combustível.
![[Pasted image 20220417220956.png]]
No entanto, se alguns desses atributos ou métodos forem facilmente visíveis e modificáveis, como o mecanismo de aceleração do carro, isso pode dar liberdade para que alterações sejam feitas, resultando em efeitos colaterais imprevisíveis. Nessa analogia, uma pessoa pode não estar satisfeita com a aceleração do carro e modifica a forma como ela ocorre, criando efeitos colaterais que podem fazer o carro nem andar, por exemplo.

Dizemos, nesse caso, que o método de aceleração do seu carro não é visível por fora do próprio carro. Na POO, um atributo ou método que não é visível de fora do próprio objeto é chamado de "privado" e quando é visível, é chamado de "público".

Mas então, como sabemos como o nosso carro acelera? É simples: não sabemos. Nós só sabemos que para acelerar, devemos pisar no acelerador e de resto o objeto sabe como executar essa ação sem expor como o faz. Dizemos que a aceleração do carro está _encapsulada_, pois sabemos o que ele vai fazer ao executarmos esse método, mas não sabemos como - e na verdade, não importa para o programa como o objeto o faz, só que ele o faça.

O mesmo vale para atributos. Por exemplo: não sabemos como o carro sabe qual velocidade mostrar no velocímetro ou como ele calcula sua velocidade, mas não precisamos saber como isso é feito. Só precisamos saber que ele vai nos dar a velocidade certa. Ler ou alterar um atributo encapsulado pode ser feito a partir de _getters e setters_.

Esse _encapsulamento_ de atributos e métodos impede o chamado _vazamento de escopo_, onde um atributo ou método é visível por alguém que não deveria vê-lo, como outro objeto ou classe. Isso evita a confusão do uso de variáveis globais no programa, deixando mais fácil de identificar em qual estado cada variável vai estar a cada momento do programa, já que a restrição de acesso nos permite identificar quem consegue modificá-la.
### Herança

No nosso exemplo, você acabou de comprar um carro com os atributos que procurava. Apesar de ser único, existem carros com exatamente os mesmos atributos ou formas modificadas. Digamos que você tenha comprado o modelo Fit, da Honda. Esse modelo possui uma outra versão, chamada WR-V (ou "Honda Fit Cross Style"), que possui muitos dos atributos da versão clássica, mas com algumas diferenças bem grandes para transitar em estradas de terra: o motor é híbrido (aceita álcool e gasolina), possui um sistema de suspensão diferente, e vamos supor que além disso ele tenha um sistema de tração diferente (tração nas quatro rodas, por exemplo). Vemos então que não só alguns atributos como tambm alguns mecanismos (ou métodos, traduzindo para POO) mudam, mas essa versão "cross" ainda é do modelo Honda Fit, ou melhor, _é um tipo_ do modelo

### Interface

Muitos dos métodos dos carros são comuns em vários automóveis. Tanto um carro quanto uma motocicleta são classes cujos objetos podem acelerar, parar, acender o farol etc, pois são coisas comuns a automóveis. Podemos dizer, então, que ambas as classes "carro" e "motocicleta" _são_ "automóveis".

Quando duas (ou mais) classes possuem comportamentos comuns que podem ser separados em uma outra classe, dizemos que a "classe comum" é uma _interface_, que pode ser "herdada" pelas outras classes. Note que colocamos a interface como "classe comum", que pode ser "herdada" (com aspas), porque uma interface não é exatamente um classe, mas sim um conjunto de métodos que todas as classes que herdarem dela devem possuir (implementar) - portanto, uma interface não é "herdada" por uma classe, mas sim _implementada_. No mundo do desenvolvimento de software, dizemos que uma interface é um "contrato": uma classe que implementa uma interface deve fornecer uma implementação a **todos** os métodos que a interface define, e em compensação, a classe implementadora pode dizer que ela é do tipo da interface. No nosso exemplo, "carro" e "motocicleta" são classes que implementam os métodos da interface "automóvel", logo podemos dizer que qualquer objeto dessas duas primeiras classes, como um Honda Fit ou uma motocicleta da Yamaha, são automóveis.

Um pequeno detalhe: uma interface não pode ser herdada por uma classe, mas sim implementada. No entanto, uma interface pode herdar de outra interface, criando uma hierarquia de interfaces. Usando um exemplo completo com carros, dizemos que a classe "Honda Fit Cross" herda da classe "Honda Fit", que por sua vez herda da classe "Carro". A classe "Carro" implementa a interface "Automóvel" que, por sua vez, pode herdar (por exemplo) uma interface chamada "MeioDeTransporte", uma vez que tanto um "automóvel" quanto uma "carroça" _são_ meios de transporte, ainda que uma carroça _não seja_ um automóvel.

### Polimorfismo

Vamos dizer que um dos motivos de você ter comprado um carro foi a qualidade do sistema de som dele. Mas, no seu caso, digamos que a reprodução só pode ser feita via rádio ou _bluetooth_, enquanto que no seu antigo carro, podia ser feita apenas via cartão SD e _pendrive_. Em ambos os carros está presente o método "tocar música" mas, como o sistema de som deles é diferente, a forma como o carro toca as músicas é diferente. Dizemos que o método "tocar música" é uma forma de **polimorfismo**, pois dois objetos, de duas classes diferentes, têm um mesmo método que é implementado de formas diferentes, ou seja, um método possui _várias formas_, várias implementações diferentes em classes diferentes, mas que possuem o mesmo efeito ("polimorfismo" vem do grego _poli_ = muitas, _morphos_ = forma).

## Design Patterns

Alguns problemas aparecem com tanta frequência em **POO** que suas soluções se tornaram padrões de design de sistemas e modelagem de código orientado a objeto, a fim de resolvê-los. Esses **padrões de projeto**, (ou **[[design patterns]]**) nada mais são do que formas padronizadas de resolver problemas comuns em linguagens orientadas a objetos. O livro "Design Patterns", conhecido como **Gof:Gang of Four**, é a principal referência nesse assunto, contendo os principais padrões usados em grandes projetos