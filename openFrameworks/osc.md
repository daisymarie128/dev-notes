# Using OSC to receive messages
OSC description...

## How to setup OSC in a project
Generate a project and include the addon `ofxOsc`.<br>
Then we need to include this library in our `Header` file. So go to `ofApp.h` and include it at the top of your file.
```c++
#include "ofMain.h"
#include "ofxOsc.h"

#define PORT 12345

class ofApp : public ofBaseApp{
    ....
```

Next we need to set up a port to listen and send to.
```c++
#include "ofMain.h"
#include "ofxOsc.h"

class ofApp : public ofBaseApp{
    ....
```

Now you can decide if you want to use a reseiver or a sender. See details under relevant heading.

### Creating a Receiver
First we need to create our receiver in our `setup` function.<br>
This tell ofx what port we want to listen for incoming messages on.
```c++
void ofApp::setup(){
    receive.setup(PORT);
    ....
```

It's good practice to cap things that use OSC with a frame rate. It's recommended to use either 30 or 60. If you have a lot of data not doing this can sometimes mess around with your messages that your sending or receiving.
<br>

This `while` loop will read data in, and will help make sure we're not reading extra data when nothing is being passed through.
```c++
void ofApp::update(){
    while (receive.hasWaitingMessages()) {
    }
}
```

What we want to do now is read those messages and we can check for the address which is being sent back. This can help as do different things with different types of data passed back.
<br>

In this case I'm going to call my path `"/hello/world"`, you'll need to remeber this for when you set up your sender in whatever other program you choose.
```c++
void ofApp::update(){
    while (receive.hasWaitingMessages()) {
        ofxOscMessage message;
        receive.getNextMessage(&message);
        
        if (message.getAddress() == "/hello/world") {
            oscY = message.getArgAsInt(0);
            ofLog() << "My integer is " << oscY;
        }
    }
}
```