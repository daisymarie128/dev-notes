## Darwing part of an image to a canvas
Here's a quick example of how to draw just part of an image to a canvas.<br>

This example assumes you've already drawn the full sized image to a canvas. If you don't know how to do that read the previous note on how to.

First you need to tell your canvas which part you'd like to sample.<br>
To do this we use the method [`.getImageData()`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData)
```js
// ctx.getImageData(startX, startY, width, height);
const myImageData = ctx.getImageData(0, 0, 512, 512);
```

Now choose what canvas you want to draw the selected part of your image to. *(you can either make a new one or use a previously created one)*

You can either clear the canvas if you had something previously drawn on it. Or if it's a new canvas you could probably skit that line.<br>
You then need to tell you canvas where and what you want to put on it.<br>
So we do this by calling [`.putImageData()`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/putImageData)<br>
So in the example below, I tell our canvas to draw our sampled data from the original image and to start drawing from the `0, 0` coordinates of our canvas. But you could tell the canvas to start from wherever you like.
```js
const sampleCanvas = canvas.getContext('2d');
temp.clearRect(0, 0, canvas.width, canvas.height);

// temp.putImageData(imagedata, startXcoord, startYcoord);
temp.putImageData(myImageData, 0, 0);
```