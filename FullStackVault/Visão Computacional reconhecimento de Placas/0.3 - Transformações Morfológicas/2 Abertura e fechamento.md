As duas próximas transformações morfológicas que veremos são chamadas de **abertura** e **fechamento** e dependem das transformações simples, como a erosão e a dilatação.

A abertura é feita através de uma erosão seguida de uma dilatação. Observe, por exemplo, a imagem a seguir.

![Letra "J" na cor branca em um fundo preto. Há diversos pontos brancos espalhados pelo fundo.](https://cdn1.gnarususercontent.com.br/1/1310269/c1bd0f66-3a65-4fce-b09c-01f56aa78a04.png)

Perceba que a imagem possui ruídos na cor branca. Sendo assim, será aplicado primeiro o processo de erosão, que expande os pixels pretos e, portanto, elimina os ruídos brancos. Em seguida, o processo de dilatação é responsável por expandir os pixels brancos, mas, como os ruídos dessa cor foram removidos, a região expandida seria a letra "J", de preenchimento branco, no entanto, devido ao processo de erosão, a espessura da letra se mantém a mesma.

![Letra "J" na cor branca em fundo preto.](https://cdn1.gnarususercontent.com.br/1/1310269/5a4003c9-926d-4740-9c5c-e5d829498ab8.png)

No processo de fechamento, ocorre o inverso: primeiro a dilatação seguida de erosão. Observe, a imagem a seguir e perceba que possui ruídos pretos.

![Letra "J" na cor branca em fundo preto. Dentro da letra há diversos pontos na cor preta.](https://cdn1.gnarususercontent.com.br/1/1310269/2990d099-ec46-40af-b145-846b28bc1a90.png)

A dilatação expandirá os pixels brancos que preencherão a letra, eliminando os ruídos pretos. Em seguida, é aplicada a erosão, que expande os pontos pretos e mantém a espessura da letra.

![Letra "J" na cor branca em fundo preto.](https://cdn1.gnarususercontent.com.br/1/1310269/8e86ab91-a092-44c4-98fd-a9c120e87d43.png)

Vamos aplicar esses processos à nossa placa!

Iniciaremos aplicando o processo de abertura. Para isso, criaremos uma variável `abertura`, que receberá a função `cv2.morphologyEx()`. Esta função receberá como parâmetros a imagem limiarizada por Otsu, `lim_otsu`; o tipo de transformação morfológica que estamos fazendo, `cv2.MORPH_OPEN`; e o kernel que configuramos na aula anterior, `kernel`. Por fim, adicione o parâmetro de visualização `cv2_imshow(abertura)`.

```makefile
abertura = cv2.morphologyEx(lim_otsu, cv2.MORPH_OPEN, kernel)
cv2_imshow(abertura)
```

Ao executar esta célula, ela deve nos retornar a seguinte imagem:

![Placa de carro na cor branca com os caracteres "PLR3D97" em letras garrafais pretas. No canto inferior esquerdo, a sigla "BR", também em preto. Há uma barra superior na cor preta onde é possível visualizar "BRASIL" na cor branca. Ao final desta barra, no canto direito, a bandeira do Brasil apresenta manchas que inviabilizam sua identificação.](https://cdn1.gnarususercontent.com.br/1/1310269/d6b90ad0-99f5-4b5b-beef-fd6cdc647e22.png)

Perceba que os ruídos foram removidos, mas, diferente da erosão, que expandiu muito os caracteres, tornando-os mais grosseiros, aqui as letras mantiveram suas espessuras originais.

Aplicaremos, agora, o processo de fechamento. Em uma variável `fechamento`, chamaremos a função `cv2.morphologyEx()` que receberá os parâmetros `lim_otsu`, `cv2.MORPH_CLOSE` e `kernel`. Por fim, chamamos o comando de visualização `cv2_imshow(fechamento)`.

```makefile
fechamento = cv2.morphologyEx(lim_otsu, cv2.MORPH_CLOSE, kernel)
cv2_imshow(fechamento)
```

Execute esta célula e observe a imagem que nos retorna:

![Placa de carro na cor branca com os caracteres "PLR3D97" em letras garrafais pretas e manchas brancas. A sigla "BR", no canto inferior esquerdo, dá lugar a uma pequena mancha preta. Há uma barra superior na cor preta onde é possível visualizar "BRASIL" na cor branca. Ao final desta barra, no canto direito, a bandeira do Brasil já não pode ser identificada, pois assumiu a forma de um quadrado branco com ruído preto.](https://cdn1.gnarususercontent.com.br/1/1310269/33d56a87-2ac8-4dcf-b59c-525f735b3197.png)

Perceba que esse procedimento não apresentou um resultado tão satisfatório, pois as manchas brancas expandiram-se e ocuparam mais espaços internos aos caracteres principais da placa.

A seguir, veremos as últimas transformações morfológicas aplicáveis às nossas imagens!