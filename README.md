[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)
## Deep Learning Project ##
[//]: # (Image References)
[image1]: ./FCN.png

In this project we need to build and train a neural network
to find and isolate a single person from the image feed of the simulated drone footage.
The drone inside the simulator should then, if the network works fine, follow this person.

## Architecture
For the upcoming task we need a model that is able to classify each individual pixel in the constant
video stream without loosing any of the given spatial information in the original image.
Therefor a FCN(Fully Convolutional Network) comes in very handy because it mets all the previously mentioned requirements.
To label each pixel of the we use Semantic Segmentation which is a pixel wise classification technique.
A typical FCN consists of three base components: Encoder, 1x1 Convolution Layer and Decoder.

![alt text][image1]

## Encoder
The encoder section of a FCN is a stack of one or more convolution layers.
Each layer performs its own convolution resulting in a new height, width and depth which each additional layer.
Because the weights used in this convolution are shared over the entire operation these network architecures
are much more efficient than a regular Deep Neural Network. The general idea is, that the encoder looks a bit like a stepped pyramid and with each
convolutional layer we climb on step up on this pyramid.
With each additional layer in the encoder the network is able to gain a better 
understanding of the information in the image. 
For example in the first layer the network can detect lines.
In the next layer it is able to detect simple geomatrical shapes like squares or circles.

## 1x1 Convolution Layer
After the encoder a 1x1 Convolution Layer follows in the architecture of our FCN. 
In this part the data of the encoder is flattened into two dimensions by retaining 
the location information of the encoder.
This flattening process is essential for the pixelwise classification of the data. 
Unlike a Fully Connected Layer we feed the data in the 1x1 Convolution Layer to 
get a classification for each pixel in the image. 
A Fully Connected layer/network just gives us a resulting class like dog, cat, sausage.
The 1x1 convolution layer is a simple convolution, with a kernel and stride of 1.

## Decoder
The next and last section of the model is the decoder.
One decoder block consists of a simple upscaling followed by a 
concatenation of the small and larger layer.
After that a actiavation function, in this case "relu" runs over the layer.
The decoder section reverses the effect of the encoder by 
multiplying each pixel with the kernel of decoder kernel.
An essential part of this decoder are skip connections.
These Skip connections feed information from prior layers that were lost in the encoder layer. 
Skip layers use the output of a layer as input to another layer in the decoder block.
With each layer in the decoder section of the network is able reconstruct more and more of the 
resolution of original input. The ouput of the last decoder layer is exactly of the same size as the 
original input image. 

## Hyperparameters
I started with the following parameters:
- learning_rate = 0.01
- batch_size = 100
- num_epochs = 30
- steps_per_epoch = 200
- validation_steps = 50
- workers = 2

## Training
After the first 30 epochs i adjusted the learing rate to 0.001 and 
started the training again. The results after this run were better 
but not good enought so i adjusted the learnign rate once more to 0.0001 
and trainded the FCN for another 30 epochs.

## Results
The final score was 0.41 which could be better but not with thre provided data.

## Future Work
The results and the score of the network could be 
improved by collecting more data. Especially data that represents 
the weak spots of the trained network.

With the right data the network could be trained to detect 
any kind of object for example cats, cars or sausages.

 

