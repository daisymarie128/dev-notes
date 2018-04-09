# How to make a drawing app
First generate a new project as explained in the getting started section.
<br>

We're going to aim to create a simple app which just draws some basic lines.<br>
In your Header file `ofApp.h`, define `ofPolyline line;`.

<br>

Next lets set a background color in our setup function, make it black, `ofBackground(0, 0, 0);`
<br>

Now in our `mouseDragged` function lets add some code which will tell our progam to add points to our line which we're dragging the mouse around.<br>
```c++
void ofApp::mouseDragged(int x, int y, int button){
    ofPoint pt;
    pt.set(x,y);
    line.addVertex(pt);
}
```

And finally lets add some code in our `draw` function, which will allow our line to continuously be drawn.<br>
```c++
void ofApp::draw(){
    line.draw();
}
```

Now you can run your App `cmd + r` and that should build successfully and we now have a basic app which draws a line to the screen. Woo!

**System Notes**
