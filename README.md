# Convolutional Neural Network

### Convolutional Layer:


- Initializing convolutional layer and filter weights and biases, filter size, stride, padding, input channel
- During __forward pass__, add padding, then loop over image, take subimages and multiply them with filter, add biases, pass them through the activation function, construct new 2D (rows, columns only) and save the output as a new feature map. 
- During __backpropagation__, first of all, taking derivative of output with respect to activation function, then taking derivative of results with respect to filters, biases, then updating the filters and biases of convolutional layer. 

### Max Pool Layer:

- Initializing max pool layer
- During __forward pass__, traverse over the image with a window of pool size, taking the maximum pixel from the window and constructing new feature maps with maximum pixels, saving the pixel location of highest pixel value for backpropagation.
- During __backward pass__, the derivative is distributed only to the maximum pixels, because only pixels with highest value are taking part in forward pass, no trainable parameters in max pool, pixels other than maximum values are not used in backpropagation.

### Flatten:

- Converting the multi-dimensional input e.g., 64*7*7 (64 feature maps of 7 x 7 shape) into 1D array. 
- During backpropagation, 1D image is reconstructed back to the shape of input, 1D -> 64*7*7

### Fully Connected Layer:

- Initializing weights and biases, multiplying weights with the input , adding biases and pass the weighted sum + bias through activation function. 
- During backward propagation, taking derivative with respect to activation function, then with respect to weights and biases, then updating weights and biases using derivative.

### CNN class:

- Combining all layers together, passing output of each layer to next layer during forward pass, then during backward pass, taking inputs from the next layer and passing them to the layer before in backward direction.

- Train method: Training loop, dividing the input into batches, forward and backward pass per batch,  calculating epoch loss and accuracy (average of loss, accuracy of all batches)
- After each epoch, calculating validation loss and accuracy. And repeat.