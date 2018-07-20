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
- Se o position do container não for diferente do static (padrão),  
posiciona o elemento considerando o browser 
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