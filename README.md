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

## Section 6: Diving Deeper into Relative Positioning

- position: relative permite mover um elemento em relação à sua posição original, sem retirá-lo do fluxo de documentos.

- Usar top, left, right e bottom com relative apenas move o elemento dentro de sua área de layout, sem afetar outros elementos ao seu redor.

- Ao contrário de position: absolute ou position: fixed, o position: relative não retira o elemento do fluxo e não muda a posição de outros elementos na página.

- É importante lembrar que, ao mover um elemento de maneira extrema (como 300px), ele pode ultrapassar os limites do seu elemento pai, o que pode causar problemas de layout.

## Section 6: Working with "overflow" and Relative Positioning

Quando você aplica "position: relative" a um elemento, ele pode se mover para fora do seu container, dependendo dos valores de top, left, right e bottom.

Uma maneira de resolver esse problema é usando a propriedade "overflow: hidden" no elemento pai. Ao aplicar "overflow: hidden", qualquer conteúdo que ultrapasse os limites do pai será ocultado, o que impede o elemento de sair da área visível do container.

Mas quando o "overflow: hidden" é aplicado no body, o comportamento não ocorre como esperado.
Isso acontece devido ao comportamento padrão do CSS, onde, se você aplicar "overflow: hidden" ao elemento body, a declaração é "passada" para o elemento html, o que não afeta o layout do body da maneira que esperamos.

Para resolver esse problema, é necessário aplicar a propriedade overflow tanto ao elemento html quanto ao elemento body. Isso garante que o overflow seja ocultado corretamente, impedindo que o conteúdo ultrapasse os limites da página.

PS: Ao invés de "overflow: hidden"", você pode usar overflow: auto. Quando você usa "overflow: auto", o conteúdo que ultrapassar os limites do container exibirá uma barra de rolagem, permitindo ao usuário visualizar o conteúdo adicional. Esse comportamento é útil quando você não quer esconder o conteúdo, mas deseja dar ao usuário a possibilidade de rolar.

## Section 6: Useful Resourses & Links

- Positioning theory: https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning

- More about the "position" property: https://developer.mozilla.org/en-US/docs/Web/CSS/position

- The z-index: https://developer.mozilla.org/en-US/docs/Web/CSS/z-index

- The Stacking Context: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context

- The "sticky" value and current browser support: https://caniuse.com/#search=sticky