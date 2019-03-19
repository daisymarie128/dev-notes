# Tensorflow
Tensorflow is Googles opensource library for machine learning. A library written in C++ - low level functionality. It's a low level library.

## Terminology

### Tensors
A tensor is a mathamatical thing. Holds numbers. All the operations associated with manipulating these numbers. Similar to p5 createVector();
These are the building blocks for tensors.

Scalars - single number i.e 3
Vectors - list of numbers i.e [1, 2, 3, 4, 8]
Matrices/Matrix - 2 dimentional i.e [[1, 2], [2, 3]]

## Basic building blocks
### Layers API
Apart of tensorflow.js

### Core API
- Tensor




### Making a tensor
Using proper rank tensors makes code more readable - legible
Tensors are immutable, these values can never be changed.

#### Defining shape
You say rows first. 2x3 =
```
[
  [1, 2, 3],
  [4, 5, 6]
]
```

This matters because for example if we fed in image data, you might have lots of images, lets say 100.
And each image is 28 x 28 px in dimension.
You would tell your tensor the shape of your data is:
```
[ 100, 28, 28]
```

This is preparing data. Values, Shape (defining depth), dtype (tell it what kindve numbers we are passing in).

### Helper functions:
`print()` - allows us to just see our data. console logging will return us an object.


### Ranks
Ranking is ...

#### Scalar



### Variables
If you need to change the v alues in your tensor you can use a variable. i.e for changing weights etc.
Low level api needs to know how to handle things differently.

#### Memory management
Tansorflow manages the memroy being used with your GPU.

`tf.memory` - maange helper



#### DataSync
Gives me data bake but waist for it to be done.
Comes back as a 1D array.

#### .get()
Brings us back the values we are looking for (index)

### Operations
Mathamatical operations we want t o preform on tensors themselves.
Linear algerbra
Element wise: 2 matrices adding values with exact same position.o


#### matMul
muliplying matrices: very usful for weights nureal networks
Must be rank 2 (2D matrices)
Number of columns must match the number of rows in the second matrix.o

#### Transpose
Manipulates the matrice

## Layers API
- Inputs
- Hidden
- Outputs

### dense()
Every node is fully connected to each node in model.

need to confugure the model and the layer

#### compile()



### softmax


### activation:
squashes any number into a range

### model.fit()

