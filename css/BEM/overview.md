## BEM

### What is BEM?
BEM stands for ***Block, Element, Modifier***, and put simply it's just a class naming convention to structure and organise your css.<br>

The most common way of writting BEM is like so:
```css
.block {}
.block__element {}
.block__element_modifier {} 
```

##### BEM breakdown
***BLOCK***<br>
Represents an object on your website such as a button, or a search form.

***ELEMENT***<br>
Is typically a component within the block that performs a particular function, such as a menu item, or an input field inside a search form.

***MODIFIER**<br>
This is what represents any variations of the block or element, such as a size or color.