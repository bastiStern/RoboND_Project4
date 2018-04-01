[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)
## Deep Learning Project ##
[//]: # (Image References)
[image1]: ./pics/pl1.png

In this project we need to build and train a neural network
to find and isolate a single person from the image feed of the simulated drone footage.
The drone inside the simulator should then, if the network works fine, follow this person.

## Architecture
For the upcoming task we need a model that is able to classify each individual pixel in the constant
video stream without loosing any of the given spatial information in the original image.
Therefor a FCN(Fully Convolutional Network) comes in very handy because it mets all the previously mentioned requirements.
To label each pixel of the we use Semantic Segmentation which is a pixel wise classification technique.
A typical FCN consists of three base components: Encoder, 1x1 Convolution Layer and Decoder.

## Encoder
The encoder section of a FCN is a stack of one or more convolution layers.
Each layer performs its own convolution resulting in a new height, width and depth which each additional layer.
Because the weights used in this convolution are shared over the entire operation these network architecures
are much more efficient than a regular Deep Neural Network. The general idea is, that the encoder looks a bit like a stepped pyramid and with each
convolutional layer we climb on step up on this pyramid.

## 1x1 Convolution Layer
After the encoder a 1x1 Convolution Layer follows in the architecture of our FCN. In this part

## Decoder

## Hyperparameters

## Training

## Results

## Sources