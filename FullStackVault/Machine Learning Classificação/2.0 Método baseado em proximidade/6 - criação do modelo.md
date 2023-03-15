Podemos utilizar a biblioteca scikit-learn para classificar dados usando o algoritmo KNeighborsClassifier. Para isso, devemos dividir os dados entre dados de treinamento e teste e aplicar funções da biblioteca para realizar a previsão.

Considere o código abaixo:

```javascript
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
```

---

```markdown
X_treino, X_teste, Y_treino, Y_teste = train_test_split(X_normalizado, Y, test_size=0.3, random_state=42)

knn = KNeighborsClassifier(metric='euclidean')
knn.fit(_____,_____)
predito_knn = knn._____(X_teste)
```

Assinale a alternativa que completa corretamente as lacunas apresentadas no código.

Selecione uma alternativa

-   ```makefile
    X_treino, X_teste, Y_treino, Y_teste = train_test_split(X_normalizado, Y, test_size=0.3, random_state=42)
    
    knn = KNeighborsClassifier(metric='euclidean')
    knn.fit(X_treino, Y_teste )
    predito_knn = knn.fit(X_teste)
    ```
    
-   ```makefile
    X_treino, X_teste, Y_treino, Y_teste = train_test_split(X_normalizado, Y, test_size=0.3, random_state=42)
    
    knn = KNeighborsClassifier(metric='euclidean')
    knn.fit(X_teste,Y_teste)
    predito_knn = knn.predict(X_teste)
    ```
    
-   ```makefile
    X_treino, X_teste, Y_treino, Y_teste = train_test_split(X_normalizado, Y, test_size=0.3, random_state=42)
    
    knn = KNeighborsClassifier(metric='euclidean')
    knn.fit(X_treino, Y_treino)
    predito_knn = knn.predict(X_teste)
    ```
    
-   ```makefile
    X_treino, X_teste, Y_treino, Y_teste = train_test_split(X_normalizado, Y, test_size=0.3, random_state=42)
    
    knn = KNeighborsClassifier(metric='euclidean')
    knn.fit(Y_treino, X_teste)
    predito_knn = knn.score(X_teste)
    ```