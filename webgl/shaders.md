## Shaders
Shaders are small scripts which are written in the OpenGL Shading Language (GLSL), which is a language similar to C/C++. These scripts are processed on your GPU instead of you CPU which makes their performance for graphics extremely fast. Using a shader can speed up your app significantly.

Shaders are run once per pixel that is on screen, which is usually always an extremely large number. The reason why shaders are so performant is because they draw many pixels in parallel (i.e. at the same time). But because of this, the shaders can only work on a single pixel at a time, and they don't access to the values of any other pixels.

There are two types on shaders:<br>
[Vertex Shader](#vertex)<br>
[Fragment Shader](#fragment)

<!-- TODO: update this -->
#### Vertex
Vertex shaders are typically used to tell the GPU where to draw/place things in a 2D or 3D space.
Consider it like this:<br>
Take a standard sphere. Its made up of many vertices (depending on the detail more). A vertex shader takes these points and manipulates them (moves them etc - this is how you can animate with a shader).<brb>

Vertex shaders have one main responsibility - it MUST at some point set something called `gl_Position` (a 4d float vector - this is the final position of the vertex on screen).

#### Fragment
Fragment shaders are typically used to output the pixel colors of the vertex shader. They handle things to do with texture, lighting and color.

Its one MUST do job is: set or discard the `gl_FragColor` variable, another 4D float vector - which is the final color of our fragment.<br>
Now imagine a fragment like this:<br>
A triangle – and it reads its three vertices which it is made up of. And now each pixel in the triangle needs to be drawn out. A fragment is the data provided by these 3 vertices in order to color the triangle. So if one vertex was red and another blue - you would get a gradient from red - purple - blue.

*Example of what the shaders compute*
<img src="../assets/webgl/basic-shder.png" width="450px"/>

#### Shader Variables
There are three declarations you can make using shaders.<br>

 UNIFORMS                                                    | ATTRIBUTES                             | VARYINGS                                                                    |
:----------------------------------------------------------- |:-------------------------------------- |:--------------------------------------------------------------------------- |
Sent to both shaders                                         |Applied to individual vertices          |Declared in the vertex shader BUT want to be shared with the fragment shader |
Value that stays the same across entire frame being rendered |Only available to the vertex shader     |Processed in the vertex shader first                                         |
Values which are passed from the CPU to the GPU              |One to one relation ship with vertices  |Fragment shader receives interpolated data                                   |


This is an example of a basic fragment shader:
```c
precision highp float;
varying vec2 vUv;

void main () {
  gl_FragColor = vec4(vUv.xy, 1.0, 1.0);
}
```
*result:*
<img src="../assets/webgl/basic-shder.png" width="450px"/>

#### Data Types & Syntax
A vector is
