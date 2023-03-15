**Dados desbalanceados** são aqueles que possuem muitos registros para uma categoria e poucos para outra. Se não balanceamos esses dados de alguma forma, eles podem acarretar em problemas na construção de modelos e na geração de previsões.

Para verificarmos se a nossa base de dados está desbalanceada, vamos gerar um gráfico que apresenta a distribuição dos valores da nossa variável classificadora **"Churn"**:

```kotlin
import seaborn as sns
%matplotlib inline

ax = sns.countplot(x='Churn', data=dados_final)
```

![alt text: Gráfico com a distribuição dos valores da variável classificadora Churn. No eixo x, temos o churn com valores 0 e 1. O eixo y contém o count que vai de 0 a 5000. Na área do gráfico temos duas barras: uma azul, à direita, com valor de 0 a 5174; e outra barra laranja, à esquerda, com valor de 0 a 1869.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/01/Aula1-img4.png)

Analisando o gráfico, podemos perceber que nossa variável está desbalanceada e precisamos tratar isso. Para realizar o balanceamento dos dados, utilizaremos uma técnica chamada de _Oversampling_, que consiste em realizar a criação de novas observações da classe quando há menos amostras, tendo como objetivo igualar a proporção entre as categorias.

Uma das técnicas de oversampling muito utilizada é a **SMOTE**. Sua ideia consiste em criar observações intermediárias entre os dados que estão próximos. Por exemplo, se minutos totais por dia são 129.1 e 146.3, então será criada uma amostra com os minutos totais por dia com 137.7. Lembrando que não é necessariamente a média entre as amostras.

Vamos dar uma olhada no trecho de código utilizado para balancear o nosso dataset com o auxílio da biblioteca [imbalanced-learn](https://imbalanced-learn.org/stable/index.html) e da classe [SMOTE](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html).

Caso esteja utilizando outro ambiente de desenvolvimento que não seja o Colab e seja necessário instalar a biblioteca, você pode fazê-la executando o trecho de código abaixo em alguma célula do seu notebook:

```diff
!pip install -U imbalanced-learn
```

```ini
# Para podermos aplicar o SMOTE, devemos separar  os dados em variáveis características e resposta  

X = dados_final.drop('Churn', axis = 1)
y = dados_final['Churn']
```

```python
from imblearn.over_sampling import SMOTE

smt = SMOTE(random_state=123)  # Instancia um objeto da classe SMOTE
X, y = smt.fit_resample(X, y)  # Realiza a reamostragem do conjunto de dados
```

```makefile
dados_final = pd.concat([X, y], axis=1)  # Concatena a variável target (y) com as features (X)

# Verifica se o balanceamento e a concatenação estão corretos.
dados_final.head(2)
```

```ini
ax = sns.countplot(x='Churn', data=dados_final)  # plotando a variável target balanceada.
```

![alt text: Gráfico com a distribuição dos valores da variável classificadora Churn. No eixo x, temos o churn com valores 0 e 1. O eixo y contém o count que vai de 0 a 5000. Na área do gráfico temos duas barras: uma azul, à esquerda, com valor de 0 a 5174; e outra barra laranja, à direita, com valor de 0 a 5174.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/01/Aula1-img5.png)