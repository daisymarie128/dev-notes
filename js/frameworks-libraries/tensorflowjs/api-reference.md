# API reference

## tf.sequential
This is a type of `model`. This type of model is where one layers outputs are then used as the lext layers inputs.
Think of this as a stack of layers with no branching or skipping.

So the first layer in the model SHOULD have a predefined input shape.

## tf.layer.dense
Creates a dense (fully connected) layer.

This layer implements the operation: `output = activation(dot(input, kernel) + bias)

kernel is a weights matrix created by the layer.

bias is a vector created by the layer(onlly applicable if useBias is true).

### Parameters:
Config (Object)
    units(number): Must be a positive integer. This is the dimensionality pf the output space.

## model.compile
This is a configuration step. Prepares the model for training and evaluation.

Compiling sets up the model with an optimizer, loss and/or metric.

If you tried to call `fit` or `evaluate` on an un-compiled model will throw an error.

### Parameters:
config (object)
    optimizer(string): // TODO: read & write notes on this
    loss(string): This is the name of an objective function. // TODO: research what loss is
    metrics(string): List of metrics to be evaluated by the model during training and testing.
