Vamos supor que temos um conjunto de informações de pacientes com suspeita de sarampo. Para auxiliar o(a) médico(a) na tomada de decisão sobre o diagnóstico, aplicamos um modelo de classificação e obtemos os seguintes resultados:

```java
Diagnóstico predito = [0,0,0,0,1,1,1,1,0,1,0,1]
```

---

```go
Diagnóstico real = [1,1,0,0,1,1,1,0,1,0,1,0]
```

Sabendo que o valor 1 representa caso confirmado de sarampo e o valor 0 não é um caso de sarampo, calcule o desempenho deste modelo de classificação usando as métricas Recall e f1-score. Em seguida, selecione a resposta com os respectivos valores:

Selecione uma alternativa

-   0.500 e 0.416
    
-   0.428 e 0.461
    
-   0.414 e 0.416
    
-   0.500 e 0.414