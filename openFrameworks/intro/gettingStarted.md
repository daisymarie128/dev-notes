# Getting started with openFrameworks

Download openFrameworks for appropriate os [here](http://openframeworks.cc/download/).<br>
For me I'll use osx.<br>
<br>

Next you need to get Xcode setup correctly<br>
Follow this step by step guide if you don't already have Xcode installed: [setup guide](http://openframeworks.cc/setup/xcode/)


## How to setup your first project



### Files:

#### ofApp.h
This is the `Header` file. In here is where you will declare and define objects and types for you program to use. 

#### ofApp.cpp
This is where all the logic and main functions of your App are kept.

#### Functions:
##### setup()
The setup method is called only once at the beginning of the application. It's used to initialize other objects or variables which are usually declared in ofApp.h.

##### update/draw()
Update and draw are called in an infinite loop one after another in that order, until we finish the application.

The `update` function is where you will do calculations and updates to states. 

### How to render text to screen:
### How to debug
`std::printf("value_name: %{type}\n", {value});`
`std::printf("button: %i\n", x);`
### How to use an image:
  #### Why do assets have to be in bin/data
  // TODO: write why
  #### Loading and drawing images
  First define your image variable with the type ofImage in your header file.
  Then in `setup()` call `imageExample.load("/images/assetName.png")`

  Next to draw it to the screen we just call `imageExample.draw(posX, posY, width, height)`
  Remeber if you changed the draw color earlier in your code this will effect the result of your image. Resetting it back to `ofSetColor(255); ` can always be safe.

  #### useful functions
  Resize: `exampleImage.reseize(width, height);`
  Mirror: `exampleImage.mirror(bool width, bool height);` -- Don't use this in draw call instead place in update or appropriate listener func.

### How to render 3D object

### How to animate
### How to use a plugin/addon



### What is openGL
