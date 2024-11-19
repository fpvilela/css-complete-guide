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

- background-position: 20px 30px -> When using pixels, you are defining the exact position of the background image relative to the container. 20px is the offset from the left edge (X axis) and 30px is the offset from the top edge (Y axis) of the container.

- background-position: 10% 20% -> When using percentages, you are saying how much of the image should be "offset" within the container. If the image is larger than the container, the image will be "cropped" (cut off) from the opposite edge.

    What happens: 10% refers to the horizontal position and 20% refers to the vertical position. In other words, 10% of the width of the image will be "offset" to the right, and 20% of the height of the image will be "offset" downwards. This can make the image "go up" or "move" depending on the aspect ratio.

- background-position: left 10% bottom 20% -> When we use keywords like left, right, top, and bottom, we are aligning the background image more directly with the edges of the container. A value of 10% on the X axis will offset the image of its container 10% from the left edge (rather than an absolute value like pixels), and a value of 20% on the Y axis will offset the image 20% up from the bottom edge.

## Section 7: The "background" shorthand - theory

1) Background image (```background-image```)

2) Background color (```background-color```)

3) Background position (```background-position```)

4) Background size (```background-size```):
    - cover: The background image adjusts to cover the entire container area, and can be cropped.
    - contain: The image is resized to fit completely inside the container.

5) Bckground repeat (```background-repeat```):
    - no-repeat: The image will not be repeated.
    - repeat: The image will be repeated horizontally and vertically.
    - repeat-x: Repeat only in the horizontal direction.
    - repeat-y: Repeat only in the vertical direction.

6) Bckground origin (```background-origin```):

    Define a área dentro do contêiner onde a imagem de fundo é posicionada, podendo ser ```padding-box```, ```border-box``` ou ```content-box```.

7) Bckground clip (```background-clip```):

    Controla se o plano de fundo deve se estender abaixo de bordas de elementos (como bordas pontilhadas ou tracejadas).

8) Background attachment (```backgroun-attachment```):

    Defines how the background image behaves when the user scrolls the page. It can be fixed or scroll along with the content.
    
    - fixed: The background image will remain fixed while the content scrolls.
    - scroll: The background image will scroll along with the content.

## Section 7: Using the "bakcground" shorthands on our project

The background property is a shorthand way of setting multiple background subproperties in a single line. It can include the background image, position, size, repeat, source, and clip.

A sintaxe para a propriedade background é como segue:
```
background: [imagem] [posição] [tamanho] [repetição] [origem] [clip];
```
- Image: The URL of the background image.
- Position: How the image should be positioned (can use values ​​such as pixels or percentages).
- Size: Sets the size of the image (e.g. cover or contain).
Repeat: Whether the background image should repeat or not (e.g. no-repeat).
- Origin: Where the image starts to be positioned (e.g. border-box or padding-box).

When you use the / slash, it separates the position and size properties of the image:
```css
background: [imagem] [posição] / [tamanho];
```

## Section 7: Styling images]

In order for an image to be contained within the "a" (anchor) tag, it must be converted into a block element to respect its original dimensions.

With normal images, the positioning and sizing options are more limited compared to background images.

For more precise image positioning or to create more advanced effects, the use of background images is recommended, although background images are not part of the normal flow of the document, which can harm accessibility.

## Section 7: Working on the Image Layout

When we place an image inside a container, the image, being an inline element (i.e. an element that flows with the text, as if it were part of the text), may leave some space below it. This extra space occurs due to the typical behavior of an inline element, which includes the "placeholder" for the text baseline (as if the image were a letter).

There are two solutions for this:

- Use vertical-align: top:

    O vertical-align controla o alinhamento vertical de um elemento inline em relação a outros elementos. Usando top, a imagem será alinhada no topo da linha, o que pode remover o espaço extra abaixo dela.

- Change the image display to block:

    Setting the image to display: block would make the image behave like a block element, i.e. the image will occupy the entire available width, pushing the other elements down (without the inline behavior).
    This would also remove the white space below the image because, by becoming a block element, the image will no longer be aligned with the text line and, therefore, does not leave this extra space.

See the example in CSS:
```CSS
.testimonial__image {
    width: 100%;
    vertical-align: top; /*or display: block */
  }
```

## Section 7: Understanding Linear Grandients

Gradients are treated as images in CSS. This means you can use gradients as a background, just like you would an image.

The linear-gradient() function can have multiple arguments, but the first one is always the direction of the gradient.

- Gradient direction:
    - Keywords such as to top, to bottom, to left, to right (e.g., to bottom indicates that the gradient goes from top to bottom).
    - Angles in degrees, such as 30deg for a slanted gradient. An angle of 0deg goes from bottom to top, while 180deg goes from top to bottom.

- You can add multiple colors to a gradient, and they will transition smoothly between each other.

- Gradients can also involve transparency using the rgba() function.

- You can control where each color starts and ends within the gradient by adjusting the percentage or position of each color.

## Section 7: Appling Radial Gradients

The radial gradient function creates a gradient that starts from a center point and spreads outward, rather than going from one edge to the other like linear gradients.

A simple radial gradient can have two colors. By default, the gradient is circular and centered, with the color transition starting in the center and spreading out to the edges.

- Gradient Shape:

    The default is ellipse (not circle), but you can set the gradient shape to circle by changing the first value in the radial-gradient() function.

    For example: circle results in a circular gradient, while ellipse results in an elliptical shape.

- Gradient Position:

    The gradient origin point can be positioned using keywords such as top, bottom, left, right.

    You can also use custom values ​​such as 20% 50% to specify the position on the X and Y axis.

- Gradient Size:

    The size of the gradient can be controlled, for example, by adding a value of 20px after the shape (circle or ellipse). This value defines the diameter of the gradient.

    For the ellipse, you can specify width and height as two values ​​separated by spaces.

- Palavras-chave de Tamanho:

    Você também pode usar palavras-chave como "closest-side" (para o lado mais próximo) e "farthest-side" (para o lado mais distante) para ajustar o tamanho do gradiente, ajustando até onde ele se estende.

- Paradas de Cor:

    Assim como no gradiente linear, você pode definir paradas de cor no gradiente radial. Por exemplo, você pode especificar que a transição entre cores deve ocorrer em 70% da área do gradiente.

Example:
```CSS
background-image: radial-gradient(ellipse farthest-corner at 20% 50%, red, blue, green);
```