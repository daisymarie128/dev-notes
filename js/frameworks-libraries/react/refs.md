## React refs
Ref is used to return a reference to your element.

Is especially useful when you need to find the DOM markup rendered by a component

But try to avoid overusing ref.

The ref attribute takes a callback function, and the callback will be executed immediately after the component is mounted or unmounted.

```
ref={(input) => { this.textInput = input; }}
```

example taken from [react docs](https://facebook.github.io/react/docs/refs-and-the-dom.html)
