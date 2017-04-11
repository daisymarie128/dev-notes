## Darwing images in canvas

```js
createTexture() {
    const ctx = this.canvas.getContext('2d');
    this.img = new Image();
    this.img.src = 'image.png';
    this.img.onload = () => {
        this.canvas.width = this.img.width * 0.5;
        this.canvas.height = this.img.height * 0.5;
        ctx.drawImage(this.img, 0, 0, this.canvas.width, this.canvas.height);
    }
}
```