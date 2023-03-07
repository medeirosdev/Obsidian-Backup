Estruturas de Dados é um dos tópicos mais especiais de qualquer formação nos cursos de computação. Da minha graduação, considero que ela foi tão importante quanto Algoritmos, Sistemas Operacionais e Redes. Essas quatro disciplinas formam a base para todo bom desenvolvedor de sistemas.### As Estruturas de Dados

Em Java, as estruturas de dados estão representadas na linguagem no Java Collections Framework, e você pode acessar todos os detalhes sobre ele no tutorial oficial ([link](https://docs.oracle.com/javase/tutorial/collections/index.html)).

De acordo com o Tutorial Java

> "A _collection_ — sometimes called a container — is simply an object that groups multiple elements into a single unit. Collections are used to store, retrieve, manipulate, and communicate aggregate data. Typically, they represent data items that form a natural group, such as a poker hand (a collection of cards), a mail folder (a collection of letters), or a telephone directory (a mapping of names to phone numbers)."

A seguir, vamos fazer uma breve descrição sobre o conceito, propósito e operações de cada estrutura e, sem seguida, um exemplo de implementação em Java.
### Array

É uma estrutura linear onde dados homogêneos são armazenados em espaços contínuos da memória. O acesso a cada elemento é feito através de um índice. Como parte da modernização que Java vem passando, os organizadores da linguagem adicionaram ao Collections Framework classes utilitárias que seguem o esquema de nomenclatura: **Array -> Arrays, Collection -> Collections, File -> Files** (ok, aqui não estamos falando sobre arquivos, mas você pegou a ideia, certo?).

Exemplo de código:

```java
1class ArrayDemo {
2	public static void main(String[] args) {
3		int[] arrayInteiros = new int[5];//declara um array de 5 posições, vazio
4		int[] numeros = {2,3,1,5,4};//um array com os elementos já preenchidos
5		System.out.println(numeros.length);//informa o tamanho do array, ou seja, 5
6		System.out.println(numeros[0]);//vai imprimir "2"
7		Arrays.sort(numeros);//ordena o array 
8		System.out.println(Arrays.toString(numeros));//imprime cada um dos elementos
9	}
10}
```
### Linked List

Existe um elemento "raiz", logo, cada elemento está ligado a outro. O tamanho é dinâmico e a lista pode ser "espalhada" pela memória.

Essa estrutura costuma ser negligenciada devido suas semelhanças com **ArrayList** (a interface Java **java.util.List** implementada como um array). No entanto, a principal vantagem está em listas com tamanho dinâmico que costumam crescer quando necessário. Enquanto no melhor caso da operação de adição, ambas tem custo **O(1)** (em notação _Big O_ - [https://pt.wikipedia.org/wiki/Grande-O](https://pt.wikipedia.org/wiki/Grande-O)), caso seja necessário redimensionar o array, o custo será **O(log(n))**.

```java
1class LinkedListDemo {
2	public static void main(String[] args) {
3		LinkedList<String> linkedList = new LinkedList<>(List.of("maçã", "uva", "banana"));//cria uma nova lista encadeada 
4		linkedList.push("laranja");//adiciona ao início
5		String headElement = linkedList.poll();//remove o elemento da frente
6		System.out.println("Removido: " + headElement);//imprime "Removido: laranja"
7		String collect = linkedList.stream().sorted().collect(Collectors.joining(", "));//ordena e junta numa string separada por vírgula
8		System.out.println(collect);//imprime "banana, maçã, uva"
9	}
10}
```

### Stack

Representa uma pilha (como um baralho de cartas ou livros empilhados), seguindo o algoritmo LIFO. As quatro operações principais são: **push(e)** - insere um elemento no topo; **pop()** - remove o elemento do topo; **isEmpty()** - informa verdadeiro/falso se a pilha está vazia; **peek()** - acessa o elemento do topo (sem remover).

Essa estrutura é muito usada para representações de estado ou histórico de navegação, onde o mais recente está sempre no topo.

```java
1class StackDemo {
2	public static void main(String[] args) {
3		Stack<String> history = new Stack<>();
4		history.push("Algoritmos");
5		history.push("Estruturas de Dados");  
6		history.push("Java");  
7		System.out.println("Topo: " + history.peek());  
8		String collect = String.join(", ", history);  
9		System.out.println("Todos: "+ collect);
10	}
11}
```
### Set

Representa um grupo de dados homogêneos únicos, sem repetições. Por isso, deve haver uma forma de comparar os elementos de forma a decidir se são iguais ou não. Em Java, essa comparação é feita pelos métodos **equals** e **hashcode**. As principais classes que implementam a interface **Set** são: **HashSet**, **TreeSet** e **LinkedHashSet**.

```java
1class SetDemo {
2	public static void main(String[] args) {
3		Set<String> setFrutas = new HashSet<>(List.of("maçã", "uva", "banana"));  
4		setFrutas.add("abacaxi");  
5		setFrutas.add("abacaxi"); //não adiciona o elemento repetido
6		String collect = String.join(", ", setFrutas); 
7		System.out.println("Todos: "+ collect);//Todos: banana, uva, maçã, abacaxi
8	}
9}
```

### HashMap

Usa funções hash para determinar a posição de cada elemento. Uma função hash é um algoritmo que mapeia dados de entrada de comprimento variável em dados de comprimento fixo. Assim, cada elemento a ser inserido na estrutura tem o seu endereço calculado. Isso evita "colisões" e acelera as operações de leitura.

No código a seguir, vamos contar a ocorrência de cada caractere na frase "estruturas de dados Java", desconsiderando os espaços em branco. A chave do nosso mapa, _key_, será o caractere e o valor, _value_, será o contador. Como esperado, a saída do programa será "a: 4, r: 2, s: 3, t: 2, d: 3, e: 2, u: 2, v: 1, j: 1, o: 1".

```java
1class HashMapDemo {
2	public static void main(String[] args) {
3		HashMap<Character, Integer> charCountMap = new HashMap<>();  
4		String demo = "estruturas de dados java";  
5		for (char c : demo.toCharArray()) {  
6		    if (charCountMap.containsKey(c)) {  
7		        charCountMap.put(c, charCountMap.get(c) + 1);  
8		  } else {  
9		        charCountMap.put(c, 1);  
10		  }  
11		}  
12		String collect = charCountMap.entrySet().stream()  
13		    .filter(Predicate.not(entry -> entry.getKey().equals(' ')))
14		    .map(entry -> entry.getKey() + ": " + entry.getValue())  
15		    .collect(Collectors.joining(", "));  
16		System.out.println(collect);
17	}
18}
```

No desenvolvimento de software precisamos representar conjuntos de dados. A disciplina da Ciência da Computação estuda a melhor forma de estruturar essa informação é chamada Estrutura de Dados. Elas são definidas de acordo com a natureza dos dados e as operações mais comuns pretendidas.

Em Java, as estruturas de dados estão disponíveis no Java Collection Framework. Neste artigo discutimos o que deve estar contido no repertório de um bom programador Java: Array, Linked List, Set, Stack e HashMap.

Se você se interessa por Estrutura de Dados, confira [nossos cursos](https://letscode.com.br/) e acompanhe nosso blog para mais dicas de Java!