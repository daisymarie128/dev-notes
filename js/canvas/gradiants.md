## Gradients with Canvas
Quick example of how to make gradients in canvas.<br>

##### Linear gradients
`.createLinearGradient()` will create a gradient along a line given two points.<br>
When passing in coordinates to this function remember that they will be relevant to your canvas. Not to your shape.

`.addColorStop(offset, color)` This function defines what your gradient will look like. The first value is where along the gradient your color will start.

```js
const gradient = ctx.createLinearGradient(
  xCoordStart,
  yCoordStart,
  xCoordEnd,
  yCoordEnd
);

gradient.addColorStop(0, 'red');
gradient.addColorStop(1, 'white');
```