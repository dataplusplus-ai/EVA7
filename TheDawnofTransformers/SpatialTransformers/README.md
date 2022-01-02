

## Spatial Transformer

The spatial transformer module consists of layers of neural networks that can spatially transform an image. These spatial transformations include cropping, scaling, rotations, and translations etc

CNNs perform poorly when the input data contains so much variation. One of the solutions to this is the max-pooling layer. But then again, max-pooling layers do not make the CNN invariant image translation.

In STNs, the transformer module knows where to apply the transformation to properly scale, resize, and crop and image. We can apply the STN module to the input data directly, or even to the feature maps (output of a convolution layer). In simple words, we can say that the spatial transformer module acts as an attention mechanism and knows where to focus on the input data.

## Architecture

The architecture of a Spatial Transformer Network is based on three important parts.

The localization network.

Parameterized sampling grid.

Differentiable image sampling.

![image](https://user-images.githubusercontent.com/45157166/147868606-3fd614d7-acd5-40e6-b830-5c08dd4528ee.png)

### Localisation Network

The localization network takes the input feature map and outputs the parameters of the spatial transformations that should be applied to the feature map. The localization network is a very simple stacking of convolutional layers.

In the above figuare, U is the feature map input to the localization network. It outputs θ which are the transformation parameters that are regressed from the localization network. The final regression layers are fully-connected linear layers. Tθ is the transformation operation using the parameters θ.

### Parameterized Sampling Grid

Parameterized Sampling Grid mainly generates a sampling grid that is consistent with the picture pixels, and multiplies it with theta matrix to gradually learn to fully correspond to the tilt recognition object

### Differentiable image sampling.

Differentable Image Sampling is mainly used to obtain the original image pixels corresponding to the sampling points to form a V feature map to complete the output of the V feature map


### Model Architecture

### Training Logs

### SVisuaization of STN results
