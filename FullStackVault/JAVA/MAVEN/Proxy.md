[00:00] Outro recurso bem bacana do Maven é a configuração de _proxy_. Às vezes, isso vai ser extremamente útil para você.

[00:10] Se você usar o Maven no seu trabalho ou em alguma rede que tem _proxy_ para você configurar o acesso à internet, se você for usar o Maven nessa situação, você vai ter algum problema porque na hora dele baixar as dependências da internet não vai conseguir, porque precisa de um _proxy_. Sem um _proxy_ você não vai conseguir navegar. O Maven iria gerar um erro para você.

[00:31] Como eu faço para configurar um _proxy_ no Maven? A princípio, você pensaria: “basta abrir o `pom.xml`, deve ter alguma propriedade em algum lugar chamada _proxy_ ou algo do gênero! ” Só que na verdade não tem. Como isso não é algo do projeto. É um _proxy_, é uma configuração do Maven para o Maven acessar a internet não é algo específico de um projeto. Não fica no `pom.xml`.

[00:57] Existem algumas configurações do Maven e essas configurações que são externas ficam em um arquivo específico. Lembra daquela pasta “.m2”? Eu estou nela, dentro dela tem aquele diretório “repository”, que tem os JAR, as dependências e dentro se você quiser configurar alguma coisa, tem que criar um arquivo chamado “settings.xml”.

[01:22] Eu já criei esse arquivo e está vazio. Temos a _tag_ `</settings`, a _tag_ raiz do arquivo, tem os _namespaces_ do Maven. Você pega um desse exemplo na internet - não vai ficar memorizando isso - e aqui dentro vem configurações globais, configurações específicas do Maven e não necessariamente dizem respeito a um único projeto.

[01:45] Dentre essas configurações vem a configuração de _proxy_. Eu já tenho ela copiada vou só colar para não perdermos muito tempo. É dessa maneira que configuramos um _proxy_.

> Código em `setting.xml`:

```php-template
<settings xmlns="http://maven.apache.org/SETTINGS¹1.0.0"

//código omitido

    <proxies>
        <proxy>
                    <id>genproxy</id>
                    <active>true</active>
                    <protocol>http</protocol>
                    <host>proxyHost</host>
                    <port>3128</port>
                    <username>username</username>
                    <password>password</password>
        </proxy>
    </proxies>

    </settings>
```

[01:56] Dentro da _tag_ raiz `<settings>` você coloca a _tag_ `<proxies>` e dentro dela você coloca os _proxys_ que você tiver, geralmente é só um. Como podem ter vários, você coloca um `<id>meu-proxy</id>`, `active>true</active>` para dizer que esse _proxy_ está ativo. Qual é o protocolo? `protocol>http</protocol>`.

[02:13] Aí você vai ter que conhecer o _proxy_ que você utiliza. É HTTP? É HTTPS? O _host_. Qual é o endereço do _proxy_? Provavelmente vai ser algo assim `<host>http://ip</host>`, esse é o IP interno da essa sua empresa que funciona como um _host_.

[02:33] Qual é a porta? `<port>3128</port>`. Vai ter que conhecer. E se tiver _login_ e senha, qual é? `<username>username</username>`. E qual é a senha? `<password>password</password>`. Se não tiver _login_ e senha, o _proxy_ não exigir você pode ocultar essa _tag_ _username_ e _password_. No geral, quando tem _proxy_ tem usuário e senha, deve ser teu _login_ da rede, a sua senha da rede.

[02:49] Dessa maneira você configura o _proxy_. Vou salvar e pronto, basta salvar isso daqui nesse arquivo `settings.xml` dentro do diretório “.m2”! A partir de agora, o Maven, quando for baixar as dependências e quando precisar acessar a internet, vai levar em consideração esses _proxys_.

[03:09] Outra coisa que daria para fazer: lembra no projeto que configuramos um repositório em `pom.xml`, além de usarmos o repositório central do Maven? Dá para fazermos isso no `pom.xml` para ser um repositório específico desse projeto, mas dá para configurar repositório também no `settings.xml`, que ele fica valendo para todos os projetos.

[03:28] Só que nesse caso, como não dá para configurar no `settings.xml` e no `pom.xml`, se tiver um no `pom.xml` ele tem prioridade, ele vai meio que sobrescrever o que está configurado no `settings.xml`. O que é específico do projeto tem precedência em relação ao `settings.xml` - que é mais global, digamos assim.

[03:50] Mais um recurso, às vezes a galera quebra a cabeça por conta disso: você vai usar o Maven em casa. Funciona e quando usar no trabalho tem alguma dor de cabeça porque tem um _proxy_ e para configurar não é no `pom.xml`, é nesse arquivo de configurações.