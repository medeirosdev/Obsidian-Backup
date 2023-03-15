[00:00] O que é classificação? Para entendermos melhor essa tarefa de aprendizado de máquina eu apresento a você a Maria, a nova cliente da Alura Voz.

[00:12] Que possui as seguintes características: maior de 65 anos ou se é idosa ou não. 0, ela não é maior de 65 anos. Se possui cônjuge, ela não possui. Dependentes, não. Meses de contrato 0, já que ela é uma cliente nova ela não completou nenhum mês de contrato ainda.

[00:40] Telefone fixo sim, esse primeiro serviço que nós vemos que a Maria contratou. Várias linhas telefônicas não, esse serviço extra não. Serviço de internet, o tipo de internet que ela preferiu é a fibra óptica. Seguro online não, serviço adicional ela não desejou. Backup online sim. Seguro no dispositivo não.

[01:08] Suporte técnico, que é aquele suporte extra que demora menos tempo, tem uma atenção especial ela decidiu contratar, sim. A TV a cabo não. _Streaming_ de filmes sim. O tipo de contrato dela é aquele de um ano, ela tem um ano pela frente assinado com a Alura Voz. O pagamento online sim, ela prefere receber o boleto, a fatura pela internet do que receber pelos correios.

[01:43] A forma de pagamento é débito em conta, a conta mensal dela é 39,90. E o Churn? O Churn que ainda não sabemos. Será ela uma nova cliente potencial a deixar a Alura Voz ou não?

[02:01] É aí que entra a classificação, que a partir das informações que já temos, as características dos outros clientes podemos trabalhar com essas informações e conseguir prever qual é o Churn da Maria. Seja ele um Churn não, não saiu da empresa ou Churn sim, ela saiu da empresa.

[02:24] Vamos agora voltar para o Colab para entrar ainda mais sobre o que é a classificação.[00:00] Agora que já sabemos o que é de fato a classificação, mas como que ela funciona por trás do panos?

[00:12] Vamos supor que todos os nossos clientes possuem um conjunto de informações, X e Y, sendo que o X representa os dados de entrada, as características desse cliente e o Y são os dados de saída ou até melhor, os dados que desejamos classificar esses clientes.

[00:43] Vamos retomar o nosso _head_, mas uma coisa antes. Como vocês puderam observar para processamento e da transformação dos dados, passamos a ter 39 colunas e não conseguimos ver todas elas, elas aparecem minimizadas. Eu vou deixar aqui uma dica para você de como conseguir ver essas informações completas na nossa tela.

[01:13] Vamos chamar a função da biblioteca Pandas, `pd.set_option('display.max_columns', 39)`, 39 é o suficiente, é o número máximo de colunas que temos na nossa tabela. Vamos rodar e chamamos o _head_ novamente e aqui estão todas as linhas e colunas dos cinco primeiros clientes aparecendo completas para nós.

[01:56] Agora podemos entender melhor o X e o Y. Já que os nossos dados de entrada são as características desses clientes, todas essas informações são nossos conjuntos pertencentes ao vetor X, X1, X2, X3, X4 e assim por diante, até XN.

[02:17] Agora, o nosso Y é aquela variável classificadora, o dado de saída, é o no Churn, o nosso Y1. Que também pode ser YN, Y1, Y2 e assim por diante. Já que o Y é uma variável de saída, um dado de saída pode dizer da seguinte forma, temos o conjunto X e Y, o Y é o resultado de uma função desconhecida que a máquina irá aprender com o algoritmo e aplicar aos nossos dados X. Y é resultado dessa função desconhecida aplicada ao X.

[03:05] Podemos escrever da seguinte forma: `Yi = f(Xi)`, no nosso caso é o Churn, é resultado de uma função desconhecida que a máquina vai aprender a partir da entrada desses dados, do cônjuge, dependentes, telefone fixo e assim por diante.

[03:30] Agora dados as novas informações da Maria, vamos retomar, a Maria não possui cônjuge é 0, não possui dependentes, ela possui telefone fixo, ela escolheu o pagamento online, sim e assim por diante. Esse é o vetor de características da Maria:

```lua
Xmaria = [[0,0,1,1,0,0,39.90,1,0,0,0,1,0,0,0,0,1,1,1,0,0,1,1,0,0,0,0,1,0,0,1,0,0,0,1]]
```

Lembrando que é um conjunto de informações que queremos armazenar e colocamos todas as variáveis apresentadas nos slides.

[04:09] A partir dos pares X e Y da Maria, sendo que o Y ainda não sabemos, a máquina vai aplicar uma função desconhecida aproximada que ela aprendeu a partir dos dados dos outros clientes na Maria. Que aí a partir do X da Maria vai conseguir classificar em Churn _true_ ou _false_, ou sim e não.