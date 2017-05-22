##BEM good tips

### class names
If a component or element is going to be reused, it's good to seperate out modifer classes.<br>
E.g
```html
<button class="o-button button--white button--large">I'm a button</button>
```

Seperating out modifiers like this allows you to easily reuse and change styles without have to re-write or duplicate and styles.<br>
Another example:<br>
```html
<button class="o-button button--white button--large">I'm a button</button>
<button class="o-button button--blue button--small">I'm a smaller button</button>
```

```css
.o-button {
  width: 100px;
  height: 100px;
  border: 1px solid black;
}

.button--white {
  background-color: white;
}

.button--blue {
  background-color: blue;
}
```


