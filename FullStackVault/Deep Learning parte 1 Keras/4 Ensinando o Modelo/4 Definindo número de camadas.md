Podemos partir para olhar um pouco para a segunda camada, a 1, com 256 unidades e ativado por ReLU, que provavelmente está entendendo, por baixo dos panos, os contornos das nossas imagens. Mas reparem que quando estávamos criando esta camada também percebemos que ela é densa, totalmente conectada. E aqui temos 256 unidades, daquelas bolinhas de funções, se conectando totalmente com 10.

Assim, poderíamos criar algo intermediário, que fosse afunilando essa conexão que estamos fazendo. Será que isso pode melhorar, diminuir a perda de nossa rede? Vamos testar dando Enter e fazendo mais uma camada também, de Keras, e em vez de colocarmos 256 unidades, reduzimos para 128, incluiremos uma vírgula e activation igual tensorflow.nn.relu.

Muito provavelmente esta ReLU, em vez de apenas captar o contorno, captará outros detalhes das nossas imagens quando elas forem processadas. Não podemos esquecer de incluir uma vírgula no fim da linha. Vamos rodar este modelo para ver o que acontece com a nossa perda. Lembrando que ela está em 0.48.

Podemos ver os resultados, e desta vez a nossa perda aumentou para 0.77, demorando mais para executar, também, pois houve aumento de 2s para passar pelos 60000. Por que isso aconteceu?

Primeiro que colocamos mais uma camada, então houve um processamento extra de nossos dados, é natural que o tempo vá aumentar. Se vocês forem trabalhar desenvolvendo estes modelos de Machine Learning vocês verão que existem modelos que demoram dias para serem processados. Aqui, em 11s, estamos muito bem.

O que aconteceu foi que acabou aumentando a nossa perda, isso, a não ser que façamos altas contas mesmo, com derivadas e afins, é difícil de computarmos apenas observando. Não sabemos exatamente o que está acontecendo nesta camada que adicionamos. Por esses e outros motivos, utilizaremos o gancho para dizer a vocês que, muitas vezes, se não 100% ou 90% das vezes, estas camadas intermediárias, entre a de entrada e de saída, são chamadas de camadas ocultas.

Porque temos uma ideia do que pode estar acontecendo, mas não temos certeza absoluta de como está sendo este processamento. O máximo a que chegamos de visualizar o que pode estar acontecendo é saber que cada vez mais estas camadas adicionais irão agrupando mais características das nossas imagens, então elas começam com menos, e vão agrupando mais.

O que poderíamos fazer, então?

Continuando no meio, podemos adicionar mais uma camada. Que diferença será que isso vai dar? Copiaremos para não termos que reescrever, colaremos, e desta vez, de 128, vamos diminuir ainda mais este número, para 64. Salvaremos e rodaremos com Cmd + Enter. Agora demorou ainda mais para executar, 12s, e conseguimos ver que a nossa perda, ao invés de diminuir, aumentou ainda mais, passando a ser de 2.30.

Sabemos, então, que incluir camadas a mais em nossa rede, nesse momento, não está nos ajudando a diminuir a perda. Podemos experimentar mais, ou menos, vai depender do tanto que temos para poder fazer com as nossas camadas, com o tempo disponível para este desenvolvimento, etc.

O que podemos fazer, do que experimentamos até agora, é concluir que quando deixamos o modelo com apenas uma camada de ReLU com 256 unidades, ele acaba funcionando de um jeito mais legal do que se adicionamos mais uma camada com 128, ou outra com 64.