Em um problema de detecção de objetos em imagens, o rótulo de uma amostra pode ser formado pelas coordenadas (x, y) dos pontos p1 e p2 que definem um retângulo sobre o objeto desejado, sendo p1 o ponto superior esquerdo e p2 o ponto inferior direito do retângulo, como apresentado na figura a seguir.

![](https://caelum-online-public.s3.amazonaws.com/1563-treinando-pytorch/ex01_01.jpg)

Uma solução baseada em redes neurais deve comportar a predição de todas as variáveis relevantes para o problema, bem como uma função de perda adequada para esta categoria de problemas. **O objetivo neste caso é realizar uma regressão para todas as coordenadas que definem o retângulo.**

Assumindo uma camada escondida com 128 neurônios, indique a seguir a alternativa que apresenta a camada de saída e a função de perda melhor relacionadas ao problema proposto.

Selecione uma alternativa

-   Camada de saída: `nn.Linear(128, 2)` Função de perda: `nn.L1Loss()`
    
-   Camada de saída: `nn.Linear(128, 4)` Função de perda: `nn.CrossEntropyLoss()`
    
-   Camada de saída: `nn.Linear(128, 4)` Função de perda: `nn.MSELoss()`


# Faça como eu fiz na aula

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69192/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69192/question)

No script `Funções de Perda.ipynb` apresentamos um problema de regressão e definimos a função _Mean Squared Error_ (MSE) como critério de qualidade.

Altere o código do script, utilizando agora a função de perda de distância absoluta (L1), e compare o erro médio da L1 com o erro médio da MSE.

VER OPINIÃO DO INSTRUTOR

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69192/opinion)

A alteração deve ser feita na variável `criterion`, substituindo a chamada da `nn.MSELoss()` pela chamada da `nn.L1Loss()`, como apresentado a seguir:

```ini
# Antes
criterion = nn.MSELoss().to(device)
# Depois
criterion = nn.L1Loss().to(device)
```

Ao comparar os resultados, vemos que:

```css
# Resultado da MSE: tensor(28771.2148, device='cuda:0')
# Resultado da L1: tensor(151.1335, device='cuda:0')
```

Como o nosso modelo não foi treinado, ou seja, apenas foi inicializado com valores aleatórios, é esperado um baixíssimo desempenho com altos índices de erro. Podemos notar que o critério quadrático penaliza muito mais os erros, apresentando um erro 190x maior que a função de distância absoluta. Esse comportamento é ideal para uma boa convergência, **a menos que o seu modelo possua outliers**.