## Specificity
Specificity is how the browser decides which of your rules from you CSS to apply to your site.<br>

### Selector Types
The following list of selector types increases by specificity:

0. Type selectors (e.g., h1) and pseudo-elements (e.g., :before).
1. Class selectors (e.g., .example), attributes selectors (e.g., [type="radio"]) and pseudo-classes (e.g., :hover).
2. ID selectors (e.g., #example).

So this means that for markup like this:
```html
<div id="container">
    <div class="container__section"></div>
</div>
```

This style would work:
```scss
#container {
    .conatiner__section {
        width: 100px;
        height: 100px;
        background: red;
    }
}
```

But if you wanted to reuse that class and give it a different style. <br>
This would not work:
```scss
#container {
    .conatiner__section {
        width: 100px;
        height: 100px;
        background: red;
    }
}

/* This would not overide the previous style */
.conatiner__section {
    background: blue;
}
```

This wouldn't work because the styles declared before it have a higher specificity defined. As it states that for any class *INSIDE* the *DIV container* called **container__section** should have those rules.

Whereas if you tried to overide that style after it by just specifying it with it's class name, the browser would overlook this and choose the higher ordered styles.

##### !important
There is an exception when using the `important` rule. This doesn't really have anything to with specificity though, it technically just interacts directly with it. Using the declaration will overide anoy other styles that object might have.<br>
However it's always important to remember that `!important` should be avoided at all costs. Using this makes it hard to debug and can just cause general problems when developing.

#### :not
`:not` is the negation pseudo-class, which is ***NOT*** actually a pseudo-class in the specificity calculation. But selectors in the `:not` count as normal selectors when determining the count of selector types.

```css
div.outer p {
  color: red;
}
div:not(.outer) p {
  color: blue;
}
```

```html
<div class="outer">
  <p>This is some text</p> <!-- this would be red -->
  <div class="inner">
    <p>This text is other text</p> <!-- this would be blue -->
  </div>
</div>
```
