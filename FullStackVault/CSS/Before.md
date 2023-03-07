# ::before
## [Sumário](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#sumário "Permalink to Sumário")
[[CSS]]
`::before` cria um [pseudo-elemento](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) que é o primeiro filho do elemento atingido. É frequentemente utilizado para adicionar conteúdo decorativo à um element utilizando a propriedade [`content`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/content). Este elemento é inline por padrão.

## [Sintaxe](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#sintaxe "Permalink to Sintaxe")

/* CSS3 syntax */
::before

A notação `::before` (com dois dois-pontos) foi introduzida no CSS3 afim de diferenciar [pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) de [pseudo-elementos](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements). Navegadores também aceitam a notação `:before` introduzida no CSS 2.

## [Exemplos](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#exemplos "Permalink to Exemplos")

### [Adicionando aspas](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#adicionando_aspas "Permalink to Adicionando aspas")

Um exemplo simples do uso de pseudo-elementos `::before` pseudo-elementos é a exibição de aspas. Aqui usamos `::before e` ``[`::after`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::after)`` para inserir caracteres de aspas.

#### Conteúdo HTML

```
<q>Algumas citações</q>, ele disse, <q>são melhor do que nenhuma.</q>
```

#### Conteúdo CSS

```
q::before {
  content: "«";
  color: blue;
}
q::after {
  content: "»";
  color: red;
}
```

#### Saída

### [Exemplo decorativo](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#exemplo_decorativo "Permalink to Exemplo decorativo")

Podemos estilizar textos e imagens na propriedade [`content`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/content) praticamente da forma que desejarmos.

#### Conteúdo HTML

```
<span class="ribbon">Observe onde a caixa laranja está.</span>
```

#### Conteúdo CSS

```
.ribbon {
  background-color: #5BC8F7;
}

.ribbon::before {
  content: "Olhe para esta caixa laranja.";
  background-color: #FFBA10;
  border-color: black;
  border-style: dotted;
}
```

### [Lista To-do](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#lista_to-do "Permalink to Lista To-do")

Neste exemplo vamos criar uma simples lista de tarefas, usando pseudo-elementos. Este método pode frequentemente ser utilizado para dar pequenos toques à UI (User Interface) e melhorar a experiência do usuário.

#### Conteúdo HTML

```
<ul>
  <li>Comprar Leite</li>
  <li>Levar o cachorro para passear</li>
  <li>Exercitar-se</li>
  <li>Escrever codigo</li>
  <li>Tocar musica</li>
  <li>Relaxar</li>
</ul>
```

#### Conteúdo CSS

```
li {
  list-style-type: none;
  position: relative;
  margin: 2px;
  padding: 0.5em 0.5em 0.5em 2em;
  background: lightgrey;
  font-family: sans-serif;
}

li.done {
  background: #CCFF99;
}

li.done::before {
  content: '';
  position: absolute;
  border-color: #009933;
  border-style: solid;
  border-width: 0 0.3em 0.25em 0;
  height: 1em;
  top: 1.3em;
  left: 0.6em;
  margin-top: -1em;
  transform: rotate(45deg);
  width: 0.5em;
}
```

#### Conteúdo JavaScript

```
var list = document.querySelector('ul');
list.addEventListener('click', function(ev) {
  if( ev.target.tagName === 'LI') {
     ev.target.classList.toggle('done');
  }
}, false);
```

Aqui está rodando o código acima. Perceba que nenhum ícone é utilizado e o check-mark é o `::before` que foi estilizado no CSS

## [Notas](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::before#notas "Permalink to Notas")

Embora as correções posicionadas e fixadas no Firefox 3.5 não permitam que o conteúdo seja gerado como um irmão anterior ao elemento (conforme a especificação para o CSS indicam "Os Pseudo-elementos :before e :after interagem com outros elementos como se fosse elementos reais inseridos dentro do elemento associado."), eles podem ser usados para proporcionar uma ligeira melhora em layouts sem tables (por exemplo, para alcançar a centralização), a medida que o conteúdo a ser centrado está envolvido com um elemento filho adicional, uma coluna antes e depois do conteúdo pode ser introduzida sem adicionar elementos filhos reais (isto é, talvez mais semanticamente correto para adicionar uma pequena distância, do que seria adicionar um div vazio antes e / ou depois). (E sempre lembre-se de adicionar uma largura a um flutuador, pois, de outra forma, não flutuará!)

#### HTML content

```
<div class="example">
<span id="floatme">"Floated Before" should be generated on the left of the
viewport and not allow overflow in this line to flow under it. Likewise
should "Floated After" appear on the right of the viewport and not allow this
line to flow under it.</span>
</div>
```

#### CSS content

```
#floatme { float: left; width: 50%; }

/* To get an empty column, just indicate a hex code for a non-breaking space: \a0 as the content (use \0000a0 when following such a space with other characters) */
.example::before {
  content: "Floated Before";
  float: left;
  width: 25%
}
.example::after {
  content: "Floated After";
  float: right;
  width:25%
}

/* For styling */
.example::before, .example::after, .first {
  background: yellow;
  color: red;
}
```