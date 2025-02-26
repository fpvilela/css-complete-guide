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
- fixed: The element is positioned relative to the viewport, and remains fixed as the page scrolls.

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
## Section 7: Useful Resources & Links

- The background  Property: https://developer.mozilla.org/en-US/docs/Web/CSS/background

- Styling Images: https://www.w3schools.com/css/css3_images.asp
Filters: https://developer.mozilla.org/en-US/docs/Web/CSS/filter

- Styling SVG: https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/SVG_and_CSS

## Rules to Remember:

**First Rule:** Position: Fixed
- Containing Block: The viewport.
- Behavior: When an element has position: fixed, any percentage values ​​applied (such as width or height) will be based on the width and height of the viewport. In other words, the percentage unit refers to the viewport.
- Example: A navigation bar with a width of 100% will adjust to the width of the viewport, regardless of where it is on the page.

**Second Rule:** position: absolute
- Containing Block: The closest ancestor that has a position other than static (usually relative).
- Behavior: When an element has position: absolute, the percentage unit refers to the content of the closest ancestor with relative position, including padding.
- Example: A tagline with position: absolute and a width of 100% will adjust to the width of its parent with position: relative, not to the viewport.

**Third Rule:** position: static or relative
- Containing Block: The closest block-level ancestor (such as a div).
- Behavior: When an element has position: static or relative, the percentage unit refers only to the content of the block-level ancestor, without considering the padding.
- Example: An image container with position: static or relative and a width of 50% will be based on the content of its block-level parent, not the padding or border.

## Working with "rem" & "em"

**"Em" units:** These are relative to the font size of the parent element. For example, if an element's font size is 20px and a subtitle is 2em, the final size of the subtitle will be 40px. This can create a cascading effect, where the value is multiplied as you move down the element hierarchy.

**"Rem" units:** The main difference is that rem units are always relative to the font-size of the root element (HTML). This makes it easier to control layout and fonts, as all values ​​are based on the browser's default font size, providing greater consistency and flexibility. This means that a value of 1rem is equal to the font-size of the root element (usually 16px), and calculations are made from this value.

The core concept is that "rem" offers a more robust and controllable solution for responsive design, allowing greater control over font size and overall layout.

## Section 9: Manipulating Element Classes

Using the .classList object provides some helper methods, such as checking if it contains a given class. This can be used in "if" statements, to add or remove a class, or even to automatically remove it if it is active or inactive.

## Section 10: Understanding Hardware Pixels vs. Software Pixels

For a web page to display correctly on mobile devices, it is necessary to add the viewport meta tag in the HTML code, as it allows the browser to adjust the page layout according to the actual width of the device.

The viewport meta tag must have the property "width=device-width", which tells the browser to use the physical width of the device, and "initial-scale=1.0", which defines the initial zoom level. With this, the responsive design begins to work correctly, adapting to the mobile screen.

## Section 10: Understanding the "viewport" Metatag

Adding a "viewport" attribute (e.g. name="viewport") to a meta tag allows us to tell that meta tag that it should target the viewport. So, in effect, the area on our device within our browser should display our website.

The second attribute we add is the content attribute (e.g. content="width=device-width") which we can now set the width of our page.

Example:
```HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## Section 10: Things to Keep in Mind when Working with Media Queries

- When you’re building a responsive website, it’s essential to determine the breaking points where the layout should adjust for different devices. There’s no set formula for this, but you can use the width of common devices as a guide.

- A good practice is to use tools like mydevice.io to compare CSS width and height for popular devices (smartphones and tablets). For example, a breaking point of 768px might be a good starting point for portrait devices (like tablets), while for modern smartphones, a breaking point might be around 300px to 768px.

- Instead of adding too many breakpoints (e.g. 10 media queries), it is recommended to define just a few logical, broad breakpoints that cover the most common device ranges. For example, a breakpoint at 768px for tablets and another at 1000px for larger screens.

- While it is acceptable to add media queries just below CSS rules, a good practice for keeping your code organized is to move them to the end of the file. This makes it easier for other developers to find and modify the media queries if necessary.

## Section 10: Useful Resources & Links

- Absolute lengths on W3.org: https://www.w3.org/TR/css-values-3/#absolute-lengths

- More about device sizes: https://bjango.com/articles/min-device-pixel-ratio/

- Media queries theory: https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries

- Applying media queries: https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries

## Section 11: Understanding Advanced Attribute Selectors

1. **Simple Attribute Selectors:**

    - **Attribute selection:** You can select HTML elements that have a specific attribute. For example, select all ```<input>``` elements that have the attribute type, which could be "email", "password", etc.

    - Example: 
        ```CSS
        input[type="email"]
        ``` 
        Selects all input fields of type "email", but not those of type "password" or "text".

2. **Attribute List Selection:**

    - **Using the tilde (~) symbol:** If an attribute contains a list of values, you can select elements that have a specific value within that list. For example, if an element's lang attribute contains the values ​​"en-us" and "en-gb", you can use the selector to select any element with "en-us".

    - Example: 
        ```CSS
        p[lang~="en-us"] 
        ```
        Selects ```<p>``` elements that have "en-us" in the lang attribute, even if it contains other values ​​such as "en-gb".

3. **Attribute Prefix Selection:**

    - **Using the pipe symbol (|):** You can select elements where the value of an attribute begins with a specific word. This is useful for attributes like lang, where you might want to select all elements that have values ​​like "en" (for English, for example).

    - Example: 
        ```CSS
        [lang|="en"]
        ``` 
        Selects elements with lang values ​​like "en-us", "en-gb", etc.

4. **Selecting by Attribute Suffix:**

    - **Using the dollar sign ($):** This selector allows you to select elements whose attribute value ends with a specific word. This is useful, for example, to select anchor links that have a specific referring URL.

    - Example: 
        ```CSS
        [href$=".pdf"]
        ```
        Selects all ```<a>``` elements whose href attribute ends with ".pdf".

5. **Substring Selection within an Attribute:**

    - **Using the asterisk (*):** You can select elements whose attribute value contains a specific substring anywhere in the value.
    
    - Example:
        ```CSS
        [src*="cdn"]
        ```
        Selects all elements with the src attribute that contain "cdn" anywhere in the value (useful for selecting images hosted on a CDN).

6. **Case Sensitivity:**

    - **Using the i modifier:** By adding the letter "i" to the end of the attribute selector, you disable case sensitivity, allowing the search to be case insensitive.

    - Example: 
        ```CSS
        [src*="cdn" i] 
        ```
        Selects all elements that contain "cdn", regardless of whether they are in upper or lower case.

## Section 11: Providing Validation Feedback

Creating a client-side validation provides immediate feedback to the user, and can be implemented with:

- **CSS classes:** Added to invalid elements manually or via JavaScript.

- **Pseudo-SAC selectors (:invalid, :valid):** Automatically applied by the browser based on HTML attributes such as type="email" or required.

Stylize invalid elements with borders, colors, or other visual styles.

Use CSS classes as invalid or the pseudo-selector :invalid to apply styles.

Manage style conflicts using specific rules or the !important.

Use HTML attributes as required for basic validations without the need for JavaScript.

For more advanced validations (such as applying styles only after user interaction), use JavaScript to add or remove classes dynamically.

_PS: Check for resource compatibility using documentation such as the Mozilla Developer Network (MDN)._

## Section 11: Useful Resourses & Links

- Styling Form Elements: https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Styling_HTML_forms

- Styling a ``<select>``  Element: https://stackoverflow.com/questions/1895476/how-to-style-a-select-dropdown-with-css-only-without-javascript

## Section 12: Comparing Generic Families & Font Families

**Generic Families** they are broad groups that define general characteristics of the sources. They are like categories that share certain visual attributes. There are 5 main generic families: _Serif, Sans-serif, Cursive, Monospace, Fantasy_

**Font Families** these are specific groups of sources that belong to a generic family. Like for example: _Em Serif -> Times New Roman, Georgia, etc._

## Section 12: Changing the Line Height

Line-height is a property used in CSS to control the vertical space between lines of text in an element. It defines the space between the top and bottom of the text, acting as a sort of "height" for each line within a text box.

Line height is usually proportional to font size. For example, if your font size is 20px and your line height is set to "2", the final height will be 40px (20px x 2).

Different fonts can influence line height behavior even if the font size is the same. This is because each font family has specific characteristics, such as internal spacing.

It is more reliable to use numbers instead of percentages to avoid unexpected behavior, especially on elements that inherit styles from others (such as from a parent element).

## Section 12: Loading Performance & "font-display"

When we use custom fonts on our website, the browser needs to download them before it can display them. During this time, there are different ways to handle the text that is waiting for the font to load. This is controlled by something called the "font-display" property. Here are the main options and how they work:

1) **swap:**
- The text appears immediately in a default (fallback) font.
- When the custom font loads, it automatically switches to the new font, no matter how long it takes.

2) **block:**
- The text doesn't appear for a short period ("blocking" time).
- Then it appears in a default font until the custom font loads.
- It switches to the custom font when it's ready, even if it takes a while.

3) **fallback:**
- The text does not appear for a very short time.
- Then, it appears with a default font.
- The change to the custom font only happens if it loads very quickly. Otherwise, the website continues with the default font.

4) **optional:**
- The browser decides whether or not to load the custom font based on the quality of the internet connection.
- If the internet connection is good, it tries to load it. If it is bad, it just uses the default font.

5) **auto:**
- The browser decides on its own how to handle fonts (it usually uses the block behavior).

## Section 12: Useful Resources & Link

- Web Safe Fonts: https://www.cssfontstack.com/
- Google Fonts: https://fonts.google.com/
- The "line-height" property: https://developer.mozilla.org/en-US/docs/Web/CSS/line-height

## Section 13: Understanding Flexbox

Flexbox is a CSS tool that helps you arrange elements on the screen. With Flexbox, you can easily control how the items inside the container are arranged: aligned in a row, stacked in a column, centered, with specific spacing, etc.

When we apply display: flex; to an element, it becomes a **flex container**.
The elements inside it become **flex items**.

- **Properties for the container (parent):**
    - flex-flow;
    - justify-content;
    - align-content;
    - align-items

- **Properties for items (children):** 
    - order;
    - flex;
    - align-self

## Section 13: Understanding the Importance of Main Axis & Cross Axiss

**1. What are axes in Flexbox?**

- **Main axis:** This is the axis where flex items are aligned. It depends on the flex direction:
    - **Row:** This goes from left to right (or right to left with row-reverse).
    - **Column:** This goes from top to bottom (or bottom to top with column-reverse).
-   Cross axis: This is the axis perpendicular to the main axis:
    - If the main axis is a row (horizontal), the cross axis is vertical.
    - If the main axis is a column (vertical), the cross axis is horizontal.

**2. How does flex-direction affect axes?**

- **Row:**
    - Main axis: Left to right.
    - Cross axis: Up to down.
- **Row-reverse:**
    - Main axis: Right to left.
    - Cross axis: Up to down.
- **Column:**
    - Main axis: Up to down.
    - Cross axis: Left to right.
- **Column-reverse:**
    - Main axis: Down to up.
    - Cross axis: Left to right.

**3. Start point and end point**

The **starting point** changes depending on the direction:

- **Row:** Starts in the top left corner (or top right with row-reverse).
- **Column:** Starts in the top left corner (or bottom left with column-reverse).

**4. Item wrapping (flex-wrap)**

When there is not enough space:
- Items "wrap" to the next row or column on the cross-axis.

## Section 13: Working with "align-items" & "justify-content"

- **flex-direction:** row _(main axis is horizontal)_
    - **justify-content**: defines the positioning of flexible elements along the main axis (horizontal).
    - **align-items**: defines the positioning of flexible elements along the transverse axis (vertical).
- **flex-direction**: column _(main axis is vertical)_
    - **justify-content**: defines the positioning of flexible elements along the main axis (now vertical).
    - **align-items**: defines the positioning of flexible elements along the transverse axis (now horizontal).

_**Reusme:** Justify content refers to the main axis, and align items refer to the cross axis._

## Section 13: Useful Resources & Link

- Flexbox and browser compatibility: https://caniuse.com/#search=flexbox

- The theory behind flexbox: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/

- The flex container: https://developer.mozilla.org/en-US/docs/Glossary/Flex_Container

## Section 14: Using the Grid on our Project

Elements that are out of the document flow, such as those with position: absolute or position: fixed, are not considered in the CSS Grid layout. This happens because Grid organizes the direct children of the grid container within its rows and columns, but absolutely or fixed-positioned elements are removed from this normal positioning flow.

However, it's important to note that an absolutely positioned element can be placed relative to a grid item if the grid container has position: relative or another positioning value that makes it a reference context for the absolute element.

## Section 14: Working with "fit-content"

The function `fit-content()` in CSS Grid is used to define the size of the columns or rows so that they fit the content, respecting a specified maximum limit.

## Section 14: Comparing Grid & Flexbox

- Grid is two-dimensional, ideal for layouts with rows and columns.
- Flexbox is one-dimensional, used to arrange items in a row or a column.
- Although flex-wrap can create multiple lines/columns in Flexbox, positioning items relative to each other is more difficult compared to Grid.
- Grid is better for complex layouts, such as forms, while Flexbox works well for lists of items arranged in a single direction (e.g., side-by-side cards).
- The general rule: Use Flexbox for one-dimensional layouts and Grid for two-dimensional layouts.

## Section 14: Wrap Up

- Creating a Grid:
    - `display: grid`creates a grid where child elements are automatically placed in rows.
    - The default can be  overwritten with `grid-auto-flow` (and then also `grid-auto-rows` or `grid-auto-columns`).
    - Use `grid-gap` to add gaps between columns and rows.

- Defining the Grid Structure
    - You define columns and/or rows explictly via `grid-template-columns/`grid-template-rows`.
    - Use repeat (`times`, `size`) to create multiple columns and rows with ease.
    - Use `auto-fill`/`auto-fit` to derive the number of columns automatically.
    - Use `minmax` for dynamic sizing.

- Placing Elements
    - Position elements in the grid via `grid-row` and/or `grid-column`.
    - Use `span x` to span an element over multiple columns or rows.
    - Use line numbers, line names or named areas.

- Align Elements
    - Align grid item via `justify-items` (X-axis) and `align-items` (Y-axis).
    - Align the entire grid content via `justify-content` (X-axis) and `align-content` (Y-axis).

## Section 14: Useful Resources & Links

- A really great article series on the CSS Grid: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout

- A complete guide to CSS Grid: https://css-tricks.com/snippets/css/complete-guide-grid/

## Section 15: Using Rotate and Translate

The best approach for visually moving an element is using the `translate` function within the `transform` property. The focus was on `translateX` and `translateY`, which allow shifting the element along the X and Y axes, respectively, using units like `rem`, `px`, `em`, or percentages. However, if the element is rotated, the X-axis will no longer be a standard horizontal line but rather a diagonal, affecting how the transformation behaves.

Additionally, the element’s width was increased to center the text and create a badge-like effect. To finalize the positioning, `translateX` and `translateY` values were adjusted for the best fit. Any part exceeding the container’s boundaries was clipped using the `overflow: hidden` property.

Using `translate` instead of `top` and `right` has the advantage of hardware acceleration, making movement smoother and more efficient, especially when combined with transformations like rotation.

## Section 15: Useful Resources & Links

- CSS Transforms: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms

- 3D Transforms: https://desandro.github.io/3dtransforms/

## Section 16: CSS "transition" Property Deep Dive

The transition  property is used as see in the previous video:

`transition: WHAT DURATION DELAY TIMING-FUNCTION;`

Example:

`transition: opacity 200ms 1s ease-out;`

_Can be translated to: "Animate any changes in the opacity  property (for the element to which the transition  property is applied) over a duration of 200ms. Start fast and end slow, also make sure to wait 1s before you start"._

Em vez dessa abreviação, você também pode especificar as quatro propriedades individuais:

1) transition-property  (https://developer.mozilla.org/en-US/docs/Web/CSS/transition-property => transition-property: opacity; 

2) transition-duration  (https://developer.mozilla.org/en-US/docs/Web/CSS/transition-duration) => transition-duration: 200ms; 

3) transition-timing-function  (https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function) => transition-timing-function: ease-out; 

Possible timing function values are: ease-out , ease-in , linear , cubic-bezier()  and a couple of others. See the above link as well as the next lecture for more details.

4) transition-delay  (https://developer.mozilla.org/en-US/docs/Web/CSS/transition-delay) => transition-delay: 1s; 

You can read the official MDN article on CSS transitions here: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

## Section 16: Working with Timing Functions

We can think of the time or phase of the transition as a function.

Site to find timing values ​​or functions: https://easings.net/

## Section 16: CSS "animation Property Deep Dive"

The animation  property is used as see in the previous video:

`animation: NAME DURATION DELAY TIMING-FUNCTION ITERATION DIRECTION FILL-MODE PLAY-STATE; `

Example:

`animation: wiggle 200ms 1s ease-out 8 alternate forwards running; `

Can be translated to: _"Play the wiggle keyframe set (animation) over a duration of **200ms**. Between two keyframes **start fast and end slow**, also make sure to **wait 1s before you start**. Play 8 **animations** and alternate after each animation. Once you're done, **keep the final value** applied to the element. Oh, and you should be **playing the animation - not pausing**."_

Instead of this shorthand, you can also specify the individual properties:

1) `animation-name`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-name => `animation-name: wiggle`; 

2) `animation-duration`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-duration) => `animation-duration: 200ms`; 

3) `animation-timing-function`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function) => `animation-timing-function: ease-out`; 

Possible timing function values are: `ease-out` , `ease-in` , `linear` , `cubic-bezier()`  and a couple of others. See the above link for more details.

4) `animation-delay`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-delay) => `animation-delay: 1s`; 

5) `animation-iteration-count`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-iteration-count) => `animation-iteration-count: 8`; 

6) `animation-direction`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-direction) => `animation-direction: alternate`; 

7) `animation-fill-mode`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode) => `animation-fill-mode: forwards`; 

8) `animation-play-state`  (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state) => `animation-play-state: running`; 

You can read the official MDN article on CSS animations here: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations

## Section 16: Useful Resources & Links

- CSS Transitions: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

- CSS Animations: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations

- List of "transitionable" Properties: https://www.w3.org/TR/css-transitions-1/#animatable-properties