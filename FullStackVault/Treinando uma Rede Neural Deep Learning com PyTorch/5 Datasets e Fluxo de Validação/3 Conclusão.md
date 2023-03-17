[00:00] Parabéns por ter chegado até o final deste curso. Espero que eu tenha conseguido mostrar bem para vocês que o Pytorch é um excelente framework, principalmente para manipulação de dados, e não se esqueça que fazer os exercícios é muito importante, principalmente por estarmos aprendendo um framework genérico com o qual podemos fazer diversas coisas. Os exercícios permitem variar as aplicações para que vocês conheçam a variedade de formas de usar.

[00:35] Nós aprendemos os elementos do processo de otimização, que é a função de perda, a otimização e os hiper parâmetros de otimizadores. Conseguimos ver quais tipos de função de perda vamos usar para problemas de regressão, classificação, entender o porquê de cada um e dessa forma decidamos qual a função de perda ideal.

[01:05] Também falamos do processo de otimização, com a analogia da pessoa vendada andando na montanha, mais para familiarizar vocês como é o processo. Chegamos a ver como ele é afetado pelos hiper parâmetros, como o step size, a famosa taxa de aprendizado. Vimos o efeito desse hiper parâmetro. Espero que vocês tenham entendido bem o que caracteriza um hiper parâmetro, esses dados que nós definimos previamente.

[01:44] Colocamos na prática como vamos otimizar. Fizemos uma prática bem bacana de como funciona passo a passo o processo de otimização até convergir. Também falamos de carregamento de dados e tive a oportunidade de mostrar o Pytorch interagindo com o pandas, que é o pacote de tratamento de dados tabulares.

[02:20] Se você quiser trabalhar com seus próprios dados, espero que eu tenha dado o ferramental completo. Falamos da importância da classe dataset, porque esse para mim é o grande poder do Pytorch.

[02:34] Se ficou qualquer dúvida, usem o fórum, coloquem feedbacks, críticas, o que vocês gostariam de ver que não foi abordado no curso. E isso conclui nossa introdução geral de como treinar um modelo no Pytorch. Espero que agora vocês consigam aplicar nos seus próprios problemas.


# Vantagens do DataLoader

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69204/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69204/question)

Nesta aula, vimos o carregamento customizado de dados através da classe Dataset do PyTorch. Esta classe traz vantagens como o carregamento e a transformação do dado apenas quando ele for necessário, não sobrecarregando a memória do computador. Vimos também que o carregamento de dados está sempre associado à classe DataLoader, um iterador que utilizamos nos fluxos de treinamento e validação.

Sobre DataLoaders, indique a seguir as alternativas que descrevem as suas vantagens.

Selecione 2 alternativas

-   Minimiza períodos ociosos de processamento.
    
-   Normaliza os conjuntos de dados.
    
-   Divide o conjunto de dados em batches.
    
-   Otimiza a transformação dos dados.


# Faça como eu fiz na aula

[PRÓXIMA ATIVIDADE](https://cursos.alura.com.br/course/treinando-rede-neural-pytorch/task/69205/next)

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69205/question)

No script `Carregamento de Dados II.ipynb`, implementamos duas funções: `train()` para o fluxo de treinamento e `test()` para o fluxo de validação. Implemente, no lugar dessas duas funções, uma única função `forward()` separando internamente as operações referentes ao treino e à validação. Ela terá o seguinte protótipo:

```python
def forward(loader, net, epoch, mode):
```

O parâmetro `mode` deve receber o valor “train” ou “test”, a depender da operação que deve ser realizada. Este parâmetro irá controlar as operações que devem ser realizadas em cada modo. Exemplo:

```php
if mode == "train":
  net.train()
else:
  net.eval()
```

Para facilitar, pode desconsiderar o gerenciador de contexto `with torch.no_grad()`, e definir o modo de forward através dos comandos `train()` e `eval()`, como apresentado acima. **O desafio é entender quais operações são realizadas durante o treinamento e durante a validação.**

Lembre-se de substituir as chamadas de função na célula que contém o seguinte código:

```css
for epoch in range(args['num_epochs']):
  train(train_loader, net, epoch)
  test(test_loader, net, epoch)
  print("-------------------------------")
```

### Opinião do instrutor

-   [](https://cursos.alura.com.br/suggestions/new/treinando-rede-neural-pytorch/69205/opinion)

```css
# Resumo do código: Função forward()
def forward(loader, net, epoch, mode):
  if mode == "train":
    net.train()
  else:
    net.eval()

  epoch_loss = []
  for batch in loader:
    dado, rotulo = batch

    # Cast na GPU
    dado   = dado.to(args['device'])
    rotulo = rotulo.to(args['device'])

    # Forward 
    pred = net(dado)
    loss = criterion(pred, rotulo)
    epoch_loss.append(loss.cpu().data)

    if mode == "train":
      # Backward
      loss.backward()
      optimizer.step()

  epoch_loss = np.asarray(epoch_loss)
  print("Epoca %d, Loss: %.4f +\- %.4f" % (epoch, epoch_loss.mean(), epoch_loss.std()) )
```

```kotlin
# Resumo do código: Chamada de função
for epoch in range(args['num_epochs']):
  forward(train_loader, net, epoch, "train")
  forward(test_loader, net, epoch, "test")
  print("-------------------------------")
```

![[1563-treinando-pytorch-aula-05.zip]]