## Examples of how to draw different shapes with canvas

### Circle
```js
`.arc()` Draws an arc which is centered at (x, y).
ctx.beginPath();
// ctx.arc(x, y, radius, startAngle, endAngle, anticlockwise);
ctx.arc(75, 75, 50, 0, Math.PI * 2, true); 
ctx.fill();
```


### Rectangle
```js
ctx.strokeStyle="#000000";
ctx.strokeRect(20,20,150,100);
```

### Triangle
```js
ctx.beginPath();
ctx.moveTo(75, 50);
ctx.lineTo(100, 75);
ctx.lineTo(100, 25);
ctx.fill();
```

### Parts of a circle
```js
ctx.beginPath();
ctx.arc(
  shapes[i].x,
  shapes[i].y,
  shapes[i].r,
  shapes[i].startAngle,
  shapes[i].endAngle
);
ctx.lineWidth = 45;
ctx.strokeStyle = pattern;
ctx.stroke();
```

### Slant
```js
// skew our canvas
ctx.transform(1, 0, -0.4, 1, 0, 0);
ctx.beginPath();
ctx.lineWidth = 190;

ctx.moveTo(xCoordBottom, yCoordBottom);
ctx.lineTo(xCoordTop, yCoordTop);
ctx.strokeStyle="#000000";
ctx.stroke();
ctx.setTransform(1, 0, 0, 1, 0, 0);
```