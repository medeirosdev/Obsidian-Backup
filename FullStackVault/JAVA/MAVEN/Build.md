[[Maven]]
[00:00] Na última aula aprendemos sobre um dos pilares do Maven, essa parte de gerenciamento de dependências. Aprendemos a adicionar dependências no projeto, a pesquisar por essas dependências no repositório central do Maven e aprendemos também essa questão de repositórios, o _cache_ local, repositório local.

[00:20] Esse era um dos grandes pilares no Maven, gerenciamento de dependências, conforme tínhamos discutido. Um outro pilar essencial para uma aplicação é a questão do _build_, como que eu faço para buildar a aplicação, para compilar, modificar arquivos, criar diretórios e gerar o pacote do projeto para fazer o _deploy_ e ele entrar em produção.

[00:41] Nessa aula o objetivo vai ser esse, aprender sobre o _build_ do projeto. Na realidade, o Maven já tem embutido essa questão do _build_, podemos executar o _build_ da aplicação pelo pela IDE, pelo Eclipse, ou pelo _prompt_ de comando, no terminal.

[00:58] Vou fazer nos dois casos porque essa parte de rodar comandos para o _build_ também é comum de ser executada pelo _prompt_ de comando. No prompt, eu estou no diretório da minha aplicação. Se eu digitar um `ls` para listar os arquivos, tem o `pom.xml`, o `src` e aqui lembra tem aquele `mvn`.

[01:17] Se você já estiver adicionado no _path_ do sistema operacional como variável de ambiente, diretório onde descompactou o Maven, você já consegue rodar pelo `mvn` diretamente, sem passar o caminho completo da pasta `bin` do Maven.

[01:29] `mvn` e o que você passa é um objetivo, que é chamado de _goal_. Existem vários objetivos, várias tarefas que o Maven pode executar em cima do seu projeto relacionadas com o _build_ da aplicação.

[01:40] Por exemplo: tem o `mvn compile`, serve para compilar. Eu estou falando "Maven compila" e aí ele vai procurar no diretório onde eu estiver, tem o `pom.xml`. Vai encontrar as configurações do projeto, vai encontrar os arquivos e fazer a compilação. Se eu usar a tecla “Enter”, ele começará o processo de compilação. Ele encontrou o nosso projeto “loja”, executou e compilou com sucesso.

[02:07] Se dermos uma analisada no `pom.xml`, em nenhum lugar que eu disse nada sobre _build_, sobre versão de Java e tudo mais. Lembra que tinha aquele comando que eu tinha comentado com vocês, que às vezes você precisa atualizar o projeto? Você clica com o botão direito do mouse no projeto “loja > Maven > Update Project” e nós podemos simular isso no _prompt_ de comando.

[02:29] Se executarmos um `mvn clean`, que é um outro _goal_ (objetivo) do Maven, que é só para limpar o diretório _target_, limpar os arquivos e deixar o terreno preparado, se você quisesse compilar. Vamos executar um `clean`. É sempre importante limpar, você já tinha arquivos lá na _target_, talvez ele pule alguma etapa.

[02:49] Agora se eu executar um `mvn compile`, vamos ver o que vai acontecer. Como eu já havia executado antes, tinha dado certo. Agora deu um erro, que era o erro que eu estava esperando.

[03:00] Ele falou: “O Java 5 não é mais suportado, tem que ser pelo menos o Java 6”. Temos um problema, ele está, por padrão, configurado que o Java está na versão 5. Em nenhum lugar do `pom.xml` dissemos qual é a versão do Java.

[03:04] Então tem um padrão que ele pega como Java 5. Só que para configurar isso podemos adicionar no `pom.xml`, eu vou colar que eu já tenho salvo só para não perder muito tempo. Existe essa _tag_ `<build>`, que é justamente utilizada para configurarmos coisas do _build_ e coisas opcionais.

> Código `pom.xml`:

```php-template
<project xmlns="http://maven.apache.org/POM/4.0.0"

//código omitido

<build>
        <plugins>
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
</build>

</project>
```

[03:32] Tem `<plugins>`, que depois vamos ver com calma. Existe esse _plugin_ chamado `maven-compiler-plugin`, que é para configurarmos qual é a versão do Java. Tem essa _tag_ `<configuration>`, o código-fonte está na versão 11 e é para ele compilar e gerar os arquivos binários na versão 11 também.

[03:50] Agora, eu já adicionei esse _plugin_ e com isso eu já ensinei ao Maven qual é a versão do Java utilizada na aplicação. Se rodarmos novamente no _prompt_, podemos dar um `mvn clean` e podemos passar mais de um _goal_ ao mesmo tempo. É só escrever nome do _goal_ + "Espaço" + nome do segundo _goal_.

[04:10] Eu posso passar um _compile_, `mvn clean compile` - ele vai executar um _clean_ e se tudo der certo ele vai para o próximo _goal_ - que no caso é o `compile`. Vai fazer um _clean_ do projeto. E agora compilou tudo certo, detectou a versão do Java 11 e apareceu essa mensagem: “BUILD SUCCESS”. Gerou o _build_ com sucesso, ele fez a tarefa que você mandou ele fazer que é dar um _clean_ e um _compile_.

[04:29] Cadê as classes compiladas? Como é que eu verifico isso? Se você olhar em cima no terminal, informa que compilou um _source file_. O projeto só tem uma única classe, para o diretório “loja/target”.

[04:44] Lá na pasta, entramos em “eclipse-workspace > loja > target”, tem esse diretório _target_, que é onde ele compila. Todo _build_ vem para cá. Tem `classes`, tem aquele arquivo “messages.properties”, que estava no diretório “source/main/resources”, que tinha criado de exemplo. Ele jogou para cá faz parte da compilação. Ele criou pastas "“br” > “com” > “alura” > “loja”, está em "loja" o arquivo `.class`, ele compilou para cá.

[05:13] Dentro do diretório _target_ é onde ele executa, joga os artefatos, tudo o que foi gerado no processo de _build_. Em `pom.xml` na parte do código que acabamos de colar poderíamos configurar outras informações também, tudo que for relacionado com _build_ configuramos na _tag_ `<build>`.

[05:27] Outros _goals_ que existem e são importantes - além do _clean_ e do _compile_, eu tenho testes automatizados na aplicação. Quero executar os meus testes, eu posso executar `mvn test`. Ele vai verificar se tem algum teste automatizado com `JUnit` na aplicação, vai executar os testes e dizer se passou ou se falhou.

[05:46] No caso falhou e em cima ele te dá um relatório, resultado, em _Results_.

[05:51] Ele rodou um teste e esse único teste falhou. Ele te informa qual foi o teste que falhou, foi na classe produto teste e a mensagem “Not yet implemented”.

[05:59] Isso foi porque tínhamos deixado de propósito uma classe de teste de exemplo em `ProdutoTest.java` que está com um _fail_ , `fail(“Not yet implemented”)`, então ele vai falhar. Vou só remover essa parte de `fail`, não vou escrever um teste, só para emular. Tem um teste, vamos rodar um `mvn test` novamente para ver. Ele vai executar e agora foi com sucesso.

[06:20] Só que perceba que antes de executar essa tarefa de testes, ele imprimiu um monte de coisas. Você não precisa ficar preocupado com tudo isso, mas ele fala algumas coisas do _build_ e de _plugin_. De _plugin_ pode ignorar, mas ele fala. Nessa parte é que começou a brincadeira, "Building loja 1.0.0" ele começou a fazer o _build_ do “loja”. É aquela versão do projeto que tínhamos configurado e aí ele executou esse _plugin_, `maven-resources-plugin:2.6:resources`, para pagar os _resources_ do projeto.

[06:48] E rodou o Maven _compile_. Ele fez um _compile_ antes, embora só tenha executado `mvn test`, o _compile_ é pré-requisito do teste, para nós rodarmos os testes precisamos compilar o código-fonte primeiro.

[06:58] As classes de testes vão utilizar as nossas classes, elas precisam estar compiladas. Depois é que ele veio aqui, gerou os _resources_ de testes, compilou as classes de testes e executou os testes. Aí vem um relatório dizendo se passou ou se falhou.

[07:14] Agora no caso, rodou 1, não deu nenhuma falha: "Tests run: 1, Failures: 0, Errors: 0, Skipped: O, Time elapsed: 0. 094 sec". Tem um relatório dos testes ele te mostra em quantos segundos rodou e o _build_ foi executado com sucesso, "BUILD SUCCESS".