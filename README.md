# Resumo das aulas

## Section 3: Understanding the display property

- We cannot define a top and bottom margin on inline elements. That is why it is important to change the display when necessary.

- Changing an element that is inline to block is not always a good idea. Because a certain inline element is like that for a good reason. That is why we added the display property not to the anchor in this case, but to the <li> element ([see line 32 of main.css](https://github.com/Filipe-vilela-felix/css-complete-guide/blob/main/main.css#L32))

- Right after that, instead of adding <display: block>, we prefer to add <display: inline-block>. Because this way, there is a mix in the behavior of both (inline and block). As inline elements, these elements can be close to each other, but they still behave like block-level elements when it comes to defining top and bottom margins, among others.

## Section 3: Theory Time - Pseudo Classes & Pseudo Elements

- Pseudo Classes: defines the style of a special state of an element;

- Pseudo Element: defines the style of a specific part of an element;

An example of a pseudo element:

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

- What properties were used?
    color:
    background-color:
    display:
    padding:
    padding:
    border:
    margin:
    width:
    height:

- What was learned in this module?
    - Box model:
        Each element is treated as a box, no matter if it is an element, line or block, it is treated as a box. With the exception of inline elements;
    - Width and height:
        - px or % (or other units)
        - %
        - width e height
        - box-sizing, content-box (default) or border-box
    - Display property:
        We can change the behavior of block-level elements or inline elements;
    - Pseudo classes and elements:
        It is possible to style different states of an element or target different types of elements;

## Section 4: CSS Class Selectors vs ID Selectors

- CSS Class Selectors:
    These are reusable, we can add them to any HTML element that should have a certain style, allowing us to only mark and name things for styling purposes.
- CSS ID Selectors:
    To use the ID, there must be a special reason, and not because you just want to add a style. See: [here](index.html#intro).

## Section 4: Selecting the opposit with :not()

The :not() pseudo-class allows us to revert a given rule or exclude or delete a given selector.

Example:
```css
a:not(.active) {
    color: blue;
}
```

## Section 5: Understanding outlines

In some cases, it is possible to add a blue outline to an element when it receives focus at a given moment (either by clicking or navigating with the "Tab" key).

In this case, we can use the :focus pseudo-element, which is a state applied to elements when they are focused, such as when clicking a button or input field. And to remove or customize this outline, you can use the outline property.

Example :
```css
.button:focus {
    outline: none;
}
```

## Section 5: Adding "float" to aour packages

Float means that you can override the default positioning and tell the browser to push an element to the left or right of the page. In other words, you can take it out of the document flow, which is also why we don't use floats because we rarely want to do that.

Float is great for positioning an image in text and making sure the text flows around the image, but it's not so good for positioning block-level elements. We have better properties like flex box...

So what do you do if you want to position a block-level element using float without messing up the entire document?

A: You need to keep the space reserved and tell the other block-level elements that come after it that they shouldn't respect any previous float, through a little hack.

Well... yet another reason why we don't use float for positioning anymore.

To fix this, we add a div right after the element that contains the float in the CSS. And on it, we add the "clear:both" property.

Exemplo no HTML:
```html
<div class="clearfix"></div>
```
Exemplo no CSS
```css
.clearfix {
    clear:both;
}
```
This means that any elements that come after this element or an element with this class will not respect previous floats.

## Section 6: Understanding Position - The Theory

Block-level HTML elements, such as divs, normally follow the flow of the document. This means that they occupy the available space on the line and are displayed one after the other, one below the other. This is the default behavior, which is managed by the position property. By default, the property has the value static, which makes the elements follow this normal flow without changes.

However, in some cases, we may want to change the behavior of the elements and place them in different positions on the page. To do this, it is necessary to change the value of the position property to something other than static. There are four main values ​​for this: absolute, relative, fixed and sticky.

- absolute: Positions the element relative to its parent element with relative positioning (or to the root element, if no positioned parent is found).
- relative: Positions the element relative to its original position, moving it within the document flow.
= fixed: The element is positioned relative to the viewport, and remains fixed as the page scrolls.

- sticky: The element stays in one position when it reaches a certain scroll point, but it keeps moving until it reaches the top or bottom of the viewport.

Once you set the position property to something other than static, you can use the top, right, bottom, and left properties to adjust the position of the element. These properties tell you exactly where the element will be placed in relation to its new positioning context. For example, if I set top: 20px, this will move the element 20 pixels down from the starting position of its positioning context, whether it's the parent, the root element, or the viewport.

## Section 6: Diving Deeper into Relative Positioning

- position: relative allows you to move an element relative to its original position, without removing it from the document flow.

- Using top, left, right, and bottom with relative only moves the element within its layout area, without affecting other elements around it.

- Unlike position: absolute or position: fixed, position: relative does not remove the element from the flow and does not change the position of other elements on the page.

- It is important to remember that when moving an element to an extreme (such as 300px), it can exceed the bounds of its parent element, which can cause layout issues.

## Section 6: Working with "overflow" and Relative Positioning

When you apply "position: relative" to an element, it may move outside of its container, depending on the values ​​of top, left, right, and bottom.

One way to solve this problem is by using the "overflow: hidden" property on the parent element. When you apply "overflow: hidden", any content that extends beyond the parent's boundaries will be hidden, preventing the element from moving outside of the visible area of ​​the container.

However, when you apply "overflow: hidden" to the body, the behavior does not occur as expected.

This is due to the default behavior of CSS, where if you apply "overflow: hidden" to the body element, the declaration is "passed" to the html element, which does not affect the layout of the body in the way we expect.

To solve this problem, you need to apply the overflow property to both the html element and the body element. This ensures that the overflow is hidden correctly, preventing the content from extending beyond the page boundaries.

PS: Instead of "overflow: hidden", you can use overflow: auto. When you use "overflow: auto", content that overflows the container will display a scroll bar, allowing the user to view additional content. This behavior is useful when you don't want to hide the content, but want to give the user the ability to scroll.

## Section 6: Useful Resourses & Links

- Positioning theory: https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning

- More about the "position" property: https://developer.mozilla.org/en-US/docs/Web/CSS/position

- The z-index: https://developer.mozilla.org/en-US/docs/Web/CSS/z-index

- The Stacking Context: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context

- The "sticky" value and current browser support: https://caniuse.com/#search=sticky

## Section 7: Working with "background-position"

- background-position: 20px 30px -> Ao usar pixels, você está definindo a posição exata da imagem de fundo em relação ao contêiner. 20px é o deslocamento da borda esquerda (eixo X) e 30px é o deslocamento da borda superior (eixo Y) do contêiner.

- background-position: 10% 20% -> Ao usar porcentagens, você está dizendo quanto da imagem deve ser "deslocado" dentro do contêiner. Se a imagem for maior que o contêiner, a imagem 
será "recortada" (cortada) a partir da borda oposta.

    O que acontece: 10% refere-se à posição horizontal e 20% refere-se à posição vertical. Ou seja, 10% da largura da imagem será "deslocada" para a direita, e 20% da altura da imagem será "deslocada" para baixo. Isso pode fazer a imagem "subir" ou "mover-se" dependendo da proporção.

- background-position: left 10% bottom 20% -> Quando usamos palavras-chave como left, right, top e bottom, estamos alinhando a imagem de fundo de forma mais direta em relação às bordas do contêiner. O valor 10% no eixo X vai deslocar a imagem 10% do seu contêiner da borda esquerda (ao invés de um valor absoluto como pixels), e o valor 20% no eixo Y vai deslocar a imagem 20% para cima a partir da borda inferior.