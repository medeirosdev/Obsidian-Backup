Arquivos C# Possuem terminação .cs
[[CSharp]]
Estrutura de Código C# -> Possui diversos módulos que podem ser importados

Para importar um módulo, use `using _módulo_

Função Principal:
static void Main(string[] args){

}


- Para escrever no console

Console.Write("Hello World!");

- Para receber um input

Console.ReadLine();
string Nome = Console.ReadLine();

Para pular uma linha depois de um console write

Console.Write("Oláaaaaa\n")
ou também
Console.WriteLine("texto") -> pula a linha


Como declarar variáveis?

var meuTexto = "meutextofoda";
int numerofoda = 2;
string textofodafoda = "aoaoa";
float velocidade = 243.2;
bool verdade = true;

Não podemos ter variáveis no mesmo escopo com mesmo nome1

Para fazer comentários -> //
ou /*  */ 
Para omitir o tipo de variável, vc pode usar
var cor_favorita = "vermelha";
var numeroserial = 4223;


dynamic cor_favorita = "vermelhin";
declarando variáveis com dynamic podemos alterar o seu tipo depois!

Constantes ->

const float PI = 3.14;
const string Nome = "guilherme";





// int - inteiros positivos e negativos
// Float - 0.5 , 1.5
// STRING É ASPAS DUPLAS PORRA
// Char -> ' a '

nomes de váriveis não podem ter ESPAÇO
Não pode começar com Números!



Condicionais

if(10>2){

}else{

}



Funções
static void Somar(      ){

} 

Arrray

string[] produtos = new string[tamanho]{ valorse, valores, valores };
se vc definir o tamanho de um array, vc n pode mudar depois
jamais
também popde ser
int[] valores = { 1 , 2 , 3 , 4 , 6};


Switch

string cor = "azul";

switch(cor) {
case "vermelho":
	sua cor fav
	break;
case "azul":
	aaaa
	break;
}


Enum

Enum Cor { azul = 33 , Verde = 83 , amarelo = 178 , vermelho = 2}

Depois vc pode chamar, como type

Cor corfavorita = Cor.azul