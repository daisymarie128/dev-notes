## Using mulitple texture images with one shader
This is an example of how to setup your shader to render two image textures, while moving them.

Main things you need: 
- two uniform values, which will pass back your textures. – make sure they use the type `t`
```js
uniforms = {
    uMapOne: { type: 't', value: null },
    uMapTwo: { type: 't', value: null },
};
``` 

- two textures for our images.
```js
const textureOne = new TextureLoader();
textureOne.load('image.png', texture => {
    material.uniforms.uMapOne.value = texture;
});

const textureTwo = new TextureLoader();
textureTwo.load('image2.png', texture => {
    material.uniforms.uMapTwo.value = texture;
});
```

In your .js file it could look something like this:
```javascript
uniforms = {
    uResolution: { type: 'v2', value: new THREE.Vector2() },
    uMapOne: { type: 't', value: null },
    uMapTwo: { type: 't', value: null },
    uPosition: {
    type: 'vec3',
    value: new THREE.Vector3()
    }
};

const material = new THREE.ShaderMaterial({
    uniforms: this.uniforms,
    vertexShader: document.getElementById('vertexshader').textContent,
    fragmentShader: document.getElementById('fragmentshader').textContent,
    side: DoubleSide
});

const textureOne = new TextureLoader();
textureOne.load('image.png', texture => {
    material.uniforms.uMapOne.value = texture;
});

const textureTwo = new TextureLoader();
textureTwo.load('image2.png', texture => {
    material.uniforms.uMapTwo.value = texture;
});

textureOne.wrapS = RepeatWrapping;
textureOne.wrapT = RepeatWrapping;
```

##### Fragment Shader
This shader simply places our 2 images side by side and animates its scale from 150% to 100%, plus translates the images right.

We took our two images and transformed there position and scales in the texture2D. Then we use a condition to check the positions and whether it should be image 1 or 2.<br>


> Note: Remember that uv's are always between 0 and 1.

Snippet of what your fragment shader should look like.
```glsl
uniform sampler2D uMapOne;
uniform sampler2D uMapTwo;
uniform vec3 uScale;
uniform vec3 uPosition;
void main() {
    vec2 st = gl_FragCoord.xy / uResolution;
    vec2 uv = vUv;
    vec4 image1 = texture2D(uMapOne, vec2(1.0, 0.0) + (uv - uPosition.xy) / uScale.xy);
    vec4 image2 = texture2D(uMapTwo, (uv - uPosition.xy) / uScale.xy);
    if (uv.x < uPosition.x) {
        gl_FragColor = image1;
    } else {
        gl_FragColor = image2;
    }
}
```