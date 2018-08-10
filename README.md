# Especificidade 
- O id é mais específico que uma classe que, por sua vez,  
é mais específica que um elemento 
  - Estilo inline 
    - Precedência máxima 
  - Id
    - Maior precedência após o estilo inline 
  - Classe, pseudo classe, atributo 
    - Maior precedência após o id 
  - Elemento, pseudo elemento 
    - Maior precedência após Classe, pseudo classe ou atributo 

# Herança 
- Elementos herdam estilos de seus containers 
- Se `body` tiver `color: red`, todos os textos dentro  
dele serão vermelhos, exceto se configurados com outro  
`color` 
- Nem todas as propriedades são herdadas. Margins e  
paddings são um exemplo 

## `inherit` 
- Valor que define que a propriedade será herdada de seu  
container 

Exemplo de propriedades herdadas do container (pai): 

```CSS
p {
  margin: inherit;
  padding: inherit;
}
```

# Resets 
- Reduzem a inconsistência de renderização de elementos  
entre browsers 
- Tende a deixar o código redundante, caso não seja avaliado  
quais propriedades são realmente necessárias 
  - Alguns resets, contém, por exemplo, elementos de correções  
  de bugs de browsers antigos como o IE6/7. Inútil caso a  
  aplicação não pretende dar suporte a estes navegadores
  - Font-size geralmente costuma ter que ser reescrito 

## [css reset](https://meyerweb.com/eric/tools/css/reset/)

## [normalize](https://necolas.github.io/normalize.css/)

# Text 

## `text-transform: uppercase;` 
- Transforma todas as letras do texto em maiúsculas 

## `text-transform: lowercase;` 
- Transforma todas as letras do texto em minúsculas 

## `text-transform: capitalize;` 
- Transforma todas as iniciais das palavras em maiúsculas 

# Unidades de medida 
- Unidades relativas, como em e rem, permitem que os  
elementos de um layout sejam escaláveis, pois se adaptam  
naturalmente

## `%`
- Corresponde ao valor do `width` do elemento pai 

## `em`
- Corresponde ao `font-size` do pai do elemento em questão 
- Caso algum elemento pai não tenha o `font-size` definido,  
corresponde ao valor de `font-size` do browser, que, por  
padrão, é em média 16px
- Favorece a usabilidade, por ser uma medida relativa 
- Fórmula para o cálculo de um em: `target / context = result`
  - target: valor do font-size do elemento 
  - context: valor do font-size do pai/container

### Truque de css para facilitar a conversão de px para em: 
- É possível ajustar o font size padrão do browser, para que  
12px passe a equivaler a 1.2em, por exemplo 

```css
body {
  font-size: 62.5%; /* fonte alterada pra 10px */
}
```

### `em` em margins e paddings 
- Quando usado em margins e paddings, corresponde ao  
font-size do próprio elemento em questão 
- Ao ser aplicado em um padding de uma div, por exemplo,  
o espaço interno da div será adaptado ao font-size dela 

## `rem`
- Root em
- Corresponde ao elemento `:root` do HTML 
- Foi criado para consertar o problema de escalabilidade dos  
elementos com `em`'s

### `rem` em margins, paddings e widths 
- Sempre consistente, sempre corresponde ao font-size do  
elemento root do HTML 
- [Caso o `font-size` do browser seja aumentado, o elemento  
com o width em rem será redimensionado proporcionalmente](https://youtu.be/UHf3aQz50jQ?t=3m38s)

### Combinando `em` e `rem` de forma atômica 
- Se o `font-size` de um botão estiver em `rem` e todas as outras  
unidades de medida deste botão estiverem em `em` (paddings,  
border, border-radius, etc), os componentes da estrutura deste botão 
estarão associados a ele mesmo 
- Resumindo: `rem` em text nodes e `em` em componentes anexados  
aos text nodes 

### Combinando margins e paddings com `em` e `rem` 
- Em botões, por exemplo, ao ajustar o `font-size` do botão,  
se o padding estiver com `em`, esse padding irá se ajustar  
automaticamente ao tamanho da fonte, ou seja,  
**as proporções são mantidas**
- Ainda em botões, caso a `margin` esteja setada em `rem`,  
haverá um espaço consistente em qualquer lugar em que os  
botões forem aplicados 

# `width`
- Especifica a largura do elemento 
- A largura default é o content-area

# Position 

## `position: static;`
- Posicionamento padrão
- Não altera o elemento caso seja retirado 
- O elemento é posicionado abaixo/após o elemento anterior,  
desde que este tenha display block 
- Não permite que a posição do elemento seja definida 

## `position: absolute;`
- Posiciona o elemento **em relação ao seu container**, caso  
o container tenha um position definido 
- Se o position do container **não for** diferente do static  
(padrão), posiciona o elemento considerando o browser 
- Tira o elemento do fluxo do documento 

## `position: relative;` 
- Posiciona o elemento **em relação a si mesmo** 
- Mesmo quando deslocado, o seu lugar no fluxo do documento  
é preservado 
- O ponto 0 é o canto superior esquerdo 

## `position: fixed;`
- Fixa o elemento e o posiciona em relação à janela do browser 

## `z-index`
- Só funciona se a propriedade position do elemento tiver um valor  
diferente de `static`
- Altera o eixo x do elemento 

# Display

## `display: block;`
- Ocupa 100% da largura da tela, por padrão 
- Aceita propriedades de largura e altura 
- Ocupa a linha inteira, não deixa outros elementos ocuparem  
a mesma linha que ele  

## `display: inline;`
- Permite que os elementos fiquem lado-a-lado 
- Não aceita largura ou altura 
- Ganha o comportamento de uma palavra, ou seja, existe um espaço  
de alguns pixels entre cada elemento (palavra)
- Esse comportamento de palavra só é retirado caso não haja quebra  
de linha nas tags do elemento, ou comentário entre elas (permitindo  
a quebra de linha)
- A propriedade `text-align` irá posicionar os elementos, caso  
seja especificada no container deles 

## `display: inline-block;`
- Junção dos comportamentos `inline` e `block`
- Coloca um elemento ao lado de outro 
- Considera altura e largura 
- Também ganha comportamento de uma palavra, como no inline 
- `text-align` também irá posicionar os elementos, caso seja  
especificada no container deles 

# Margin 

## `margin-left: auto;`
- Posiciona o elemento no canto direito da tela 

## `margin: 0 auto;`
- Posiciona o elemento no centro horizontal da tela

# Pseudo-elementos

## `:after`
- Sintaxe: `nomeTag:after`
- Cria um pseudo-elemento 
- Adiciona um elemento dentro da tag informada no seletor 
- O elemento que ele adiciona sempre será o último dentro da tag 
- O texto através da propriedade `content` deve ser apenas  
um atrativo visual

# Box model 

## `box-sizing`
- Propriedade usada para alterar a propriedade padrão da box  
model, usada para calcular larguras e alturas dos elementos 

## `border-box`
- Valor usado para que o padding e border de um elemento  
sejam considerados na altura e largura de um elemento 
- Desconsidera a propriedade `margin` 

# Prefixes / prefixos 
- Propriedades que ainda estão em testes nos navegadores  
precisam de prefixos 

Exemplos: 

- `-webkit-` (Chrome, Safari, versões mais recentes do Opera.)
- `-moz-` (Firefox)
- `-o-` (Versões antigas do Opera)
- `-ms-` (Internet Explorer)

## [Autoprefixer](http://autoprefixer.github.io/)
- Plugin do PostCSS que parseia o CSS e adiciona prefixos 
- Se baseia no [Can I use](https://caniuse.com)

# Transform 
- Propriedade que permite que um elemento seja manipulado  
visualmente, através de inclinação, rotação, traslado ou  
dimensionamento
- Não faz com que outros elementos flutuem ao seu redor,  
ou seja, os sobrepõe
- Aceita a especificação de multiplos valores, separados  
por um espaço 
- O valor que se encontra à frente será realizado antes  
do valor posterior 

`transform: valor1() valor2();`

## `transform-origin: value;`
- É uma propriedade usada em conjunto com o transform 
- Permite a mudança do ponto de origem de um transform 
- O default da origem de um transform é "50% 50%", ou seja,  
exatamente no centro do elemento
- Pode receber 2 valores separados por espaço, em caso  
de transformações 2d 
  - Em transformações 3d, recebe 3 valores 
- Os valores podem ser `top`, `left`, `right`, `bottom`  
e `center`
  - O primeiro valor é a posição horizontal
  - O segundo, a vertical
  - O terceiro, o eixo Z
    - Só funciona caso o elemento possua transforms 3d
    - Não pode ser uma porcentagem 

`transform-origin: bottom right;`

## 3D transform 
- A maioria das propriedades abaixo possuem sua versão 3d

## Scale 
### `transform: scale(xxTimes);` 
- Valor que faz com que o elemento seja redimensionado  
em relação ao número de vezes passado por parâmetro 
- Aplica-se às propriedades `font-size`, `padding`,  
`height`, e `width`
- É um atalho para `scaleX()` e `scaleY()`

```css
.my-div:hover {
  transform: scale(2); 
  /* no hover, faz com que o elemento tenha 2x suas dimensões originais */
}
```

### `transform: scale(x, y);`
- Parâmetro `x` estica o elemento horizontalmente 
- Parâmetro `y` estica o elemento verticalmente 

```css
.my-div:hover {
  transform: scale(4, .5);
  /* no hover, o elemento terá 4x sua largura e metade de sua altura */
}
```

### `transform: scaleX(xTimes)`
- Faz com que o elemento tenha x vezes sua largura original 

### `transform: scaleY(xTimes)`
- Faz com que o elemento tenha x vezes sua altura original 

### `transform: scale3d(sx, sy, sz)` / `scaleZ(value)`
- Afeta a escala ao longo do eixo Z, linha imaginária que  
sai da tela em direção ao usuário 

## Skew 
### `transform: skewX(xxdeg)` e `transform: skewY(xxdeg)`
- Inclina um elemento para a esquerda ou direita
- Ambas funções precisam ser usadas, pois não há atalho  
para este valor
- Pode, por exemplo, inclinar um quadrado para a esquerda,  
com o `skewX()`

```css
.my-div {
  width: 50px;
  height: 50px;
  background-color: red;
  margin: 50px auto 0;
  transform: skewX(-45deg);
}
```

![skewx](https://user-images.githubusercontent.com/29297788/43177327-26fcea5c-8f9e-11e8-8fab-88ce1d2cc4ae.png)

## Translate 
### `transform: translate(tx, ty)`, `transform: translateX(value)`, `transform: translateY(value)`
- Move o elemento lateralmente ou para cima e para baixo,  
à partir de seu canto superior esquerdo 
- Valores são especificados em unidades de medida padrão  
do css, negativos ou positivos 
- Valor x positivo move o elemento para a direita 
- Valor y positivo move o elemento para baixo 

### `transform: translate3d(x, y, z)` / `translateZ(value)`
- Move o elemento em direção ao usuário
  - Aceita valores negativos

## Rotate 
### `transform: rotate()`
- Rotaciona o elemento no sentido horário, à partir de sua  
posição atual 
  - Valores negativos rotacionam no sentido anti-horário

### `transform: rotateX()`
- Rotaciona o elemento em torno do eixo horizontal 

### `transform: rotateY()`
- Rotaciona o elemento em torno do eixo vertical  

### `transform: rotateZ()`
- Rotaciona o elemento em torno do eixo Z  

### `transform: perspective(value)`
- Não afeta o elemento em si, mas as propriedades `transform`  
3d dos elementos descendentes, permitindo que elas tenham uma  
profundidade consistente de perspectiva 

## Matrix 
### `transform: matrix()`
- Combina todas as transformações em uma 

## Perspective
### `transform: perspective()`
- Não afeta o próprio elemento, mas afeta os elementos com  
transforms com valores 3D, permitindo que todos eles tenham  
uma constante profundade de perspectiva 

# `box-shadow`
- Funde sombras em elementos do tipo block 
- Recebe 5 valores, separados por espaço 
  1. Horizontal offset
    - Positivo significa que a sombra estará à direita do  
    elemento 
    - Negativo, leva a sombra para o lado esquerdo 
  2. Vertical offset
    - Negativo traz a sombra para cima do elemento 
    - Positivo, para baixo 
  3. Blur radius 
    - Opcional
    - 0 faz com que a sombra seja não tenha desfoque 
    - Quanto maior o valor, mais desfocada será a sombra 
  4. Spread radius 
    - Opcional
    - Valores positivos aumentam o tamanho da sombra 
    - Negativos, diminuem 
    - 0 é o valor default, a sombra é do mesmo tamanho  
    do desfoque
  5. Color 

```css
div{
  box-shadow: 0 15px 20px -10px #b1b1b1;
}
```

![box-shadow](https://user-images.githubusercontent.com/29297788/43301406-3bee70d6-913b-11e8-8d3a-3c8398100606.jpg)

- Inner shadow 

```css
div {
  box-shadow: inset 0 0 10px black;
}
```

![inner-shadow](https://user-images.githubusercontent.com/29297788/43301509-0a63ca7e-913c-11e8-8992-f72e19fdf81c.jpg)

# `rgba()`
- Valor que recebe 4 parâmetros separados por vírgula 
- O 4º parâmetro indica o quanto a cor do elemento  
terá de opacidade 

```css
div {
  background-color: rgba(255, 0, 0, .1); /* 10% de opacidade */
}
```

![rgba](https://user-images.githubusercontent.com/29297788/43301759-74cec502-913d-11e8-85ba-3f7e05add444.jpg)

- Ao contrário da propriedade `opacity`, o rgba não  
afeta os elementos filhos 

![opacity-rgba](https://user-images.githubusercontent.com/29297788/43302032-b0785ffe-913e-11e8-8cd9-9f76ba65e866.jpg)

# `background`
- Propriedade que permite manipular o background de  
qualquer elemento 
- É uma propriedade de atalho, ou seja, permite que várias  
propriedades sejam escritas dentro dela 
- É composta de 8 propriedades separadas por espaço: 
  - background-image
  - background-position
  - background-size
  - background-repeat
  - background-attachment
  - background-origin
  - background-clip
  - background-color
- As propriedades podem ser combinadas na quantidade necessária,  
contudo, **a ordem de declaração é a referência acima**
- Tudo o que não é especificado na propriedade `background`  
é setado como default 
  - Se há uma instrução `background-color: red` em uma linha e,  
  abaixo dela, uma instrução `background: url(./texture.jpg)`, o  
  background do elemento será transparente 

```css
.my-div {
  background: 
    url(./img/my-img.jpg)    /* image */
    top center / 200px 200px /* position / size */
    no-repeat                /* repeat */
    fixed                    /* attachment */
    padding-box              /* origin */
    content-box              /* clip */
    red;                     /* color */
}
```

# Múltiplos backgrounds
- Empilha os backgrounds do elemento 
  - Possibilita uma camada de png acima de um gradiente,  
  por exemplo
- As propriedades relacionadas aos backgrounds são  
separadas por vírgula 
  - Cada valor na lista separada por vírgula corresponde  
  às respectivas camadas de background 
- Vale para múltiplos gradientes, separados por vírgula 

```css
.my-div {
  background: 
    url(./img/my-logo.png), 
    url(./img/my-second-png.png), 
    linear-gradient(ro right, rgba(30, 75, 115, 1), rgba(255, 255, 255, 0));
  background-repeat: no-repeat, no-repeat, no-repeat;
  background-position: bottom right, left; /* posicionou apenas as 2 camadas de imagens */
}
```

# `background-image(url, url)`
- Propriedade que aplica um gráfico (PNG, SVG, JPG, GIF, WEBP)  
ou gradiente ao background de um elemento 
  - Aplica-se a todos os elementos 
- Uso de imagens: `background-image: url(./image-path-here.extension);`
- Pode ser usada para fazer sprites de imagens 
  - Método que pode reduzir o número de requisições HTTP
- Especificar um background-color para ser usado se uma imagem não  
estiver disponível. Imagens de fundo são renderizadas sobre a cor  
de fundo
- Aceita múltiplas imagens e/ou degradês por parâmetro, separados  
por vírgula 
  - Comumente necessita de mais valores para que os backgrounds  
  se posicionem corretamente 
- `background-color` como fallback
  - Se um `background-image` ou gradiente não for carregado, 
  o browser irá procurar um background-color como fallback
    - Neste caso, o recomendado é especificar a imagem primeiro  
    e depois a cor de fallback

`background-color` como fallback:

```css
background: url(sweettexture.jpg) blue;
```

múltiplas imagens:

```css
body {
  background:
    url(logo.png) bottom center no-repeat,
    url(background-pattern.png) repeat;
}
```

# `linear-gradient(color, color)`
- Aceita duas ou mais cores por parâmetro, separadas por vírgula 
- Valores aceitos
  - `XXdeg` como primeiro parâmetro 
    - Inclina xx graus 
    - Sentido horário 
    - `to top` ou `0deg`
    - `to bottom` ou `180deg`
    - `to left` ou `270deg`
    - `to right` ou `90deg`
  - `<color-stop>`
    - O gradiente começa em XX% da linha do gradiente 
- Suportam transparências `rgba()`

```css
.my-div {
  background: linear-gradient(blue, #222);
}
```
![linear-gradient](https://user-images.githubusercontent.com/29297788/43361373-5a6fff02-92a3-11e8-82d2-58615e76abe2.png)

```css
.my-div {
  background: linear-gradient(45deg, red, blue);
}
```
![linear-gradient-with-deg](https://user-images.githubusercontent.com/29297788/43361407-5f7c5c1a-92a4-11e8-94b8-b3c33668bd08.png)

```css
.my-div {
  background: linear-gradient(135deg, orange, orange 60%, cyan);
}
```
![l-g-color-stop](https://user-images.githubusercontent.com/29297788/43361484-bca9d542-92a5-11e8-9f39-b4b25e82c2e7.png)

```css
.my-div {
  background: linear-gradient(to right, rgba(255,255,255,0), rgba(255,255,255,1)), url(http://foo.com/image.jpg);
}
```
![gradientes](https://user-images.githubusercontent.com/29297788/43361505-6276d5ce-92a6-11e8-90a9-0905d537c528.png)

# `radial-gradient(color, color)`
- Inicia em um único ponto e emana para fora 
- Comumente usados para simular iluminação 
  - Faz com que o gradiente pareça mais natural 
- O valor default faz com que a cor do primeiro parâmetro  
se inicie no centro e se desvaneça para a cor final em  
direção às bordas do elemento 
  - O desvanecimento acontece em um ritmo igual, não  
  importa em qual direção
- `circle closest-side` 
  - Ao contrário do parâmetro default (`ellipse`), faz  
  com que o desvanecimento termine como um espaço  
  separando o valor da forma 
- `circle at top right`
  - Posiciona o círculo no background 

```css
.my-div {
  background: radial-gradient(white, black);
}
```
![radiel-01](https://user-images.githubusercontent.com/29297788/43361558-ec102d0c-92a7-11e8-895b-6a2ea58f64f3.png)

```css
.my-div {
  background: radial-gradient(circle closest-side, white, black);
}
```
![radiel-02](https://user-images.githubusercontent.com/29297788/43361592-e7f3d4c0-92a8-11e8-87ea-98495b9024df.png)

```css
.my-div {
  background: radial-gradient(circle at bottom right, white, black);
}
```
![gr1](https://user-images.githubusercontent.com/29297788/43376355-b1696102-9390-11e8-909d-25d823b036b4.png)

# Gradientes cônicos 
![cg](https://user-images.githubusercontent.com/29297788/43376390-ee89575e-9390-11e8-9d1d-6fb793d1d600.png)
- Similar aos gradientes radiais, é circular e usa o centro do  
elemento como ponto de origem para as paradas de cores 
- Contudo, enquanto a parada de cor de um gradiente radial emerge  
do centro do círculo, o gradiente cônico insere as cores **ao redor**  
do círculo 
- Têm esse nome devido a parecer a forma de um cone visto por cima 
- [Ainda não suportado pelos browsers](https://caniuse.com/#feat=css-conic-gradients)

```css
.my-div {
  background: conic-gradient(#fff, #000);
}
```

# `repeating-linear-gradient()`
- O tamanho do gradiente é determinado pelo fim da cor final 
  - Se for 20px, o tamanho do gradiente, que se repete, será  
  20px x 20px quadrados 

```css
.my-div {
  background: repeating-linear-gradient(45deg, blue, yellow 10px, red 10px, red 20px);
}
```

![grad](https://user-images.githubusercontent.com/29297788/43497469-bb5b0a10-9518-11e8-9d89-e52a980201cf.png)

# `repeating-radial-gradient()`
- Segue a mesma lógica de repetição do gradiente linear 

```css
.my-div {
  background: repeating-radial-gradient(
    circle at 0 0, 
    #ccc, 
    white 50px
  );
}
```

![rg](https://user-images.githubusercontent.com/29297788/43497673-ba5821c4-9519-11e8-895e-bbe3cafb8879.png)

# `background-position: x y;`
- Seta a posição inicial de uma imagem ou gradiente, relativa  
ao `background-origin`
- Valores default posicionam a imagem no topo esquerdo do container 
- Possíveis valores: 
  - Palavras-chave `top` (0% y), `bottom` (100% y), `left` (0% x),  
  `right` (100% x), `center` (50% x e y)
  - Porcentagem `25%` `75%`
    - `50%` significa o alinhamento do meio da imagem com o meio  
    do container
    - `100%` significa o alinhamento do último pixel da imagem  
    com o último pixel do container
  - Múltiplas imagens `0` `0`, `center`
  - Considerando a borda `bottom 10px right 20px`
- Caso apenas um valor seja declarado, ele será o valor x e o  
browser irá setar o valor y como center
- Aceita até quatro valores, incluindo qualquer uma das  
palavras-chave, exceto `center`
  - `background-position: right 45px bottom;`
    - O background será posicionado à 45px da borda direita e  
    0px à parte inferior do container 
  - `background-position: right 10px bottom 20px;`
    - Posiciona o background à 10px à direita da borda e à 20px  
    da parte inferior do container 
  - Neste formato, a palavra-chave sempre deve preceder a  
  unidade de medida 

```css
.container {
  width: 700px;
  height: 700px;
  background: url(./img/pug.png) no-repeat #ffda8f ;
  background-position: 100% 100%;
}
```

![background-position](https://user-images.githubusercontent.com/29297788/43561348-0888febc-95ed-11e8-8d99-52702b80c0fb.png)

# `background-size`
- Propriedade que possui muitas variações e diferentes  
sintaxes, todas com diferentes casos de uso 
- Ao ser usada com o shothand `background`, vir após a  
propriedade `background-position`, que deve ser especificada
- Há 4 diferentes sintaxes possíveis para esta propriedade: 
  - keywords sintax 
    - Além do valor padrão, (auto), há 2 keywords possíveis 
      - `auto` calcula, automaticamente, a medida baseada no  
      tamanho atual da imagem e proporção 
        - Mantém a proporção da imagem inalterada (exemplo 3)
    - ![cover-and-contain](https://user-images.githubusercontent.com/29297788/43672257-94c5fa12-9780-11e8-864c-56429650d9fd.jpg)
    - `cover`
      - Diz ao browser que a imagem **sempre** irá cobrir todo  
      o container, mesmo que a imagem tenha que ser esticada  
      (proporcionalmente) ou ultrapasse os limites do container  
      (exemplo 1)
    - `contain`
      - **Sempre** mostra toda a imagem, proporcionalmente, mesmo  
      que deixe espaço em um dos lados ou em baixo (exemplo 2)
  - one-value sintax 
    - Configura a largura. A altura permanece `auto`
    - Qualquer unidade de medida CSS pode ser utilizada (exemplo 4)
  - two-values sintax (exemplo 5)
    - Valor 1: seta a largura da imagem
    - Valor 2: seta a altura da imagem
    - Qualquer unidade de medida pode ser utilizada
    - Pode distorcer a imagem 
  - multiple background sintax (exemplo 6)
    - Permite combinar qualquer um dos valores acima  
    e aplicá-los à multiplas imagens, apenas adicionando  
    vírgula entre cada sintaxe 

```css
.container {
  /* ... */
  background: url(img/t11.png) top / cover no-repeat;
}
```

![cover](https://user-images.githubusercontent.com/29297788/43672400-72635caa-9783-11e8-9cc7-ad15b2664486.png)

```css
.container {
  /* ... */
  background: url(img/t11.png) top / contain no-repeat;
}
```

![contain](https://user-images.githubusercontent.com/29297788/43672410-a75b3e28-9783-11e8-885c-46eb0cf02156.png)

```css
.container {
  /* ... */
  background: url(img/t11.png) top / auto no-repeat;
}
```

![auto](https://user-images.githubusercontent.com/29297788/43672442-52dd1dde-9784-11e8-9ca9-44e99371a6f6.png)

```css
.container {
  /* ... */
  background: url(img/t11.png) top left / 95% no-repeat;
}
```

![one-value-syntax](https://user-images.githubusercontent.com/29297788/43672463-c45da640-9784-11e8-8820-fd793390c4a6.png)

```css
.container {
  /* ... */
  background: url(img/t11.png) top / 95% 75% no-repeat; /* position / size */
}
```

![bg-size-two-values](https://user-images.githubusercontent.com/29297788/43672494-66aa9214-9785-11e8-8410-0a25014f5237.png)

```css
.container {
  background: 
    url(img/pug.png) top / contain no-repeat, /* position / size */
    url(img/t11.png) bottom / contain no-repeat /* position / size */
  ;
}
```
![multiple](https://user-images.githubusercontent.com/29297788/43672588-a12e6878-9787-11e8-8a08-b41864a25cdf.png)

# `background-repeat`
- Se uma propriedade `background-image` é especificada,  
`background-repeat` define se e como essa imagem será  
repetida (exemplo 1)
- Possíveis valores: 
  - `repeat`: ladrilha a imagem em ambas as direções,  
  x e y. É o valor default
  - `repeat-x`: repete a imagem horizontalmente
  - `repeat-y`: repete a imagem verticalmente
  - `no-repeat`: mostra a imagem apenas uma vez 
  - `space`: ladrilha a imagem em ambas as direções (x, y). 
  Nunca corta a imagem, a menos que uma única imagem seja  
  muito grande para encaixar. Se múltiplas imagens podem  
  ser encaixadas, elas serão espaçadas de forma com que  
  toquem as bordas (exemplo 2)
  - `round`: ladrilha a imagem em ambas as direções, nunca  
  corta a imagem, a menos que uma única imagem seja muito  
  grande para encaixar. Se múltiplas imagens podem ser  
  encaixadas e há espaço sobrando, esmaga ou estica as  
  imagens para que elas se encaixem no espaço (exemplo 3)
- Possibilita a passagem de 2 valores:  
`background-repeat: round space` (exemplo 4)

exemplo 1:

```css
.container {
  background: url(./img/pug.png);
  background-repeat: repeat-x;
}
```

![repeat-x](https://user-images.githubusercontent.com/29297788/43689089-5494df2a-98cb-11e8-9976-1b98a6e20034.png)

exemplo 2:

```css
.container {
  width: 1500px;
  height: 800px;
  background: url(./img/pug.png);
  background-repeat: space;
  background-color: red;
}
```

![space](https://user-images.githubusercontent.com/29297788/43689076-01a198bc-98cb-11e8-98cf-9403767918b2.png)

exemplo 3:

```css
.container {
  /* ... */
  background: url(./img/pug.png);
  background-repeat: round;
  background-color: red;
}
```

![round](https://user-images.githubusercontent.com/29297788/43689138-12538e6c-98cc-11e8-983e-87993902319f.png)

exemplo 4: 

![2values](https://user-images.githubusercontent.com/29297788/43689172-8b1567da-98cc-11e8-9e8f-992cb2265ddf.png)

# `background-atachment`
- Especifica como mover o background em relação ao viewport 
- Valores possíveis: 
  - `scroll`: valor default. O background acompanha o scroll.  
    - O background é fixo em relação ao próprio elemento, e  
    não rola com os conteúdos do background. É efetivamente  
    anexado à borda do elemento 
  - `fixed`: faz com que o background não role ao scrollar  
  a página

# `background-origin`
- Define onde o background será exibido: em todo o elemento,  
dentro da borda ou dentro do padding
- Valores possíveis: 
  - `border-box` - exemplo 1: o background é posicionado  
  relativo ao border-box
  - `content-box` - exemplo 2: o background é posicionado  
  relativo ao content-box
  - `padding-box` - exemplo 3: o background é posicionado  
  relativo ao padding-box
  - `inherit`
- Similar ao `background-clip`, mas redimensiona o background  
ao invés de cortá-lo 
- É ignorado caso o `background-attachment` possua o valor `fixed`

exemplo 1: 

```css
.container {
  height: 500px;
  width: 500px;
  border: 20px solid rgba(0,0,0, .3);
  background: url(./img/pug.png);
  background-repeat: no-repeat;
  background-origin: border-box;
}
```

![bb](https://user-images.githubusercontent.com/29297788/43809073-7a62be18-9a86-11e8-9c93-226e03d9ee2c.jpg)

exemplo 2: 

```css
.container {
  height: 500px;
  width: 500px;
  border: 20px solid rgba(0,0,0, .3);
  background: url(./img/pug.png);
  background-repeat: no-repeat;
  background-origin: content-box;
  background-color: red;
}
```

![cb](https://user-images.githubusercontent.com/29297788/43809143-e4d074f2-9a86-11e8-9a9b-ddd5f5d4b561.jpg)

exemplo 3: 

```css
.container {
  height: 500px;
  width: 500px;
  border: 30px solid rgba(0,0,0, .3);
  padding: 40px;
  background: url(./img/pug.png);
  background-repeat: no-repeat;
  background-origin: padding-box;
  background-color: red;
}
```

![pb](https://user-images.githubusercontent.com/29297788/43809256-a25fad80-9a87-11e8-9878-4e10aa0a2777.jpg)

# `background-clip`
- Define o quanto o fundo deve se estender dentro do elemento 
  - Valores: 
    - `border-box` - Valor padrão. Permite que o background se  
    estenda completamente ao longo do elemento, mesmo sob a borda  
    (exemplo 1)
    - `padding-box` - O background se estende apenas até o limite  
    da borda do elemento (exemplo 2)
    - `content-box` - O background se estende apenas no limite do  
    conteúdo. Não inclui o preenchimento nem a borda (exemplo 3)
    - `text` - O background é renderizado apenas no interior do  
    texto em primeiro plano (exemplo 4). 
      - No momento em que este texto foi escrito, ainda é uma api  
      experimental. Não deve ser usada no código em produção 

exemplo 1: 

```css
.container {
  height: 300px;
  width: 500px;
  border: 10px dashed rgba(0, 0, 0, .5);
  background-color: #05ffb0;
  background-clip: border-box;
}
```

![bb](https://user-images.githubusercontent.com/29297788/43936311-64252c0e-9c2e-11e8-8d4b-f717c1fe3cf0.png)

exemplo 2:

```css
.container {
  height: 300px;
  width: 500px;
  padding: 50px;
  border: 10px dashed rgba(0, 0, 0, .5);
  background-color: #05ffb0;
  background-clip: padding-box;
}
```

![pb](https://user-images.githubusercontent.com/29297788/43936462-f737cd1c-9c2e-11e8-8a57-fa35f20220b9.png)

exemplo 3: 

```css
.container {
  height: 300px;
  width: 500px;
  padding: 80px 40px;
  border: 10px dashed rgba(0, 0, 0, .5);
  background-color: #05ffb0;
  background-clip: content-box;
}
```

![cb](https://user-images.githubusercontent.com/29297788/43936601-9e3b2460-9c2f-11e8-8cd4-fa49b033ea02.png)

exemplo 4: 

```css
.container {
  width: 500px;
  background: linear-gradient(yellow, red);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
```

![gradient-in-text](https://user-images.githubusercontent.com/29297788/43936847-e8cb7682-9c30-11e8-8159-921ecfded425.png)