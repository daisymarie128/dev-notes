## Shaders
Shaders are small programs written in the OpenGL Shading Language (GLSL), which is a language similar to C/C++. They are compiled and run on the GPU, and are extremely performant.
Three declarations you can make<br>
UNIFORMS - ATTRIBUTES - VARYINGS

**uniforms**
- sent to both shaders
- contain values that stay the same across the entire frame being rendered
- attributes which are passed from CPU to GPU

**attributes**
- applied to individual vertices
- ONLY available to vertex shaders
- could be like each vertex having a distinct color
- one to one relation ship with verticies

**varyings**
- declared in the vertex shader BUT want to SHARE with the fragment shader
- MAKE SURE to declare a varying variable of the same type and name in both the vertex and fragment shader.
- common for vertex normals which can be used for lighting calcs.

This is an example of a basic fragment shader:
```c
precision highp float;
varying vec2 vUv;

void main () {
  gl_FragColor = vec4(vUv.xy, 1.0, 1.0);
}
```
<img src="../assets/webgl/basic-shder.png" width="450px"/>
