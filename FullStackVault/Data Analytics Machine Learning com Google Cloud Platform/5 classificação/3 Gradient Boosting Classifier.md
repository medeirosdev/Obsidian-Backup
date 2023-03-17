[00:00] Agora podemos treinar o nosso modelo, vamos separar as bases de x e y uma vez que a gente trouxe o revenue para dentro do X, y_train_ds = X_train, essa parte da base com Downsample.

[00:24] Vamos fazer aqui é igual o X_train_ds.revenue.copy(), e o X_train_ds vai ser igual a ele mesmo sem o revenue vou fazer o drop do revenue, axis=1 e vou passar inplace aqui.

[00:46] Está separado x e y, pode treinar o modelo de novo. Caso alguém tenha a base exatamente igual a minha que vai depender de quando você está fazendo esse curso, como que essa base eu já mexeu desde que eu fiz esse teste para quando você está fazendo.

[01:13] Eu vou passar aqui o random_state = 42 para que os resultados possam ser comparáveis caso a base seja igual. Vou com ds e vou treinar com GradientBoosting, como vimos nos passos anteriores ponto fit, passo o X_train, ds e y_train.

[01:48] Vai demorar enquanto ele faz o fit, eu posso fazer o predict e tudo que eu vou calcular depois disso, mesma coisa que fiz antes, posso copiar. Importante lembrar-se de mudar o X_test mantém porque não mexemos na nossa base teste.

[02:05] Ajusta a nossa base de treino para influenciar um pouco o nosso modelo, mas tem de testar com o cenário mais real possível, então não pode fazer Downsample numa base de teste.

[02:14] Muda para ds também e esse vai ser chamado de predict_ds, quando terminar o predict também e fazer todas as comparações feitas, analisar como que ficou a matriz de confusão e como que ficou o classification report.

[02:42] Lembrando que estamos analisando ds, bom agora espera terminar de rodar, lembrando que o modelo GradientBoosting pode demorar um pouco.

[03:07] Já terminou de treinar o nosso modelo, fez o predict e vou olhar como ficaram os resultados, comparando com y test sem mexer em nada nessa base e também as métricas dentro do y test.

[03:21] Teve uma leve melhora nos usuários que estávamos acertando sobre se eles se eles gastaram ou não, havíamos acertado apenas 73 desses usuários. Agora já subiu para 89 e o nosso precision para esse caso aqui subiu quatro pontos percentuais, tem uma leve melhora e pode continuar fazendo alguns ajustes para mexer.

[03:44] Por último, para tentar dar um salto um pouco maior que nesse modelo e deixar um pouco mais utilizável, vamos treinar outro modelo de GradientBoosting sem usar o sklearn. Que é uma biblioteca super utilizada nos dias de hoje para modelos de gradient boosting e ver se conseguimos melhorar ainda mais esse nosso modelo.