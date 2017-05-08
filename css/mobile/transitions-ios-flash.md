## White flash with using transitions on iOS
Sometimes when using css transitions everything will look fine, until you check it on iOS. What usually happens is a white flash at the end of the transition.<br>

Example:
```css
.div-to-transition {
  opacity: 0;
  transition: opacity 1s ease-in;

  &.fade-in {
    opacity: 1;
  }
}
```

To fix this you can either try adding `-webkit-backface-visibility: hidden;` to the element transitioning. - however sometimes I find this to be a pain and not work very well.

Another option is to just use animation keyframes.

Example fix:
```css
.div-to-transition {
  opacity: 0;

  &.fade-in {
    animation: fade-in 550ms cubic-bezier(0.39, 0.575, 0.565, 1) forwards;
  }
}

@keyframes fade-in {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}
```