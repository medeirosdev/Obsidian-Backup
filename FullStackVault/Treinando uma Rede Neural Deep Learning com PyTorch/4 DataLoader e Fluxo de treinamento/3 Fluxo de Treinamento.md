[00:00] Vamos agora para a parte principal, que é fazer o fluxo de treinamento completo para um problema real. Estávamos trabalhando com um dataset de dígitos, que vai de 0 a 9, e já carregamos o dataloader, que vai fazer o trabalho de dividir em batch, embaralhar os dados, gerenciando a fila de dados.

[00:34] Precisamos implementar o MLP, definir a loss e o otimizador e fazer o fluxo de treinamento, como aprendemos. Para garantir a convergência do modelo, ao final de cada época vamos imprimir a média e o desvio padrão da perda de cada iteração.

[01:10] Vou pegar um MLP que usamos em outras aulas que com poucas modificações conseguimos implementar no nosso problema. Vou chamar de self features. Ao invés de colocar cada camada em uma variável, vou criar um sequential, colocando dentro minha rede. Posso colocar minhas camadas dentro.

[02:00] Se você quiser colocar mais um par de camada linear e ativação posso fazer isso e ficamos com uma rede mais complexa. Só tenho que garantir que as dimensões dela vão bater. A primeiro camada vai receber input_size e vai transformar numa saída hidden_size.

[02:16] Posso criar outra camada que vai transformar a saída da última camada em feature de qualquer tamanho. Depois temos o output e o softmax para fazer a classificação.

[02:38] A única coisa que tenho que mudar é que vou fazer o forward na minha sequência de features. Ele já vai fazer o forward em todas as camadas. Só o que falta mudar são essas informações. Vamos ter que linearizar o tamanho da entrada, isso é muito importante, porque redes neurais só aceitam dados em uma dimensão.

[03:41] Quando vamos fazer o forward da nossa entrada, para conseguir passar na camada linear temos que linearizar o x. Se a entrada está vindo na forma 1 por 28 por 28, temos que transformar isso em um extensor de 20 por uma unidade dimensão. O que fazemos aqui é simplesmente um view no x. Ele vai redimensionar. Mantenho a primeira dimensão, mas lineariza o resto. Isso já deve funcionar.

[05:17] Criamos nossa rede a partir de uma implementação que tínhamos feito antes. Como se trata de um problema de classificação de múltiplas classes, é só colocar o loss em crossentropy, e vai entender. O otimizador sabemos que a regra de ouro é usar o adam. Ele vai mostrar para gente a implementação. É importante destacar que por padrão a regularização está com valor zero. Eu considero importante colocar um valor porque ajuda a convergir muito mais rápido.

[06:55] No nosso dicionário de hiper parâmetros, colocamos uma taxa de aprendizado de 10-4 e um weight decay de 5e-4. Eu defini esses parâmetros, testei e coloquei aqui. Mas é o que conversamos. Ou você experimenta diferentes valores ou usa métodos que irão encontrar.

[07:35] No fluxo de treinamento, só temos que ir liberando as épocas. Para cada época, vamos treinar nosso modelo, que é fazer o batch dos dados. Iremos fazer o cast na GPU. Dado recebe dado.to args device. E o mesmo para o rótulo. Forward tem pred igual a net dado. Loss recebe critério entre a predição e o rótulo. Lembrando que definimos lá em cima a crossEntropy como critério de perda.

[09:15] Vou criar uma lista com as loss da época para imprimir a loss média no final. Precisamos tirar a informação da CPU, para liberar só os valores disso. Tenho que chamar o .cpu para que esse dado saia da CPU e consiga fazer cálculos nela normalmente.

[09:48] Falta só o backward, que é quando calculamos os gradientes, e com o optimizer.step para fazer otimização de pesos. Para acompanhar a convergência, ao final de cada época, vamos converter o epoch_loss em array, e vamos imprimir as informações.

[11:35] Como colocamos uma taxa de aprendizagem baixinha, ele vai reduzindo até chegar em um ponto de otimização bom. Como ainda não estamos fazendo treino e teste, não vou colocar métricas mais interpretáveis, mas no próximo vídeo iremos trabalhar com acurácia. Eu até coloquei uma forma de interpretar a qualidade do seu modelo. Iremos fazer isso quando estiver trabalhando com teste, que é uma medida diferente da loss, porque por mais que ela seja útil, ela não é tão interpretável.

[12:44] Aqui já dá para ver que ele está convergindo. Fizemos tudo certinho nos passos, e posso mostrar aqui depois como ficou a convergência, pelo menos em relação à perda.

# Para que tantas épocas?

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69201/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69201/question)

Nesta aula foram definidos os conceitos de batch, iteração e época no contexto de aprendizado profundo. Vimos que uma iteração é um passo completo de otimização (forward + backpropagation), o batch é o conjunto de amostras vistas em uma única iteração, e uma época é completada quando todas as amostras de treino foram utilizadas em pelo menos uma iteração.

Indique, a seguir, a alternativa que melhor descreve porque é necessário ver as mesmas amostras múltiplas vezes, ou seja, múltiplas épocas, para otimizar um modelo.

Selecione uma alternativa

-   Ver as amostras múltiplas vezes só é efetivo se a cada época a ordem das amostras for alterada para que o modelo explore a superfície de erro de diferentes maneiras.
    
-   Como a otimização é um processo iterativo, dando pequenos passos na superfície de erro, ver as amostras uma única vez não é suficiente para alcançar um ponto mínimo de erro.
    
-   A primeira época é suficiente para otimizar o modelo. As épocas subsequentes apenas permitem pequenos ajustes na solução.


# Faça como eu fiz na aula

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69202/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69202/question)

No script `Carregamento de Dados.ipynb`, definimos um dicionário de hiperparâmetros, como apresentado a seguir:

```bash
args = {
    'batch_size': 20,
    'num_workers': 4,
    'num_classes': 10,
    'lr': 1e-4,
    'weight_decay': 5e-4,
    'num_epochs': 30
}
```

Nesse dicionário **altere o `batch_size` entre os valores `100`, `20` e `5`**. Para cada valor de `batch_size` realize todo o fluxo de treinamento e avalie:

-   Em quantos segundos se passa uma época.
-   Após quantas épocas a loss fica abaixo de `1.6`.

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69202/opinion)

-   `batch_size = 100`, leva aproximadamente 5 segundos por época, leva 7 épocas para reduzir a loss abaixo de `1.6`.
-   `batch_size = 20`, leva aproximadamente 13 segundos por época, leva 5 épocas para reduzir a loss abaixo de `1.6`.
-   `batch_size = 5`, leva aproximadamente 38 segundos por época e apresenta fortes dificuldades de convergência, não sendo capaz de reduzir a loss abaixo de `1.6` (experimento com 30 épocas). Veja o parágrafo sobre comportamento de convergência para entender melhor.

**Sobre o tempo gasto por época**

Vale ressaltar que a diferença no tempo pode variar, pois o Google Colab possui variação de performance entre sessões. Porém, dentro de uma mesma sessão é possível notar que o `batch_size` impacta não só no comportamento de convergência, mas também no tempo de treinamento. Quanto menor o `batch_size`, mais iterações são realizadas, ou seja, mais tempo é gasto com o passo de otimização (que ocorre a cada iteração).

**Sobre o comportamento de convergência**

Em geral, quando o `batch_size` é muito pequeno, a taxa de aprendizado também deve assumir valores pequenos. Isso porque o passo de otimização será realizado após o modelo ver um subconjunto tão pequeno que chega a ser pouco informativo acerca da distribuição que se deseja modelar. _No caso do `batch_size = 5`_ no nosso problema, é possível ver um comportamento melhor de convergência ao _reduzir a taxa de aprendizado para `1e-6` e reduzir o `weight_decay` para `5e-6`_.