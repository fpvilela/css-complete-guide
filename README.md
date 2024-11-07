# Resumo das aulas

## Section 3: Understanding the display property

- Não podemos deifinir uma margem superior e inferior nos elementos in-line. Motivo pelo qual é importante alterarmos o display quando necessaŕio.

- Mudar um elemento que é in-line para block nem sempre é muito bom. Pq um determinado elemento in-line é assim por uma boa razão. Motivo pelo qual adicionamos a propriedade display não na âncora neste caso, mas sim no elemento <li> ([ver linha 32 do main.css](https://github.com/Filipe-vilela-felix/css-complete-guide/blob/main/main.css#L32))

- Logo em seguida, ao invés de adicionarmos o <display: block>, preferimos adicionar o <display: inline-block>. Pois assim, há uma mistura no comportamento de ambos (in-line e block). Como elemento inline, esses elementos podem ficar próximos uns dos outros, mas ainda se comportam com elementos de nível de bloco quando se trata em definir margens superior e inferior, dentre outros

## Section 3: Theory Time - Pseudo Classes & Pseudo Elements

- Pseudo Classes: define o estilo de um estado especial de um elemento;

- Pseudo Element: define o estilo de uma parte específica de um elemento;

Um exemplo de pseudo element:

```css
.main-nav__item a::after {
    content: " (Link)";
    color: red;
}
```
## Section 3: Properties Worth to Remember & wrap up

```
selector {
    property: value;
}
```

- Quais propriedades foram usadas?
    color:
    background-color:
    display:
    padding:
    padding:
    border:
    margin:
    width:
    height:

- O que foi aprendido neste módulo?
    - Modelo de caixa: 
        Cada elemento é tratado como uma caixa, não importa se é elemento, linha ou bloco, é tratado como uma caixa. Com excessão dos elementos inline;
    - Largura e altura:
        - px ou % (ou outras unidades)
        - %
        - width e height
        - box-sizing, content-box (padrão) ou border-box
    - Propriedade display:
        Podemos alterar o comportamento de elementos de nível de bloco ou elementos em linha;
    - Pseudo classes e elementos:
        É possível estilizar diferentes estdados de um elemento ou segmentar diferentes tipos de elementos;

## Section 4: CSS Class Selectors vs ID Selectors

- CSS Class Selectors:
    São reutilizaveis, podemos adiciona-las a qualquer elemento HTML que deve ter um determinado estilo, nos permitindo apenas marcar e nomear as coisas apenas para fim de estilo.
- CSS ID Selectors:
    Para usa o ID, deve haver um motivo especial, e não porque deseja apenas adicionar um estilo. Veja: [aqui](index.html#intro).

## Section 4: Selecting the opposit with :not()

A pseudo-classe :not() nos permite reverter uma determinada regra ou excluir ou excluir determinado selector.

Exemplo:
```
a:not(.active) {
    color: blue;
}
```

## Section 5: Understanding outlines

Em alguns caso, é possível que um contorno azul seja adicionado à um elemento quando o mesmo recebe um foco em determinado momento. (seja ao clicar ou navegar com a tecla "Tab").

Neste caso, podemos usar o pseudo elemento :focus, que é um estado aplicado aos elementos quando eles são focados, como ao clicar em um botão ou campo de entrada. E para remover ou customizar esse contorno, você pode usar a propriedade outline.

Exemplo:
```
.button:focus {
    outline: none;
}
```

## Section 5: Adding "float" to aour packages

Float significa que você pode sobrescrever o posicionamento padrão e diz ao navegador para empurrar um elemento para a esquerda ou para a direita da página. Ou seja, podemos tira-lo do fluxo de documentos, é também por isso que não estamos usando floats porque raramente queremos isso.

O float é ótimo para posicionar uma imagem em texto e garantir que o texto flua pela imagem, mas não é tão bom para posicionar elementos em nível de bloco. Temos proriedade melhores como flex box...

Então o que fazer se quisermos posicionar um elemento de nível de bloco usando o float sem prejucar todo o documento?
R: Precisamos manter o espaço reservado e dizer aos outros elementos de nível de bloco que vêm depois, que eles não devem respeitar nenhuma flutuação anterior, através de um pequeno hack.

Bom...mais um motivo pelo qual não usamos o float para posicionar mais.

Para concertar isto, adicionamos uma div logo após o elemento que contém o float no CSS. E nele, adicionamos a propriedade "clear:both".

Exemplo no HTML:
```
<div class="clearfix"></div>
```
Exemplo no CSS
```
.clearfix {
    clear:both;
}
```
Isso significa que quaisquer elementos que vierem depois desse elemento ou de um elemento com essa classe, não respeitarão floats anteriores.

## Section 6: Understanding Position - The Theory

Os elementos HTML de nível de bloco, como as "div", normalmente seguem o fluxo do documento. Isso significa que eles ocupam o espaço disponível na linha e são exibidos um após o outro, um abaixo do outro. Esse é o comportamento padrão, que é gerenciado pela propriedade position. Por padrão, a propriedade tem o valor static, o que faz com que os elementos sigam esse fluxo normal sem alterações.

No entanto, em alguns casos, a gente pode querer mudar o comportamento dos elementos e colocar eles em posições diferentes na página. Para isso, é necessário mudar o valor da propriedade position para algo diferente de static. Existem quatro valores principais para isso: absolute, relative, fixed e sticky.

- absolute: Posiciona o elemento em relação ao seu elemento pai com posicionamento relativo (ou ao elemento raiz, se nenhum pai posicionado for encontrado).
- relative: Posiciona o elemento em relação à sua posição original, movendo-o dentro do fluxo de documentos.
= fixed: O elemento é posicionado em relação à janela de visualização (viewport), e permanece fixo durante o rolar da página.
- sticky: O elemento fica fixo em uma posição quando atinge um determinado ponto de rolagem, mas continua se movendo até atingir a parte superior ou inferior da viewport.

Depois de definir a propriedade position para algo diferente de static, a gente pode usar as propriedades top, right, bottom e left para ajustar a posição do elemento. Essas propriedades dizem onde exatamente o elemento vai ser colocado em relação ao seu novo contexto de posicionamento. Por exemplo, se eu definir top: 20px, isso vai mover o elemento 20 pixels para baixo, a partir da posição inicial do seu contexto de posicionamento, seja ele o pai, o elemento raiz ou a viewport.