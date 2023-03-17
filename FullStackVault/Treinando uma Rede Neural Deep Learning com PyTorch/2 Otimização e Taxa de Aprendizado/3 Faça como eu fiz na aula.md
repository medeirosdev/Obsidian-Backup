Na [demonstração interativa de Stanford](http://vision.stanford.edu/teaching/cs231n-demos/linear-classify/), experimentamos algumas taxas de aprendizado para entender o seu comportamento na otimização de um modelo. Faça como eu fiz na aula, ou seja, experimente algumas taxas de aprendizado, e conclua **qual o valor aproximado de taxa de aprendizado que consegue convergir em menos tempo**.

> Atenção: para avaliar se o treinamento já convergiu, preste atenção na função de custo exibida na ferramenta. Quando este valor estabilizar, o treinamento terá convergido. A imagem a seguir destaca a localização desta informação.

![Indicação visual de onde se localiza a informação da função de custo na demonstração interativa.](https://caelum-online-public.s3.amazonaws.com/1563-treinando-pytorch/ex02_02.PNG)### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69196/opinion)

O interessante deste exercício é perceber a possibilidade de alcançar rapidamente uma boa solução, mas por outro lado perder estabilidade na convergência. Vamos analisar alguns casos:

-   Um step size no valor de `0.5` encontra uma solução aproximada em 1 segundo, porém, a convergência é extremamente instável, ou seja, a cada nova iteração de treinamento, o modelo se altera significativamente, alterando também a loss média.
-   Já um step size de `0.1` parece mais interessante, demorando em torno de 10 segundos para encontrar uma boa solução, porém, consegue estabilizar em uma loss média de 0.06.