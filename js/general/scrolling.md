## Scrolling

To listen to scroll you can use `window.onscroll` or `el.addEventListener('scroll', () => function)`

To get the scroll position you can do something like this:

```
window.onscroll = (e) => {
  let scrollTopVal;
  if (IS_FIREFOX) {
    scrollTopVal = e.pageY;
  } else {
    scrollTopVal = document.body.scrollTop;
  }
}
```
Note in firefox `document.body.scrollTop` always stays at `0`.

In Firefox you can use `e.pageY`
