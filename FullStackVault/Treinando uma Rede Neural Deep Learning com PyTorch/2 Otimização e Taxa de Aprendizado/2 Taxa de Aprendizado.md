[00:00] Vamos concluir o raciocínio de qual o efeito de aumentar ou diminuir a taxa de aprendizado, para que fique clara a nossa escolha de guiar a taxa de aprendizado. Primeiro, vamos continuar olhando o gráfico de loss pelos pesos. Ou seja, como ela se comporta à medida em que aumentamos os pesos.

[00:27] Vou escolher um peso igual a 0.1. Ele vai me dar uma loss de 0.8. Se minha taxa de aprendizado é pequena, eu vou dar um passo muito pequeno. Para o novo peso igual a 0.11 daria uma loss menor. Vou continuar nessa direção. É o que o gradiente vai dizer, com base nos cálculos.

[01:54] Eu sei pela alteração de pesos que eu estava decrescendo e posso fazer uma projeção da minha superfície de erro. Com essa taxa de aprendizado, eu ia alterando os pesos passo a passo até chegar no ponto mínimo.

[02:15] Se minha taxa de aprendizado é grande, vamos supor que eu começo no 0.1. Preciso alterar os pesos. Vou alterar com um passo muito maior, indo para 0.6. É um ponto mínimo. Você vai ver que é a direção certa, mas a loss volta a subir. Então você vai parar de mudar em uma direção e ir para outra. Você vai dar passos tão grandes que nunca vai estabilizar.

[03:57] À medida que você treina seu modelo, você vai avaliar como a loss está se comportando, isso é o clássico de monitoração de modelos para você saber se seu modelo está melhorando ou piorando.

[04:25] Temos quatro casos. Um em que a taxa de aprendizado está muito alta, um em que está um pouco alta, um em que está baixa e uma em que está boa. Se estiver muito alto, o que vai acontecer é que o modelo vai começar convergindo e depois vai divergir. Meus passos são tão grandes que vou piorar e desviar da solução.

[05:33] Diminuí a taxa de aprendizado. **Se ela estiver alta, mas não muito, ela vai convergir e saturar em um ponto não ótimo.** Minha taxa ainda está muito alta. Se eu tiver uma taxa de aprendizado muito baixa, ela vai diminuir tão devagar que até chegar na solução ótima fiz tanta coisa que não vale a pena.

[06:32] Uma boa taxa de aprendizado vai decrescer rapidamente e saturar em um ponto ótimo, próximo de zero. Esse monitoramento é muito importante para nos ajudar a definir a taxa de aprendizado aplicada na nossa otimização. No próximo vídeo vamos ver no Pytorch como fazer o processo de otimização.

# Escolhendo os pesos da rede

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69194/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69194/question)

Nesta aula conhecemos o processo de otimização de uma rede neural. Vimos que, na essência, a otimização consiste em experimentar diferentes combinações de pesos para os parâmetros de um modelo, de modo a explorar a sua superfície de erro em busca do ponto onde a loss alcança o seu mínimo.

No entanto, as combinações de peso experimentadas não são aleatórias. Marque a seguir a alternativa que **melhor descreve** como são escolhidas as combinações de pesos experimentadas.

Selecione uma alternativa

-   O resultado da função de perda (_loss_) é suficiente para avaliar a qualidade da combinação de pesos experimentada e definir o próximo passo da otimização.
    
-   Calcula-se o gradiente da função que relaciona a loss com os parâmetros do modelo. A partir do gradiente é possível fazer uma escolha mais inteligente da próxima combinação de pesos.
    
-   A taxa de aprendizado definida antes do treinamento é responsável por direcionar as alterações de peso ao longo do processo de otimização.
# Para saber mais

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69195/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69195/question)

Sobre o impacto de alterar a taxa de aprendizado, vale experimentar uma [demonstração interativa fornecida pela Google](https://developers.google.com/machine-learning/crash-course/fitter/graph). Esta demo apresenta um gráfico 2D da função de custo em relação ao valor de um peso do modelo, como apresentado na figura a seguir.

![Plot de uma função quadrática relacionando a função de custo e uma variável correspondendo ao peso de um modelo.](https://caelum-online-public.s3.amazonaws.com/1563-treinando-pytorch/ex02.PNG).

São sugeridos alguns exercícios que lhe ajudarão a entender como escolher uma boa taxa de aprendizado de acordo com o comportamento do seu modelo ao longo das iterações. Alguns exemplos de exercício são:

-   Defina a taxa de aprendizado no valor `0.1` e veja em quantos passos é possível minimizar o erro.
-   Aumente a taxa de aprendizado para `1` e compare o número de passos necessários para minimizar o erro.
-   Por fim, defina o valor `4` para a taxa de aprendizado. O que acontece agora?

É evidente que esses valores mágicos não vão funcionar da mesma forma em todas as situações. Esta é só mais uma forma de compreender o que pode acontecer com o seu modelo ao experimentar diferentes valores de taxa de aprendizado. Esta é uma tarefa **essencial** para solucionar um problema com redes neurais, portanto, vale uma compreensão sólida do funcionamento deste parâmetro.