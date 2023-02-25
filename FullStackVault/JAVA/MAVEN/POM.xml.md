[00:13] Chegou a hora de[[Maven]] entendermos melhor como o Maven baixa essas dependências. Se analisarmos o `pom.xml`, em nenhum local dissemos de onde que o Maven vai baixar essas dependências, se é da internet ou do computador.

[00:28] Isso não foi configurado porque, por padrão, o Maven vai primeiro buscar no repositório local que está no seu computador. Daqui a pouco eu mostro esse repositório para vocês. E se ele não encontrar essa dependência no repositório local, ele pesquisa na internet em um repositório central do próprio Maven.

[00:45] Se você quiser conhecer um pouco sobre esse repositório central, você pode abrir o Google e pesquisar “Maven repository” e vai aparecer esse site, [mvnrepository.com neste link](https://mvnrepository.com/). Esse é o repositório central do Maven.

[01:02] É onde estão todos os projetos, os _frameworks_, as bibliotecas e com tudo disponibilizado nesse repositório central do Maven. É que ele faz a consulta e faz o download do JAR e das dependências conforme o seu projeto demandar. Esse é o repositório central.

[01:18] Porém, pode acontecer de determinada dependência que você quer utilizar no seu projeto não estar disponibilizada no repositório central no Maven e estar disponibilizado em um outro repositório de outra empresa, ou pode ser até um repositório privado, interno da sua organização.

[01:36] Você quer manter um controle melhor, não quer que o pessoal da área de programação baixe diretamente da internet. Você quer deixar tudo local na sua empresa. Tem como você configurar um repositório interno da sua empresa ou utilizar um outro repositório que não seja o do próprio Maven.

[01:52] Para fazer isso é só você vir no arquivo `pom.xml`. Dentro da _tag_ `project`, da _tag_ raiz do `pom.xml`, você adiciona uma _tag_ chamada "repositories". Eu já tenho ela copiada, só para não perdermos muito tempo. Vou colar e essa é a _tag_ `<repositories>`. Aqui dentro você pode adicionar um ou mais repositórios, que o Maven sempre vai procurar a ordem de declaração.

```php-template
<project xmlns="http://maven.apache.org/POM/4.0.0"

//código omitido

    <repositories>
        <repository>
            <id>spring-repo</id>
            <url>https://repo.spring.io/release</url>
        </repository>
    </repositories>
</project>
```

[02:17] Tem a _tag_ `<repository>`, tem o `<id>`. Aqui, por exemplo, eu coloquei o repositório do _Spring_. O _Spring_ tem um repositório próprio que tem lá os JAR, as bibliotecas do _Spring_.

[02:27] Tem o `<id>` e uma `<url>`, o que interessa mesmo é só a URL, `<url>https://repo.spring.io/release</url>`. A partir de agora quando eu solicitar para o Maven adicionar uma nova dependência no projeto. Ele vai pesquisar nesse repositório, um novo repositório remoto que você acabou de adicionar.

[02:41] Em `<url>https://repo.spring.io/release</url>` não precisa necessariamente ser um repositório hospedado na internet. Ao invés de “http” poderia colocar “file:///home/”, uma pasta da minha máquina, ou poderia ser “[http://ip”](http://xn--ip-02t/) de um servidor interno da sua empresa. Pode ser algo interno, algo local no seu computador ou algo hospedado na internet - seja um repositório no Maven ou de outros projetos.

[03:16] Tem o repositório do _Spring_, tem o repositório também da _JBoss_, tem alguns outros repositórios que você pode utilizar. Vou deixar esse salvo aqui de exemplo, `<url>https://repo.spring.io/release</url>`.

[03:25] Toda vez que você adiciona uma nova dependência no `pom.xml`, o Maven primeiramente vai olhar no _cache_ local da sua máquina para ver se já existe essa dependência salva no seu computador, porque aí ele não precisa acessar nenhum endereço para baixar essas dependências, então acaba sendo mais rápido.