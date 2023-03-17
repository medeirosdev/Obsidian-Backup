Nesta aula conhecemos os impactos de cada hiperparâmetro no processo de otimização. Por exemplo, o momentum aumenta a robustez a mínimos locais, e a taxa de aprendizado define o tamanho do passo de otimização. Alguns desses hiperparâmetros possuem valores padrão, que funcionam para a maioria dos problemas, como é o caso do `momentum` onde se sugere o valor `0.9`. Já o decaimento de pesos (`weight_decay`) precisa ser ajustado para cada problema específico, e é um dos hiperparâmetros mais importantes do processo de otimização.

Indique a seguir a afirmativa que melhor descreve o papel do `weight_decay`.

Selecione uma alternativa

-   Penaliza erros muito altos do modelo, modificando os pesos de forma proporcional aos erros.
    
-   É uma penalidade de regularização que controla a complexidade do modelo.
    
-   Reduz os pesos do modelo iterativamente até a sua configuração mais simples.]
- 
- # Faça como eu fiz na aula

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69199/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69199/question)

No script `Otimização.ipynb` ajustamos um problema de classificação com 3 categorias (verde, azul e vermelho). Um dos passos realizados foi a padronização dos dados através da função `StandardScaler()`. Este passo foi concentrado em uma única célula, contendo o código a seguir:

```kotlin
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
data = scaler.fit_transform(data)

plt.scatter(data[:, 0], data[:,1], c=targets, s=15, cmap=plt.cm.brg)
plt.xlabel(wine.feature_names[features[0]])
plt.ylabel(wine.feature_names[features[1]])
```

Comente a célula com o código acima, e rode todo o código, desde o carregamento dos dados até a otimização da rede. Como ficará o modelo resultante?

VER OPINIÃO DO INSTRUTOR

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69199/opinion)

Sem o passo de padronização, após 200 iterações de treinamento, o meu experimento obteve o resultado apresentado na figura a seguir.

![Plot da fronteira de decisão após 200 iterações de treinamento.](https://caelum-online-public.s3.amazonaws.com/1563-treinando-pytorch/ex03.png)

Para replicar o meu experimento, antes da definição da rede adicione a seguinte linha de código para fixar a aleatorização de pesos:

```scss
torch.manual_seed(42)
```

Podemos concluir que sem a padronização o processo de otimização tem maior dificuldade em encontrar um resultado adequado. Isso ocorre porque a diferença na escala entre as variáveis dificulta a sua combinação pelo modelo. Processos como a padronização e a normalização levam todos os dados para uma escala similar, enquanto mantêm as suas distribuições originais.