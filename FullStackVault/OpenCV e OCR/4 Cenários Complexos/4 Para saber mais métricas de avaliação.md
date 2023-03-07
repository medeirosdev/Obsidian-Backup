[[OpenCV]]Semelhante aos modelos de machine learning convencionais temos as métricas que podem ser utilizadas após a montagem da matriz de confusão e nos auxiliam a entender melhor sobre como nosso modelo está performando.

Dentro da nossa matriz de confusão ainda continuamos com os mesmos campos, de verdadeiros e falsos que podem ser positivos ou negativos, gerando nossas quatro categorias:

-   **Verdadeiro Positivo (VP):** É quando o modelo categoriza corretamente uma imagem. Por exemplo, categorizar uma imagem de um gato como um gato.
-   **Falso Positivo (FP):** Quando o modelo categoriza uma imagem quando não deveria. Por exemplo, categorizar uma imagem de um gato como um cachorro.
-   **Verdadeiro Negativo (VN):** Ocasião na qual o modelo não categoriza corretamente uma imagem. Por exemplo, não categorizar uma imagem de um gato como um cachorro.
-   **Falso Negativo (FN):** É quando o modelo não categoriza uma imagem, mas deveria. Por exemplo, não categorizar uma imagem de um gato como gato.

Um destaque especial é dado para os valores de **Falsos Positivos (FP)** que ocorrem quando a imagem tem mais classificações do que deveria, apresentando caixas a mais em lugares onde o objeto ou o texto não se encontra, que foi o caso da aula de [Falsos Positivos](https://cursos.alura.com.br/course/visao-computacional-reconhecimento-texto-ocr-opencv/task/112873).

Após termos os valores de VP, FP, VN e FN podemos medir a performance do nosso modelo com algumas métricas, como a **Acurácia**, **Precisão** e **Recall** (ou Sensibilidade - em português).

Sendo assim, temos que cada um destes itens significam, respectivamente:

-   **Acurácia:** avalia a proporção de acertos em relação a **todas** as previsões realizadas. É obtida pelo quociente da soma dos valores de verdadeiros positivos e negativos por todos os outros valores previstos (VP, VN, FP, FN).
    
-   **Precisão:** avalia a proporção de verdadeiros positivos dentre as predições dadas como positivas pelo modelo. É obtida dividindo os verdadeiros positivos pela soma das previsões positivas.
    
-   **Recall / Sensibilidade:** avalia a proporção de verdadeiros positivos dentre todos os valores positivos reais. É obtida dividindo os verdadeiros positivos pela soma de positivos reais.
    

Além disso, outras métricas, tais como **Taxa de Verdadeiros Positivos (TVP)** e a **Taxa de Falsos Positivos (TFP)** também podem ser calculadas com base nos valores obtidos da matriz de confusão. Com os valores de TVP e TFP é possível fazer o gráfico utilizado para avaliar modelos de classificação, chamado de **curva ROC** e para saber mais sobre você pode ver esse [Alura+ sobre Curva ROC](https://cursos.alura.com.br/extra/alura-mais/curva-roc-c1465).