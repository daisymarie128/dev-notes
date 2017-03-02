## Materials
Materials in threejs are what describe an objects appearance in your scene. You can think of it as what gives your object colors or textures.<br>
It is the second item which a Mesh requires, alongside the geometry. Threejs Provides many different material options for allowing different looks and feels in your project.

List of built in threejs materials:
- LineBasicMaterial
- LineDashedMaterial
- Material
- MeshBasicMaterial
- MeshDepthMaterial
- MeshLambertMaterial
- MeshNormalMaterial
- MeshPhongMaterial
- MeshPhysicalMaterial
- MeshStandardMaterial
- MeshToonMaterial
- MultiMaterial
- PointsMaterial
- RawShaderMaterial
- ShaderMaterial
- ShadowMaterial
- SpriteMaterial

Each material provides different options for generating different appearances. I want go over all of them but I will cover a few options which are worth noting.<br>

**Color and Colors**
Color property is the most basic and common option to set. This does the obvious and sets a particular color to the material.
```js
const material = new THREE.MeshBasicMaterial({ color: 0xffffff });
```

The colors property provides different options for coloring objects faces or vertices.
```js
THREE.NoColors
THREE.FaceColors
THREE.VertexColors
```
These provide different coloring options

**Side**
This options tells the renderer which faces to apply the material to. For example by setting `THREE.FrontSide` this will only apply the material to the front of the object. So if I ended up looking at the object from inside out at any stage nothing would be rendered to the screen. If your unsure of which to use, I recommend just sticking with `THREE.DoubleSide`.
```js
THREE.FrontSide
THREE.BackSide
THREE.DoubleSide
```

**Shading**
This tells the renderer how the object should be rendered. This difference between the 2 is that smooth will do what it says and rendered your object nice and smoothly, whereas Flatshading will make the object look more jaggedy and make it more clear to see the objects faces.
```js
THREE.SmoothShading
THREE.FlatShading
```

A collection of different materials and what they look like can be found [here](https://daisymarie128.github.io/code-references/examples/materials/index.html)
