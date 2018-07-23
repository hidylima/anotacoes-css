# Especificidade 
- O id é mais específico que uma classe que, por sua vez,  
é mais específica que um elemento 

## Estilo inline 
- Precedência máxima 

## Id
- Maior precedência após o estilo inline 

## Classe, pseudo classe, atributo 
- Maior precedência após o id 

## Elemento, pseudo elemento 
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