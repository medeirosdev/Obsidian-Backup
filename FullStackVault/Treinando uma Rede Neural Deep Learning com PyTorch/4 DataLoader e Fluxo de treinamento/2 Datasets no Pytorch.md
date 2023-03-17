[00:00] Agora vamos colocar a mão na massa para valer e vamos trabalhar com dados que se aproximam do mundo real, porque o Pytorch tem um ferramental muito bom para manipulação e carregamento de dados e quero que vocês conheçam antes de terminarmos o curso.

[00:17] Vamos fazer primeiro o que já sabemos, que são imports de pacotes e a definição de qual o dispositivo de hardware que vamos usar. Iremos precisar dos pacotes normal e do nn e o optim que tem os otimizadores.

[00:44] O que vamos fazer de diferente agora é criar um dicionário com os hiper parâmetros que vamos definir. Por exemplo, teremos a chave batch size, e eu quero um de tamanho 20. Sempre que eu quiser acessar essa variável ela está ali em cima. Faço isso porque esses valores que podemos modificar manualmente não gosto que fiquem perdidos ao longo do código.

[01:12] Na hora de verificar, posso colocar também como um elemento do meu dicionário. Imprimimos qual o device. Estou fazendo dessa forma porque toda vez que precisarmos importar alguma coisa, colocamos em cima para ficar organizado.

[01:51] Vou mostrar brevemente os datasets pré-existentes no framework do Pytorch. Se quisermos usar, são muito mais fáceis. Duas bibliotecas são as mais importantes. O Pytorch text, que tem dados de texto, modelo de linguagem, tradução. E o Pytorch vision, que tem datasets de dígitos, de cenas, faces, ações.

[02:30] Como tratar de texto é muito complicado, tem muita nuance que não teremos tempo de lidar, minha sugestão é trabalhar com imagens para conseguirmos trabalhar com dados que se assemelham à realidade. O Pytorch só tem esse tipo de dado pré-carregado. Pelo menos eu só conheço esses dois pacotes.

[02:55] Para carregar, vamos um passo de cada vez. É só colocar data, train_set recebe datasets.MNIST, que foi um dataset que eu escolhi de dígitos feitos à mão. Como vamos baixar, eu quero que seja baixado na raiz. Quero conjunto de treino. Eu não vou entrar em detalhes sobre transformações em imagem, mas o que é muito valioso para qualquer tipo de dados que estivermos trabalhando é a transformação para tensor.

[04:18] Vamos importar o transformer e podemos colocar toTensor. Vou fazer isso para o treino e para o teste. Posso imprimir quantas amostras de treino quero. O comprimento dessa estrutura que tem sete. E amostras de teste são o comprimento dessa estrutura test_set.

[05:55] Se olharmos o type das informações, o que veremos é que a variável train_set é uma classe específica do dataset. Quando trabalhamos com datasets próprios nossos, vamos ter que implementar uma classe específica, dessa mesma forma.

[06:26] Cada elemento desse conjunto é uma tupla que sempre vai obedecer a organização primeiro dado e depois rótulo. Se eu imprimir aqui, ele é uma tupla que vai ter o dado, que é a imagem, e o rotulo.

[07:00] Podemos iterar no dataset e observar algumas amostras. Posso chamar pelos índices. Dado, rótulo recebe train_set. Vou plotar figura, imshow e título. Vou ver três amostras do meu conjunto de treino, mas para isso preciso importar lá em cima o matplotlib.

[08:23] O detalhe aqui é que temos 70 mil amostras, sendo 60 mil de treino e 10 de teste, mas elas ainda não estão carregadas na memória. Uma das vantagens do Pytorch é que quando ele carrega os dados com a base dataset é porque é extremamente necessário. Se eu colocar uma transformação aleatória aqui, como um random crop, quando eu rodar de novo o carregamento, ele vai mostrar três recortes diferentes da mesma amostra.

[09:30] Isso é só para mostrar que cada vez que indexamos um item do dataset, lemos essa amostra do arquivo e aplicamos as transformações. Cada vez que chamamos um item estamos recarregando na memória. Isso é extremamente útil para liberar espaço de memória.

[09:52] Outra vantagem absurda é a classe dataloader. Vamos importar e ver como o Pytorch organiza esses carregamentos. O dataloader separa dados em batches, embaralha os dados para você e carrega os batches em paralelo utilizando diferentes processos.

[11:00] Como aquele dado só vai ser carregado na memória quando você indexar aquela amostra, isso pode ser um gargalo, porque esse processo de leitura e escrita no hd demora muito. O dataloader vai carregar vários batches ao mesmo tempo para que o processador não fique ocioso.

[11:23] Carregamos lá em cima o pacote do dataloader e agora vamos criar nosso train_loader, que vai receber um objeto do tipo dataset, o tamanho do batch, se ele vai embaralhar as amostras e quantos processos ele vai carregar. E temos o test_loader. A primeira grande diferença é que o dataloader não pode ser indexado. Tenho que colocar em um comando de iteração.

[15:16] Agora temos um batch de tamanho 20 e uma amostra de tamanho 1 por 28 por 28. Temos uma imagem quadrada com um canal de cor. Se copiarmos o plot que fizemos anteriormente, consigo plotar igual plotei lá em cima, mas direto do batch. Ele plotou uma amostra de treino.

[16:30] O que vamos fazer em seguida, no próximo vídeo, é fundamentar uma rede simples para classificar essas informações e ver como fazemos o fluxo de treinamento da forma correta.