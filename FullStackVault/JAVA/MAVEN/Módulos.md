[00:00] Nesse vídeo vamos aprender mais um recurso do Maven, que é a ideia de você ter **módulos**. Às vezes, você tem aplicações que são maiores, são complexas e você quer modularizá-las, quer dividi-las em alguns módulos com projetos separados. É possível fazer isso com o Maven.

[00:21] Hoje, como já temos o Java 9 que já tem o sistema de módulos, você poderia usar o esquema do Java 9 para uma modularização de aplicação. Antes disso, você não tinha esse recurso no Java e uma das maneiras de fazer isso era utilizando, por exemplo, o Maven. O Maven tem um suporte para módulos onde você consegue criar uma aplicação que vai funcionar como pai de outras aplicações e você tem esses módulos e essas dependências entre módulos.

[00:47] Eu vou mostrar esse recurso para vocês agora. Como aquela aplicação que eu estava usando era uma aplicação bem simples, só de exemplo para nós focarmos no Maven, eu tenho uma outra aplicação que eu vou importar no Eclipse e ela já está utilizando esse esquema de módulos. Vamos entender com calma.

[01:02] No _package explorer_ vou clicar em “Import projects”, vou filtrar pelo, digitando “maven” em _"Select an import wizard"_ e selecionar “Existing Maven Projects", clicar no botão "Next", vou escolher o diretório em "Browser" que vai ser minha pasta chamada “clean-architecture”. Clico em “OK”. Perceba que ele encontrou um `pom.xml`, só que dentro tem mais três `pom.xml`, "rh-domain/pom.xml", "rh-web/pom.xml" e "rh-persistencia/pom.xml" - justamente porque ele detectou que esse é um módulo, um projeto dividido em módulos.

[01:28] Vou clicar em “Finish”. Ele importou, só que olhe só que legal, ele importou quatro aplicações separadas do lado esquerdo da tela.

[01:36] Você tem em _"Package Explorer"_ esse “rh-domain”, “rh-persistencia”, “rh-web” e tem esse “Clean-architecture”. Esse primeiro projeto “Clean-architecture” é apenas o projeto principal, é o projeto pai (_parent_), ele serve apenas para agrupar os módulos. Perceba que dentro dele tem justamente as pastas dos três módulos e um `pom.xml`.

[01:59] Vamos dar uma olhada nesse `pom.xml`. O que significa isso? Como que eu configuro um projeto para ser um pai, um _parent_, para agrupar outros projetos? Você tem o `pom.xml` tradicional, temos `<modelVersion>4.0.0</modelVersion>`, `<groupId>`, `<artifactId>` e `<version>`.

[02:15] A diferença é o `<packaging>pom</packaging>`, ao invés de ser JAR e WAR, tem essa questão de ser um `pom`. Quando você tem um projeto que vai ser um _parent_, o _packaging_ dele tem que ser `pom`. É para isso que serve esse empacotamento.

[02:28] Temos umas propriedades `<properties>` para configurar o Java 8, configurar o projeto como UTF-8. Tem as dependências `<dependencies>` e uma _tag_ nova, `<modules>` - e nessa _tag_ listamos quais são os módulos pertencentes a esse `pom`, a esse projeto principal.

[02:47] Em `<modules>` temos `<module>rh-domain</module>`, `<module>rh-web</module>` e `<module>rh-persistencia</module>`. Estamos declarando exatamente esses três módulos que apareceram em _"Package explorer"_ e _"clean-architecture"_ é só o projeto principal.

> Código _clean-architecture-pom.xml_:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>br.com.caelum.fj91</groupId>
    <artifactId>rh</artifactId>
    <version>1.0</version>
    <packaging>pom</packaging>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
        <maven.compiler.target>1.8</maven.compiler.target>
        <maven.compiler.source>1.8</maven.compiler.source>
    </properties>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.mockito</groupId>
            <artifactId>mockito-all</artifactId>
            <version>1.10.19</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <modules>
        <module>rh-domain</module>
        <module>rh-web</module>
        <module>rh-persistencia</module>
    </modules>

</project>
```

[02:59] Ele está retornando vários erros, é por conta da versão do Java e versão do Maven utilizada nesses projetos. A princípio isso não vai influenciar em nada, não vamos perder muito tempo com isso.

[03:13] Agora vamos analisar esses módulos. Se olharmos, vamos pegar esse módulo "rh-domain". Aplicação Maven `src/main/java`, `src/test/resources`, vamos para o `pom.xml` que é o que interessa. No `rh-domain/pom.xml`, perceba que no `<modelVersion>` e `<artifactId>` não tem `groupId` porque tem essa outra _tag_ nova chamada `<parent>` e é ela que eu configuro quem é o módulo pai desse módulo onde estão as configurações principais.

[03:44] Passo o `groupId` e o `artifactId` do módulo pai. Ele mostrou que o `groupId` é esse, `<groupId>br.com.caleum.fj91</groupId>`. O `artifactId` é `<artifactId>rh</artifactId>`, que é justamente o `groupId` e `artifactId` do meu `pom.xml`, que estão declaradas no `pom.xml` do projeto _parent_. A versão específica desse projeto, `<version>1.0</version>`.

> Código em `rh-domain/pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <artifactId>rh-domain</artifactId>

    <parent>
        <groupId>br.com.caelum.fj91</groupId>
        <artifactId>rh</artifactId>
        <version>1.0</version>
    </parent>

</project>
```

[04:04] Como eu estou declarando que tenho um projeto _parent_, é como se fosse a herança do Java. No projeto _parent_ em `clean-architecture/pom.xml`, como temos umas dependências `JUnit` e `Mockito`, automaticamente esse projeto herda essas dependências. Se eu quiser usar o `JUnit` nesse projeto _rh-domain_, não preciso declarar a independência porque ele já está herdando.

[04:23] Já sei quais são os problemas que estão acontecendo. Como eu acabei de importar esses projetos, eles não estão instalados no meu repositório local. A _tag_ `<parent>` não encontrou o projeto `br.com.caleum.fj91` e como no último vídeo tinha configurado esse _proxy_ só de exemplo, vou desabilitá-lo no arquivo "settings.xml".

[04:42] Vou colocar `active>false</active`, porque ele deve está tentando baixar da internet, baixar desse _proxy_ e não existe esse _proxy_. Vou ocultar esse _proxy_. Agora vou só rodar esse projeto - “clean-architeturie > Run As > Maven Install”, aí ele vai compilar e vai instalar no meu repositório local. Deve resolver esses problemas.

[05:05] Como é a primeira vez que eu estou executando o projeto no computador, demora um pouco porque ele vai baixar as dependências e tudo mais. Já baixou e começou a rodar.

[05:16] Perceba que interessante: eu mandei ele fazer o _build_ do projeto `clean-architeture`, que é o projeto pai, mas como ele tem três módulos, também faz o _build_ dos três projetos, dos três módulos. Para cada módulo que ele tiver vai fazer o _build_ de cada um dos módulos, vai baixar as dependências específicas de cada um dos módulos. Quando você tem um projeto modularizado, na hora de gerar o _build_ é diferente o projeto.

[05:40] “Rodrigo, eu vou ter que gerar o _build_ de cada um desses projetos separados, um por um?” Não! Você vai fazer tudo pelo _parent_. É no _parent_ que você faz o _build_, porque o _parent_ já contém todos esses módulos. Ele já vai fazer o _build_ de tudo ao mesmo tempo.

[05:54] Até aquela vantagem da herança temos. “Eu preciso adicionar uma dependência que é comum para todos os projetos”. É só você adicionar no `pom.xml` do projeto _parent_ - como é o caso do `JUnit` e do `Mockito`.

[06:05] Se eu quiser escrever testes nesses três projetos, vou precisar do `JUnit`. Ao invés de declará-los separadamente, repetindo em cada um dos projetos, eu adiciono ele no `pom.xml` do projeto _parent_ e pronto. Projetos filhos, os módulos já automaticamente vão herdar por dependência.

[06:23] No console do Maven, vemos que ele está baixando as bibliotecas porque cada um dos projetos tem suas dependências específicas. Por exemplo: esse projeto `rh-web/pom.xml`, se olharmos o _pom_ dele, percebemos que também depende do projeto _parent_ e ele tem as dependências do _Spring boot_, dos outros módulos. Um módulo pode depender do outro, eu posso adicionar como dependência.

[06:50] Esse módulo `rh-web` quero que dependa do módulo de persistência. É só eu declarar `groupId`, `artifactId`, qual é versão, como uma dependência e ele vai baixar do repositório local - no caso, essa dependência.

[07:04] Como esses projetos estão executando apenas na minha máquina, a dependência só existe dentro da pasta “.m2”. Se eu quiser, posso enviar esses projetos para o _"Mvn Repository"_.

[07:15] É possível você criar um projeto seu e enviá-lo para o _Mvn Repository_ para você baixar da internet e outras pessoas conseguirem baixar da internet normalmente. Não precisa ser apenas local e envio por e-mail, ou algo do gênero.

[07:30] Ele vai continuar baixando as dependências e vamos continuar.

[07:35] Esse é um recurso extremamente útil quando trabalhamos com Maven e com aplicações modularizadas. Por exemplo: hoje em dia é bem comum o pessoal desenvolver aplicações seguindo a arquitetura de microsserviços. Aqui seria um exemplo de como você poderia organizar esses microsserviços.

[07:57] Como que eu faço para quebrar o meu projeto, separar a parte web, a parte da persistência, a parte de domínio, os subdomínios. Como é que eu faço para esses projetos conversarem entre si, se interligarem? Como é que eu vou gerar o _build_ desses 10, 5, 20 projetos quebrados, separados?

[08:15] Um exemplo: seria utilizar o Maven com essa estrutura de módulos. Você poderia criar um projeto, criar um projeto do tipo `pom`. Na hora que criamos o projeto Maven daqui dar para colher qual que o _packaging_. Se é JAR, se é WAR ou se é “pom.xml”. Você adiciona os módulos, adiciona as dependências comuns para todos eles e vai criando cada um desses módulos.

[08:38] Os módulos são aplicações Maven tradicionais. Se você criar um _new Maven Project_, normal, JAR ou WAR - dependendo da tecnologia que você usar no projeto, desenvolve o projeto, leve o código-fonte e as classes de teste.

[08:54] No `pom.xml`, você declara as dependências específicas de cada um desses projetos. Esse projeto tem essas dependências - _Spring boot_, _Tomcat_, _JSTL_, cada um tem suas dependências. Se um projeto depende de um dos módulos, você declara como uma dependência.

[09:14] O módulo nada mais é do que uma dependência. Pense em um módulo como sendo um projeto. Um módulo é um projeto e é considerado uma dependência, então eu posso ter um projeto que uma das suas dependências é um dos módulos. Não tem o menor problema.

[09:29] A única diferença especial mesmo é no projeto raiz. Além de ter os três módulos aqui, você precisa ter um projeto raiz, que é só o projeto que vai agrupar tudo. Dentro de `clean-architeture` só tem um atalho para cada um dos seus módulos e o “pom.xml” dele tem essa diferença de ter o `<packaging>pom</packaging>`. Fora isso, nada de mais. Dependências e módulos. Fora isso nada demais, é um projeto como outro qualquer.

[09:58] Agora finalmente terminou! Três minutos para rodar, baixar e instalar tudo. Ele buildou e perceba que no _build_ mostra o resumo.

[10:10] Ele fez o _build_, o `rh` (que é o projeto principal) e buildou o `domain`, o `persistencia` e o `web`.

[10:16] Para você gerar o _build_ de um projeto modularizado você gera o _build_ só do projeto _parent_ e ele gera cada um dos filhos específicos.

[10:25] Vou dar um _clean_ “ Maven > Update Project > OK”. O problema é algo específico do Maven, era alguma configuração dessa que estava faltando fazer o _build_ dos projetos e dar um _clean_ geral no projeto.

[10:45] Apresentei para vocês um exemplo de projeto utilizando módulos do Maven. Existem várias maneiras de desenvolver aplicações modularizadas, o Maven é uma delas e é bem interessante principalmente por conta das dependências que você consegue reaproveitar dependências e os módulos conseguem se comunicar - um módulo pode depender do outro módulo.

[11:07] Esse é um recurso bem bacana. Avalie se você trabalha em um projeto que usa arquitetura de microsserviços. Se não faz sentido separar os microsserviços em módulos do Maven, talvez seja interessante para o seu projeto.