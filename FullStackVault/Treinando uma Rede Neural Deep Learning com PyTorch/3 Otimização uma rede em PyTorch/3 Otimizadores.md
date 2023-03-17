[00:00] Agora vamos falar um pouco sobre os otimizadores que estão ao nosso dispor. Só para entendermos a variedade que existe e como escolher o melhor.

[00:13] Existe uma quantidade considerável de otimizadores. Cada um requer um ajuste de hiper parâmetros muito específico. São valores definidos antes do treinamento, e cada otimizador vai exibir um ajuste diferente. A ordem que vamos conhecer segue uma linha temporal de evolução.

[00:50] Primeiro foi lançado a descida do gradiente, que é o mais simples, depois a adição do momentum, e vamos ver como eles evoluíram ao longo do tempo. Essa imagem seria o exemplo de uma superfície de erro. Queremos minimizar a função de perda, encontrar o ponto mínimo da função. Cada otimizador se comporta de forma diferente. Alguns chegam mais rápido na solução, outros ficam presos em soluções subótimas e se recuperam. Existem vários comportamentos que se adequam a necessidades diferentes.

[01:37] O mais comum que existe é a descida do gradiente, que é o algoritmo clássico. Ele só subtrai o gradiente dos pesos da rede, e é em função da taxa de aprendizado. A taxa de aprendizado é um hiper parâmetro que sempre vai existir, independente do otimizador, mas pode ser que existam ou não outros fatores relevantes.

[02:07] Aqui temos uma situação em que temos em y a loss e em x o espaço de feature, o peso. Temos um mínimo local, ou seja, uma solução subótima, mas que é um vale da montanha, e um mínimo global, que é a solução ótima. Estamos procurando essa solução, mas temos que tomar cuidado com as soluções subótimas que podem existir.

[02:38] O que vamos fazer aqui é aquele cálculo de derivadas, se estou melhorando continuo seguindo nessa direção até chegar no mínimo local. Se eu der um passo depois dessa região, vejo minha loss voltar a piorar, então vou considerar esse ponto minha solução ótima.

[03:03] Existem otimizadores muito suscetíveis a não explorar mais o espaço se ele encontra uma solução subótima. Porém, se explorarmos características como o momentum, ele vai levar em consideração a velocidade dos passos de atualização. Se eu vinha numa descida muito rápida, por exemplo, vou aderir a um comportamento exploratório e vou continuar seguindo, mesmo que numa direção que não seja ótima. Assim vamos descobrir o mínimo global. O momentum explora melhor o espaço de busca e é mais robusto.

[03:53] Aqui temos a descida do gradiente tradicional no Pytorch. É só chamar a biblioteca optim.SGD, passando os parâmetros do modelo e a taxa de aprendizado. Se quisermos adicionar momentum, temos que adicionar um hiper parâmetro referente ao momentum, a importância que vamos dar à velocidade de melhora da loss.

[04:22] Em geral, a taxa de aprendizado vai mudar bastante de problema para problema, mas o momentum é comum usarmos o valor 0.9. Ele costuma se comportar bem, guardadas exceções.

[04:37] Também tem a alternativa do nesterov, se você estiver usando a descida do gradiente, tratando de um problema simples e quer uma solução simples. É uma pequena modificação na matemática do momentum. A descida do gradiente permite essas adições de momentum, e o nesterov, que é só um boolean.

[05:05] Decaimento de pesos é outro parâmetro muito importante de ajustar. Ele se refere à regularização do seu modelo. Vamos falar brevemente sobre, mas vale a pena dar uma explorada maior no impacto da regularização do modelo. Tanto o SGD quanto outros otimizadores permitem a adição de um decaimento de pesos.

[05:30] Aqui coloquei um exemplo de fator para o decaimento, mas isso também vai variar bastante e você precisa otimizar para o seu problema. De forma resumida, é uma penalidade L2, quadrática, que controla a complexidade do modelo. Se você quiser saber mais sobre a relevância do decaimento de pesos, procure por overfit e o papel da regularização.

[06:07] De forma geral, o que o decaimento faz é adicionar um termo a mais que vai penalizar pesos muito grandes. Se seu W começar a crescer muito, isso vai interferir na loss. Estamos somando um fator que vai interferir diretamente. Sua loss vai piorar se seus pesos crescerem muito. O impacto disso é que quanto maior seu decaimento de pesos, mais simples vai ser seu modelo.

[06:43] Quando você estiver definindo o weight decay, você tem que pensar dessa forma. Quanto maior o valor, mais simples vai ser seu modelo. É adequado em casos de overfit, ou você pode reduzir o weight decay, se você quer um modelo mais complexo. Vai variar caso a caso.

[07:20] Aqui temos um playground do tensor flow que permite que você experimente com diferentes configurações de uma rede neural. Eu criei um cenário simples que tende facilmente ao overfit. Vocês podem testar. Ele tem uma taxa de aprendizado definida, uma ativação intermediária e a regularização L2. Essa taxa de regularização é o weight decay que você vai definir nos seus modelos, então vale a pela brincar com os valores e ver como ele se comporta.

[07:57] Por exemplo, se colocamos decaimento 0, sem regularização, o que vai acontecer é que seu modelo vai ficar mais complexo, ele vai assumir um comportamento mais superajustado aos seus dados. Ele se contorce o máximo que consegue, criando uma região de dúvida. Posso deixar o modelo rodando e ele vai tentar acertar o máximo possível.

[08:47] Já se eu aumento com os mesmos dados, ele não vai se contorcer tanto, não vai passar de uma simples curva, mesmo se estiver errando. Isso penaliza modelos mais complexos. Você não vai ver seu modelo se contorcendo para tentar se ajustar aos seus dados. Isso permite o modelo generalizar melhor, que você consiga prever melhor as amostras de teste. Independente de estar errando as amostras, ele vai entender que a região abaixo da linha é da classe laranja. Isso é um comportamento que queremos, por isso é importante controlar a regularização.

[09:55] Atualmente o SGD é o mais simples de todos. A diferença é que ele usa a mesma taxa de aprendizado para todos os parâmetros do seu modelo. Só que surgiram os otimizadores adaptados que calculam a taxa de aprendizado diferente para cada parâmetro. São ideais para conseguir ajustar melhor o modelo para diferentes tipos de problemas.

[10:25] O primeiro foi o AdaGrad, super simples de chamar, usando optim.Adagrad, depois você passa os parâmetros, a taxa de aprendizado, o decaimento de pesos e consegue rodar.

[10:45] O AdaDelta veio depois e é a mesma coisa, só chamar. O Adagrad tinha sérios problemas de underfit e por isso surgiu o AdaDelta para tentar solucionar. Depois, surgiu o RMSprop. É o mais interessante para mim. Ele resolveu o problema de underfit e ser melhor que o AdaDelta. Foi um curso online do Geoffrey Hinton. Eu deixei o link caso vocês queiram ver. Fazendo o curso, ele propôs um novo otimizador que funcionava muito melhor que os outros. Por muito tempo foi o mais usado.

[11:52] Por fim, o Adam. É o mais utilizado, que melhor se comporta nos problemas. Basta definir a taxa de aprendizado e o weight decay. Ele tem outros hiper parâmetros, tem o momentum, os betas internos, mas são os poucos os casos em que você vai ter que mexer nos hiper parâmetros.

[12:16] Tentei colocar aqui os hiper parâmetros obrigatórios que você vai ter que mexer, como taxa de aprendizado, weight decay e momentum. No caso do adam, os betas internos dele já são bem adequados para a maioria dos problemas. Ele é a estrela do show porque na dúvida, use o adam. É excelente e um dos mais atuais.

[12:55] Ficamos por aqui. Vejo vocês na próxima aula.