[[Maven]]

Para a aula funcionar é preciso adicionar a dependencia do _jacoco_ como apresentado abaixo:

```xml
<dependencies>
    <dependency>
        <groupId>org.jacoco</groupId>
        <artifactId>jacoco-maven-plugin</artifactId>
        <version>0.8.8</version>
    </dependency>
</dependencies>
```

[00:00] Agora que já completamos os dois principais pilares, a parte de gerenciamento de dependências e de _build_; nessa aula, vamos conhecer alguns outros recursos adicionais do Maven. São alguns recursos que podem te ajudar em algumas situações. Um deles é justamente esse recurso de _plugin_.

[00:21] Eu tinha comentado brevemente quando precisamos configurar a versão do Java da nossa aplicação, que por padrão o Maven estava considerando que era Java 5. Para você trabalhar com _plugins_ na _tag_ `<build>` em `pom.xml` tem essa _tag_ chamada `<plugins>`.

[00:36] Um _plugin_ nada mais é do que algo que vai modificar, manipular o _build_ da aplicação. Durante o _build_ do projeto você pode adicionar _plugins_, que farão alguma coisa. Existem diversos _plugins_, cada um com um objetivo.

[00:49] Tínhamos conhecido esse _plugin_, que é o `maven-compiler-plugin`. Éum _plugin_ do próprio Maven, onde configuramos qual é a versão do Java, dos arquivos `.java` da aplicação e do `.class` na hora em que ele for fazer a compilação. Passamos que é a versão 11.

[01:08] Um _plugin_ tem esse objetivo, de adicionar algum recurso para o _build_ da aplicação. Se abrirmos o navegador e no Google pesquisarmos "maven plugins", existe aqui site do [Maven neste link](https://maven.apache.org/plugins/) - que explica o que são os _plugins_ e ele tem uma lista de _plugins_ que são suportados por ele.

[01:28] Tem os _plugins_ padrões do Maven para fazerem _clean_, _deploy_, _test_. Tem alguns _plugins_ para empacotamento de acordo com algumas tecnologias - tipo `ear`, `ejb` e aplicações de JavaEE. _Plugins_ para relatórios de `changeLog` de mudanças que foram feitas na aplicação, e documentação do site, `pmd` para testes e boas práticas de programação.

[01:54] _Plugins_ para ferramentas do _Ant_. Tem vários _plugins_, alguns antigos estão aposentados, esses daqui em _"Retired"_ não funcionam mais. Tem alguns que estão fora da zona do Maven _("Outside The Maven Land")_ e não foi Maven que desenvolveu, mas ele suporta e destaca.

[02:11] Alguns deles são interessantes. Por exemplo: esse do `jetty`, esse daqui é um _plugin_ para você ter um servidor embutido na aplicação. Ao invés de ter um `tomcat` adicionado externo no Eclipse, você pode adicionar o `jetty` diretamente no Maven e executá-lo pelo Maven.

[02:32] No caso do `jetty`, como é que funciona? Se você adicionar esse _plugin_ do `jetty` no _prompt_ você poderia vir e executar `mvn jetty:run`. Esse "Jetty:" é o nome do _plugin_, o prefixo do _plugin_ e o "run" seria o _goal_.

[02:47] Perceba que um dos objetivos dos _plugins_ é eu posso adicionar novos _goals_ ao Maven nas etapas de _build_ do Maven. Não existe esse _goal_ `run` no Maven, por isso que ele está com `jetty:`. Aí, seu eu tentar executar, vai falhar porque eu não adicionei esse _plugin_ no `pom.xml` da aplicação.

[03:04] Essa é a ideia do _plugin_, ele serve para fazer alguma coisa no projeto - em especial na etapa de _build_. Tem vários _plugins_ no site e um deles eu vou mostrar para vocês - é um relacionado com testes automatizados, com a parte de relatório e cobertura de testes.

[03:21] É o _plugin_ chamado "Jacoco". É uma ferramenta que analisa o código-fonte da aplicação e te dá um relatório de cobertura de teste. A porcentagem de cada classe, de cada pacote está coberto por testes automatizados. Para você encontrar classes que ainda não foram testadas e coisas do gênero.

[03:37] Para adicionar um novo _plugin_ na _tag_ `<build>` tem a _tag_ `<plugins>`. Já tem um _plugin_. Uso a tecla “Enter” e vou colar. Eu já tinha copiado é um _plugin_ bem extenso. Agora vem um detalhe meio chato, cada _plugin_ funciona de um jeito, cada _plugin_ tem uma configuração diferente.

```xml
                        <plugin>
                                <groupId>org.jacoco</groupId>
                                <artifactId>jacoco-maven-plugin</artifactId>
                                <version>0.8.2</version>
                                <executions>
                                        <execution>
                                                <goals>
                                                        <goal>prepare-agent</goal>
                                                </goals>
                                        </execution>
                                        <execution>
                                                <id>report</id>
                                                <phase>test</phase>
                                                <goals>
                                                        <goal>report</goal>
                                                    </goals>
                                            </execution>
                                </executions>
                        </plugin>+
        </plugins>
```

[03:54] O _plugin_ no `maven-compiler-plugin` era só declarar o `artifactId` e essa _tag_ `<configuration>` com a versão do Java, `<source>` e o `<target>`. Simples assim!

[04:04] Agora esse do Jacoco não. Como ele não é do Maven, eu preciso do `<groupId>org.jacoco</groupId>` do `<artifactId>jacoco-maven-plugin</artifactId>`. Qual é a versão, `<version>0.8.2</version>`. Se ele tiver várias versões. Nesse têm uma _tag_ chamada `<executions>` - já que é para ele executar algum _goal_ em alguma fase do _build_ do projeto.

[04:21] Tem uma execução que é exigida por ele `<goal>prepare-agent</goal>`, que é para preparar e fazer uma análise do projeto. Tem uma outra `<execution>` - que é a principal, que é a de _report_, `<id>report</phase>`. O _goal_ se chama _report_ e ele será executado na fase de teste.

[04:37] Durante o _goal_ de teste, o Jacoco vai executar logo sequência esse _goal_ de _report_, `<goal>report</goal>` - que é o que vai gerar o relatório em si. Essa é a configuração do Jacoco. Você tem que consultar a documentação do _plugin_ para entender como você configura ele e como faz para executá-lo. No caso do Jacoco é dessa maneira.

[04:56] Vou salvar e vamos rodar pelo _prompt_ mesmo. Para rodar o Jacoco não se cria um _goal_ a mais - ele até cria aquele _goal report_, mas se você rodar o próprio `mvn test` já vai funcionar porque o _report_ no código está sendo configurado para rodar na fase de teste.

[05:13] Perceba que ele rodou os testes e na sequência, `jacoco-maven-plugin:0.8.2:report`. Ele executou o Jacoco, o _goal_ de _report_. Ele gerou um arquivo dizendo `target/jacoco.exec`.

[05:26] Se entrarmos lá no _target_ nas pastas do computador mesmo, tem um “jacoco.exec”, mas é um arquivo `.exec`, não tem como executarmos esse arquivo. Se você reparar tem uma pasta “site”, que é onde o Maven gera a documentação da aplicação. No caso não estamos usando nenhum _plugin_ para isso, por isso ele não tinha gerado.

[05:41] O Jacoco gera um _site_ para mostrar esse relatório. Na pasta “site” tem uma pasta “jacoco” e dentro tem um “index.html”. Ele gera uma página HTML com um relatório, se abrirmos está o relatório do Jacoco.

[05:56] É uma página bem feia, não tem CSS e não tem um visual bacana, mas para nós isso não importa muito. O que nos importa é o conteúdo. Ele lista todos os pacotes da aplicação, no caso a nossa aplicação só tem 1 pacote, o nível de cobertura se estiver bom ficaria verde. Está ruim, está vermelho, porque está com 0% de cobertura.

[06:15] Podemos detalhar. Quando você clica no pacote, ele te mostra todas as classes e em cada classe ele mostra a cobertura. Nós só temos uma classe e ele mostra aqui métodos, construtores e o percentual de cobertura. Está tudo zerado, não tem nada sendo testado.

[06:30] Vamos tentar escrever um teste só para mudarmos isso daí. Nós até temos o `ProdutoTest`, só que tem um teste de vazio que não faz nada, `@Test public void test () {}`.

[06:37] Vamos instanciar um produto: `Produto p = new Produto()`.Lá na classe `produto`, se dermos uma olhada em `produto.java` tem um atributo de nome, um atributo de preço, um construtor que recebe os dois atributos e um _getter_ para cada um dos dois atributos.

[06:51] Vou criar um produto `Produto p = new Produto(“teste”, BigDecimal.TEN)` e aí vou fazer um _assert_: `Assert.assertEquals(“teste”, p.getNome())`. É um teste não recomendado. Testar o método ‘get’ é algo bizarro. É só para vermos o relatório.

[07:24] Eu vou fazer um outro teste para ver se ele pega o preço aqui como sendo `(BigDecimal.TEN)`. Está dando um erro aqui. Foi o `Import`, não é desse pacote, é `assert` do "org Junit".

> Código em `ProdutoTest.Java`:

```java
package br.com.alura.loja;

import java.math.BigDecimal;

import org.junit.Test;

import org.junit.Test;

public class ProdutoTest {

        @Test
        public void test() {
             Produto p =  new Produto("teste", BigDecimal.TEN);
                         Assert.assertEqual("teste",p.getNome());
                         Assert.assertEqual(BigDecimal.TEN,p.getPreco());
        }
}
```

[07:38] É um teste bem meia boca, só para simular. Vamos rodar novamente no _prompt_, `mvn test`. Ele vai recompilar tudo, retestar o relatório geral. Se usar a tecla “F5” na tabela, olhe só que legal, agora já muda a figura!

[07:55] Vou mudar para “Home”. 100% de cobertura de teste. A barra verde dizendo que está boa a sua cobertura. Detalhou a classe produto. Tudo coberto, o construtor, os _getters_. É um _plugin_ para cobertura de testes.

[08:11] Essa é que é a ideia dos _plugins_. Existem vários _plugins_ na comunidade para relatório de testes - para modificar o _build_ do projeto, para executar um servidor, para gerar um PDF e para rodar SQL. Tem _plugins_ para tudo que você possa imaginar. Inclusive, você pode criar um _plugin_. Você pode criar um _plugin_ que vai fazer alguma coisa durante o _build_ de uma aplicação. É totalmente possível fazer isso!

[08:37] Essa é uma das vantagens do Maven. Ele é extensível, não é engessado, só tem aquelas funcionalidades “x”, “y”, “z” e acabou; você só pode usar aquilo. Ele te permite estendê-lo, adicionar _plugins_ para ter novos comportamentos e novas funcionalidades. Isso é algo extremamente importante em uma aplicação, essa capacidade de extensão para você adicionar novos comportamentos.