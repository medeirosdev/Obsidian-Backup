Agora que você já conhece o modelo KNN e as métricas de distância, chegou a hora de colocar em prática!

Calcule a distância da Maria com os(as) 10 primeiros(as) clientes da nossa base de dados **normalizada** utilizando a métrica euclidiana.

VER OPINIÃO DO INSTRUTOR

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/machine-learning-classificacao-tras-panos/107946/opinion)

Para realizar o cálculo da distância da Maria com os(as) 10 primeiros(as) clientes, segue o passo a passo de uma possível forma de resolver este desafio:

1 - Começamos importando a biblioteca Numpy.

```javascript
import numpy as np
```

2 - Depois, podemos construir uma função para calcular todas as distâncias de uma vez.

```cpp
def calcula_distancia(dados_clientes, dados_maria, numero_clientes):
    distancias = []

#loop para percorrer cliente por cliente
    for i in range(numero_clientes):
        dist1 = dados_maria - dados_clientes[i]            #subtração dos atributos
        soma_quadrado = np.sum(np.square(dist1))    #exponenciação e soma de todos os atributos
        distancias.append(np.sqrt(soma_quadrado))   #raiz quadrada da soma anterior

    return distancias
```

3 - Por fim, rodamos a função.

```scss
calcula_distancia(X_normalizado, Xmaria_normalizado, 10)
```

Bons estudos! :)