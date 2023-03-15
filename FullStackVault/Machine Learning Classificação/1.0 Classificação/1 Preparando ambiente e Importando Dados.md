## Base de dados

A base de dados utilizada durante o curso é proveniente da plataforma Kaggle e pode ser encontrada neste [link](https://www.kaggle.com/mnassrib/telecom-churn-datasets?select=churn-bigml-20.csv). Essa base passou por alguns tratamentos e por esse motivo está levemente diferente da disponibilizada no Kaggle.

Para baixar a base de dados tratada, você pode clicar [aqui](https://github.com/alura-cursos/ML_Classificacao_por_tras_dos_panos/tree/main/Dados).

## Google Colab

Para o desenvolvimento desse curso utilizaremos a ferramenta [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb), que é um serviço de nuvem hospeado pelo próprio **Google** e incentiva a pesquisa em machine learning e inteligência artificial. Esse ambiente em nuvem traz algumas vantagens:

-   Não necessita de configuração para começar a rodar os códigos;
-   Acesso gratuito a GPUs;
-   Permite fácil compartilhamento do código desenvolvido.

### Como subir arquivos para o Google Colab?

Após baixar o arquivo com os dados que serão utilizados nas próximas aulas, vamos realizar o upload no ambiente de desenvolvimento do Colab.

1 - O primeiro passo é clicar em **arquivos** e depois em **Fazer upload para o armazenamento da sessão**.

![alt text: Tela do colab com a aba arquivos aberta e marcada por um quadrado vermelho. Abaixo do título “Arquivos” há uma seta vermelha direcionada para o ícone de “Fazer upload para o armazenamento da sessão”.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/01/Aula1-img1.png)

2 - Em seguida, será aberto o diretório de pastas da sua máquina onde você poderá selecionar o arquivo **telecom_dados.csv** baixado anteriormente.

![alt text: Diretórios de pastas de um computador com a pasta Downloads selecionada. Dentro dessa pasta, o arquivo telecom_dados está destacado por uma seta vermelha. Na parte inferior direita da tela, a opção Abrir também encontra-se destacada por outra seta vermelha.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/01/Aula1-img2.png)

Para conferir que o arquivo foi importado corretamente para o Google Colab, você pode abrir novamente a aba **Arquivos** e verificar se o nome do arquivo encontra-se nessa aba.

![alt text: Aba “arquivos” do google colab com 3 arquivos, de cima para baixo: pasta “drive”, pasta “sample_data”, arquivo “telecom_dados.csv”. Há um retângulo na cor vermelha destacando o arquivo “telecom_dados.csv”.](https://caelum-online-public.s3.amazonaws.com/2422-machine-learning/01/Aula1-img3.png)

Uma observação importante é que ao fechar o seu ambiente de trabalho do Colab, os arquivos que você realizou o upload vão sumir, sendo necessário realizar o upload novamente na próxima vez que for trabalhar no notebook.

Caso queira conhecer mais detalhes sobre o Google Colab, sugerimos a leitura do artigo [Google Colab: O que é, Tutorial de Como Usar e Criar Códigos](https://www.alura.com.br/artigos/google-colab-o-que-e-e-como-usar).[00:00] Parabéns. Você acaba de ser contratado como cientista de dados na grande empresa de telecomunicações Alura Voz.

[00:11] Nos seus primeiros dias você foi convidado para participar de uma reunião com a equipe de vendas. Lá foram passados alguns parâmetros importantes de serem acompanhados e controlados como, por exemplo, o Churn. Que representa a taxa de evasão dos clientes, ou seja, se esse cliente tem o potencial ou não de nos deixar. Você, como um cientista de dados todo experiente, logo faz uma indicação de uma possível solução para controlar esse número de Churn. Você indica classificar os clientes como possíveis pessoas a deixarem ou não a nossa empresa.

[00:58] Para começar esse trabalho você solicita à equipe de vendas as informações que iremos mexer exatamente agora. Vamos lá.

[01:07] Durante todo o andamento do projeto nós vamos trabalhar com a linguagem de programação Python e a sua biblioteca Pandas, muito conhecida na área de ciência de dados por auxiliar na transformação, limpeza e modificação dos dados.

[01:23] Para começarmos vamos importar a biblioteca e sua função, utilizando o `import pandas` e apelidando essa biblioteca com `as pd`, que vai facilitar chamar as funções dessa biblioteca lá na frente, `import pandas as pd`.

[01:41] Agora vamos clicar em "Shift Enter" e rodar a célula. Também podemos clicar aqui no canto esquerdo da célula na seta que irá rodar da mesma forma que o "Shift Enter". A biblioteca está carregada.

[02:00] Agora, vamos precisar importar nossos dados, nossas informações que a equipe de vendas que a equipe de vendas passou. Começamos criando uma variável chamando `dados` que irá receber essas informações, armazenar para que ao decorrer do projeto possamos chamar apenas os dados e, assim, carregar todas as informações que temos da equipe de vendas, `dados = pd.read_csv(' ')`.

[02:32] O `pd`, estamos chamando a biblioteca Pandas, `.read_csv`, que indica que estamos querendo ler o tipo de arquivo em formato CSV. Abre e fecha parênteses, abre e fecha aspas.

[02:45] Aqui entre as aspas e o parênteses nós vamos colocar o caminho do arquivo onde o nosso arquivo está armazenado. E, claro, uma etapa muito importante que não pode deixar de ser vista é o preparando ambiente. E lá já sabemos que o nosso arquivo se encontra aqui no _notebook_.

[03:02] Vamos para a pasta de arquivos, clicamos a direta do nome do nosso arquivo nos três pontinhos e "Copiar caminho". Fechamos a aba do lado e colamos o caminho entre as aspas e o parênteses.

```ini
dados = pd.read_csv('/content/sample_data/Customer-Churn.csv') 
```

Da mesma forma rodamos a células e os dados estão carregados.

[03:24] Agora, vamos ver de fato, quais são as informações que temos, quantas informações temos. Primeiro vamos chamar a função _shape_, `dados.shape` que irá nos mostrar o seguinte: temos dois valores entre parênteses, `(7043, 18)`, o primeiro representa as linhas do nosso conjunto de dados, ou seja, quantos clientes temos disponíveis na nossa base. Temos 7043 clientes. À direita, temos o 18 que representa o número de colunas do nosso conjunto de dados ou também as nossas variáveis.

[04:04] Você deve estar se perguntando: "Ana, eu quero saber de fato quais informações nós temos." Vamos chamar a função _head_ para mostrar as primeiras cinco linhas dos nossos clientes, então `dados.head()` e rodamos a célula.

[04:24] Pronto. Aqui temos as cinco primeiras linhas de clientes, os cinco primeiros clientes da nossa base, e as informações que contém dentro dela. Vamos ver com mais detalhes.

[04:35] A primeira coluna é a que indica maior de 65 anos, sendo que 1 é igual a sim e 0 é igual a não. E vemos que os primeiros clientes são todos menores de 65 anos. Depois temos o Cônjuge, se a pessoa é casada ou não. Sim e não. Nos dependentes é se há filhos ou pessoas que dependam dessa pessoa, sim e não.

[05:05] Os meses de contrato que é o tempo que essa pessoa está atualmente com um contrato em vigor, ou seja, o contrato está em andamento. O telefone fixo, se a pessoa possui ou não telefone fixo. E agora vamos entrar nos serviços adicionais que dependem um dos outros, por exemplo, as várias linhas telefônicas.

[05:28] Temos a questão de “sem serviço telefônico”, o que quer dizer que a pessoa não tem telefone fixo ou não e sim, que indica que a pessoa tem telefone fixo, mas não tem várias linhas. E sim, caso ela tenha várias linhas. Depois temos o serviço de internet, que mostra o tipo de internet que essa pessoa contratou, DSL, fibra óptica, cabo.

[05:54] Depois temos segurança online, também sim ou não. Se ela contratou segurança online e no caso dela ter ou não assinado o serviço de internet. O _backup_ online também depende do serviço de internet, sim e não. Seguro no dispositivo também depende da internet e se a pessoa quer ou não o seguro. O suporte técnico, se a pessoa quer esse adicional de um tempo menor de espera, um suporte mais rápido, sim ou não.

[06:24] TV a cabo, se a pessoa assinou ou não. _Streaming_ de filmes, se a pessoa assina ou não e depende da internet também. E temos também o tipo de contrato, mensalmente, anual, semestralmente e assim por diante. O pagamento online, se a pessoa decidiu receber por e-mail, pagar online ou se ela prefere receber no conforto da casa dela por Correios, sim e não.

[06:54] A forma de pagamento que se a pessoa paga em débito em conta, cheque de digital, cheque de papel, cartão de crédito. Conta mensal, que é o valor que ela paga mensalmente no atual contrato dela. E o Churn, se a pessoa deixou de ser a nossa cliente ou não.

[07:22] Vamos relembrar o nosso objetivo. Nós recebemos essas informações com o objetivo de selecionar algumas características para poder classificar potenciais clientes a deixarem ou não. Vocês se lembram?