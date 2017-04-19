## Adding textures to different segments of geometry
Quick example of how to create faces for geomtery and use it with  [`new THREE.MultiMaterial`](#https://threejs.org/docs/?q=mul#Reference/Materials/MultiMaterial)

```js
geometry.faceVertexUvs[0] = [];

for (let i = 0; i < geometry.faces.length / 2; i += 1) {
  geometry.faceVertexUvs[0].push([
  new Vector2(0, 1),
  new Vector2(0, 0),
  new Vector2(1, 1)
  ]);

  geometry.faceVertexUvs[0].push([
  new Vector2(0, 0),
  new Vector2(1, 0),
  new Vector2(1, 1)
  ]);

  const j = 2 * i;
  geometry.faces[j].materialIndex = i;
  geometry.faces[j + 1].materialIndex = i;
}
```