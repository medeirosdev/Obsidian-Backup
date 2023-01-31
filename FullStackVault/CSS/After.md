# ::after 
[[CSS]]

Em CSS, **`::after`** cria um [pseudo-elemento](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Pseudo-elements) que é o último filho do elemento selecionado. Muitas vezes é usado para adicionar e melhorar o conteúdo de um elemento como a propriedade [`content`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/content). É inline por padrão.

```
/* Adiciona uma seta após os links */
a::after {
  content: "→";
}
```

## [Sintaxe](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::after#sintaxe "Permalink to Sintaxe")

/* CSS3 syntax */
::after

### [Uso simples](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::after#uso_simples "Permalink to Uso simples")

Vamos criar duas classes: uma para parágrafos tediosos e uma para parágrafos excitantes. Podemos então marcar cada parágrafo adicionando um pseudo-elemento ao final dele.

```
<p class="boring-text">Here is some plain old boring text.</p>
<p>Here is some normal text that is neither boring nor exciting.</p>
<p class="exciting-text">Contributing to MDN is easy and fun.
Just hit the edit button to add new live samples, or improve existing samples.</p>
```

```
.exciting-text::after {
  content: "<- now this *is* exciting!";
  color: green;
}

.boring-text::after {
   content: "<- BORING!";
   color: red;
}
```

### [Exemplos decorativos](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::after#exemplos_decorativos "Permalink to Exemplos decorativos")

Podemos estilizar textos ou imagens na propriedade [`content`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/content) praticamente de qualquer forma que quisermos.

```
<span class="ribbon">Observe onde a caixa de laranja está.</span>
```

```
.ribbon {
  background-color: #5BC8F7;
}

.ribbon::after {
  content: "Observe esta caixa laranja";
  background-color: #FFBA10;
  border-color: black;
  border-style: dotted;
}
```

### [Dicas](https://developer.mozilla.org/pt-BR/docs/Web/CSS/::after#dicas "Permalink to Dicas")

O exemplo a seguir mostra o uso do `::after` [pseudo-elemento](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Pseudo-elements) em conjunto com a expressão CSS [`attr()`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/attr) e um [atributo data personalizado](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Global_attributes#attr-dataset) `data-descr` para criar uma _dica_ em forma de glossário feito em CSS puro. Verifique a visualização abaixo, ou veja este exemplo em [página separada.](https://developer.mozilla.org/files/4591/css-only_tooltips.html)

```
<p>Aqui está o exemplo ao vivo do código acima.<br />
  Temos um pouco de <span data-descr="collection of words and punctuation">texto</span> aqui com algumas
  <span data-descr="small popups which also hide again">dicas</span>.<br />
  Não seja tímido, passe o mouse por cima para dar uma <span data-descr="not to be taken literally">olhada</span>.
</p>
```

```
span[data-descr] {
  position: relative;
  text-decoration: underline;
  color: #00F;
  cursor: help;
}

span[data-descr]:hover::after {
  content: attr(data-descr);
  position: absolute;
  left: 0;
  top: 24px;
  min-width: 200px;
  border: 1px #aaaaaa solid;
  border-radius: 10px;
  background-color: #ffffcc;
  padding: 12px;
  color: #000000;
  font-size: 14px;
  z-index: 1;
}
```