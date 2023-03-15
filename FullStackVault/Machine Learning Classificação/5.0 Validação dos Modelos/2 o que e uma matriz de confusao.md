A **matriz de confusão** é uma ferramenta muito utilizada para avaliar modelos de machine learning de classificação. Ela consiste em uma matriz em que **as linhas representam os valores reais** e **as colunas representam os valores preditos**. Cada espaço da matriz passa a ser um diagnóstico. A ideia geral é contabilizar a quantidade de vezes que um determinado valor A é classificado como valor B.

Para trabalharmos com um exemplo, vamos pensar em uma lista de possíveis clientes da Alura Voz, na qual você executou um modelo de predição e obteve a seguinte classificação:

```ini
valores_preditos = [0, 1, 1, 1, 0, 0, 1, 0, 0, 1]
```

Os valores reais da classificação dessas pessoas são:

```ini
valores_verdadeiros= [0, 1, 0, 1, 0, 0, 1, 0, 1, 0]
```

Nele, o valor 0 significa que o(a) cliente possivelmente não irá assinar o plano da Alura Voz e 1 significa que poderá assinar.

Analisando apenas os valores de `valores_preditos` e `valores_verdadeiros`, percebe-se que o modelo errou na classificação de algumas amostras. A matriz de confusão nos mostrará a frequência de classificação para cada classe em nosso modelo da seguinte forma:

![alt text: Matriz de confusão com 2 linhas e 2 colunas. Na linha 1, coluna 1 está o valor 4 com o rótulo “Verdadeiro Negativo”. Na linha 1, coluna 2 está o valor 2 com o rótulo “Falso Positivo”. Na linha 2, coluna 1 está o valor 1 com o rótulo “Falso Negativo”. Por fim, a linha 2, coluna 2 está o valor 3 com o rótulo “Verdadeiro Positivo”.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/05/Aula5-img1.png)

Na primeira linha e primeira coluna estão 4 valores verdadeiros negativos, ou seja, o modelo previu a classe como negativa (no nosso exemplo a classe negativa é 0) e isso realmente é verdade. Já na primeira linha e segunda coluna foram classificados 2 valores como 1, porém seu valor real é 0. Como o modelo classificou a classe positiva como sendo negativa, chamamos de falso positivo.

Seguindo para a segunda linha e primeira coluna, temos que o modelo classificou 1 valor como pertencendo à classe 0, porém seu valor real é 1. Logo, o modelo previu a classe negativa, mas isso é falso e chamamos de falso negativo. Por último, na segunda linha e segunda coluna, 3 valores foram classificados como 1, o que realmente é verdade de acordo com o valor real. Logo, foi prevista a classe verdadeira e ela é conhecida como verdadeiro positivo.

Uma observação importante: a matriz de confusão pode se apresentar também na ordem inversa à mostrada aqui, com as linhas sendo os valores preditos pelo modelo e as colunas como os valores reais. Assim, é importante não decorar a ordem, mas realizar a análise feita anteriormente. Dessa forma, você não irá cometer erros.

Para saber como a matriz acima foi criada, você pode acessar o seguinte repositório no GitHub: [Gerando matriz de confusão](https://github.com/alura-cursos/Gerando-matriz-de-confusao-ML2)Sabemos que uma matriz de confusão pode apresentar-se de uma forma diferente da estudada em aula, sendo invertidas as linhas com as colunas. Logo, as linhas seriam os valores preditos e as colunas os valores verdadeiros. Um exemplo dessa outra configuração pode ser encontrada na imagem abaixo:

![alt text: Matriz de confusão com 2 linhas e 2 colunas. As linhas representam os valores previstos, enquanto as colunas representam os valores verdadeiros.Na linha 1, coluna 1 está o valor 3. Na linha 1, coluna 2 está o valor 1. Na linha 2, coluna 1 está o valor 2. Por fim, a linha 2, coluna 2 está o valor 3.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/05/Aula5-img2.png)

Analisando a imagem acima, identifique quais alternativas estão corretas de acordo com os verdadeiros positivos, verdadeiros negativos, falsos positivos e falsos negativos.

Selecione 2 alternativas

-   O número 3 indica a quantidade de verdadeiros negativos.
    
-   O valor 1 indica a quantidade de falsos positivos.
    
-   O valor 2 indica a quantidade de verdadeiros positivos.
    
-   O valor 4 indica a quantidade de verdadeiros positivos.