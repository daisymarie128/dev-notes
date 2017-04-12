## Darwing images in canvas
A quick example of how to draw an image to a canvas.<br>
First get create a `context` element, which we get from our canvas element. Do this by:<br>
`const ctx = this.canvas.getContext('2d');`

Next you need to create a new image object, then give it a src to use: <br>
`this.img = new Image();`<br>
`this.img.src = 'image.png';`

Then you need to listen for when the image has loaded. In this function is where you want to do your drawing to the canvas:
```js
this.img.onload = () => {
    this.canvas.width = this.img.width;
    this.canvas.height = this.img.height;
    ctx.drawImage(this.img, 0, 0, this.canvas.width, this.canvas.height);
}
```

All the code togther:
```js
createTexture() {
    const ctx = this.canvas.getContext('2d');
    this.img = new Image();
    this.img.src = 'image.png';
    this.img.onload = () => {
        this.canvas.width = this.img.width;
        this.canvas.height = this.img.height;
        ctx.drawImage(this.img, 0, 0, this.canvas.width, this.canvas.height);
    }
}
```