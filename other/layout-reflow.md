# Layout / Reflow

Layout / Reflow (called "Layout" in Chrome, Opera, Safari and IE - "Reflow" in Firefox) is where the browser needs to figure out the geometric information for all the elements in the document.
<br>
<br>
You want ot try and avoid this whenever you can, as it's a blocking synchronous operation and is quite expensive.

## Stages:

When a new element is added to the DOM using Javascript this is what will happen:<br>
```js
    var element = document.createElement('div');
    document.body.appendChild(element);
    element.innerText = 'Hello World';
    console.log('element offsetTop: ', element.offsetTop);
```

> The above is an example of the code we'll run

- Adding a new element will cause the layout to become invalid.
    - The browser now realizes it needs to perform a "layout/reflow" (it will wait till the end of the current operation or frame to do so)
- Text is then added to the element
    - This also forces a "layout/reflow" but instead forces it early before the current frame is complete - this causes the frame to now take longer.
- Finally the we call a console log to print out the elements offset value.
    - This also forces an immidiate "layout/reflow" early again.

So for just to add this new element to the DOM we had to perform 2 lots of "layout/reflow". You can imagine the issue you'd have if you were to call this in a `for` loop this would start to cause jank.

<br>

### Notes

- Refrain from creating elements in `for` loops as this is a big culprit for Layout Thrashing, which can cause jank on your site.