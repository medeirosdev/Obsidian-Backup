[[JS]]
## [Resumo](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects#summary "Permalink to Resumo")

Este capítulo documenta todos os objetos nativos do JavaScript padrão, assim como seus métodos e propriedades.

O termo "objetos globais" (ou objetos nativos por padrão) aqui não deve ser confundido com o de **objeto global**. Aqui, objetos globais se referem aos **objetos no escopo global** (somente se o modo estrito/_strict mode_ do ECMAScript 5 não for usado; Nesse caso retorna [`undefined`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/undefined)). O **objeto global** pode ser acessado usando o operador [`this`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/this) no escopo global. De fato, o escopo global **consiste em** propriedades do objeto global, incluindo propriedades herdadas, se houver.

Outros objetos no escopo global também são [criados pelo desenvolvedor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Creating_new_objects) ou fornecido pela aplicação _host_. Os objetos disponíveis no _host_ no contexto do browser são documentados na [API reference](https://developer.mozilla.org/en-US/docs/Web/API/Reference). Para maiores informações sobre as distinções entre [DOM](https://developer.mozilla.org/en-US/docs/DOM/DOM_Reference) e core [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript), veja [visão geral das tecnologias JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/JavaScript_technologies_overview).

## Objetos padrão (por categoria)

### Propriedades de valor

Propriedades globais retornam um valor simples; eles não tem propriedades ou métodos.

-   [`Infinity`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Infinity)
-   [`NaN`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/NaN)
-   [`undefined`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/undefined)
-   [`null`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/null) literal

### Propriedades de função

Estas funções globais —funções que são chamadas globalmente ao invés de em um objeto—retornam diretamente seus resultados a quem chama.

-   [`eval()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/eval)
-   [`uneval()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/uneval) Non-Standard
-   [`isFinite()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/isFinite)
-   [`isNaN()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/isNaN)
-   [`parseFloat()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)
-   [`parseInt()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
-   [`decodeURI()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/decodeURI)
-   [`decodeURIComponent()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/decodeURIComponent)
-   [`encodeURI()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)
-   [`encodeURIComponent()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)
-   [`escape()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/escape) Deprecated
-   [`unescape()`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/unescape) Deprecated

### Objetos fundamentais

Estes são objetos básicos e fundamentais nos quais todos os outros objetos são baseados. Isso inclui objetos que representam objetos genéricos, funções e erros.

-   [`Object`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object)
-   [`Function`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function)
-   [`Boolean`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
-   [`Symbol`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Symbol) Experimental
-   [`Error`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Error)
-   [`EvalError`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/EvalError)
-   [`InternalError`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/InternalError)
-   [`RangeError` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError "Currently only available in English (US)")
-   [`ReferenceError`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError)
-   `StopIteration`
-   [`SyntaxError` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SyntaxError "Currently only available in English (US)")
-   [`TypeError`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
-   [`URIError` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/URIError "Currently only available in English (US)")

### Números e datas

Estes são objetos base para a representação de números, datas e cálculos matemáticos.

-   [`Number`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Number)
-   [`Math`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Math)
-   [`Date`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date)

### Processamento de texto

Estes objetos representam strings e manipulam as mesmas.

-   [`String`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/String)
-   [`RegExp`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

### Coleções indexadas

Estes objetos representam coleções de dados que são ordenados pelo valor de um índice. Isso inclui arrays (tipados) e arrays baseados em outros construtores, como `[]`.

-   [`Array`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
-   `[Float32Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Float32Array "JavaScript_typed_arrays/Float32Array")`
-   `[Float64Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Float64Array "JavaScript_typed_arrays/Float64Array")`
-   `[Int16Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Int16Array "JavaScript_typed_arrays/Int16Array")`
-   `[Int32Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Int32Array "JavaScript_typed_arrays/Int32Array")`
-   `[Int8Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Int8Array "JavaScript_typed_arrays/Int8Array")`
-   `[Uint16Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Uint16Array "JavaScript_typed_arrays/int16Array")`
-   `[Uint32Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Uint32Array "JavaScript_typed_arrays/Uint32Array")`
-   `[Uint8Array](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Uint8Array "JavaScript_typed_arrays/int8Array")`
-   `[Uint8ClampedArray](https://developer.mozilla.org/en-US/docs/JavaScript_typed_arrays/Uint8ClampedArray "JavaScript_typed_arrays/Uint8ClampedArray")`
-   `ParallelArray` Non-Standard

### Coleções chaveadas

Estes objetos representam coleções que usam chaves; estas contém elementos que são iteráveis na ordem de inserção.

-   [`Map`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Map) Experimental
-   [`Set`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Set) Experimental
-   [`WeakMap`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/WeakMap) Experimental
-   [`WeakSet`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) Experimental

### Dados estruturados

Estes objetos representam e interagem com buffers de dados estruturados e dados codificados usando JavaScript Object Notation (JSON).

-   [`ArrayBuffer`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)
-   [`DataView`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/DataView)
-   [`JSON`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON)

### Controle de abstrações de objetos

-   [`Promise`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Promise) Experimental
-   [`Generator`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Generator) Experimental
-   `GeneratorFunction` Experimental

### Reflexão (reflection)

-   [`Reflect`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Reflect) Experimental
-   [`Proxy`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Proxy) Experimental

### Internacionalização

Adições ao core do ECMAScript para funcionalidades sensíveis à linguagem.

-   [`Intl`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Intl)
-   [`Intl.Collator` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/Collator "Currently only available in English (US)")
-   [`Intl.DateTimeFormat` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat "Currently only available in English (US)")
-   [`Intl.NumberFormat`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat)