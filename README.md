# Transfer-Learning---CNN
## VGGNet architecture
_Transfer Learning is an major aspect in Deep Learning and it's techniques._

Most of the time you won't want to train a whole convolutional network yourself. Modern ConvNets training on huge datasets like ImageNet take weeks on multiple GPUs. 

Instead, most people use a pretrained network either as a fixed feature extractor, or as an initial network to fine tune. In this notebook, you'll be using VGGNet trained on the ImageNet dataset as a feature extractor. Below is a diagram of the VGGNet architecture.

![CNN Architecture](https://github.com/Ratna04priya/Transfer-Learning---CNN/blob/master/assets/cnnarchitecture.jpg)

VGGNet is great because it's simple and has great performance, coming in second in the ImageNet competition. The idea here is that we keep all the convolutional layers, but replace the final fully connected layers with our own classifier. 

This way we can use VGGNet as a feature extractor for our images then easily train a simple classifier on top of that. What we'll do is take the first fully connected layer with 4096 units, including thresholding with ReLUs. We can use those values as a code for each image, then build a classifier on top of those codes.

## Pretrained VGGNet

This is a really nice implementation of VGGNet, quite easy to work with. The network has already been trained and the parameters are available from this link.
Here, just concatenated the batch of images into the images array, and create the feed_dict as input images. And then session run, got the relu6 layer,and then that became codes_batch. 

And then after that, since codes is already existing,then we go to this else part, and then we just concatenate the new codes block with the old codes block.
So you can just build up a new set of codes like this.

## VGG-16
### The Architecture

![VGG16 Architecture](https://github.com/Golden-Bug/Transfer-Learning---CNN/blob/master/assets/vgg16.png)

The input to cov1 layer is of fixed size 224 x 224 RGB image. The image is passed through a stack of convolutional (conv.) layers, where the filters were used with a very small receptive field: 3×3 (which is the smallest size to capture the notion of left/right, up/down, center). In one of the configurations, it also utilizes 1×1 convolution filters, which can be seen as a linear transformation of the input channels (followed by non-linearity). The convolution stride is fixed to 1 pixel; the spatial padding of conv. layer input is such that the spatial resolution is preserved after convolution, i.e. the padding is 1-pixel for 3×3 conv. layers. Spatial pooling is carried out by five max-pooling layers, which follow some of the conv.  layers (not all the conv. layers are followed by max-pooling). Max-pooling is performed over a 2×2 pixel window, with stride 2.

Three Fully-Connected (FC) layers follow a stack of convolutional layers (which has a different depth in different architectures): the first two have 4096 channels each, the third performs 1000-way ILSVRC classification and thus contains 1000 channels (one for each class). The final layer is the soft-max layer. The configuration of the fully connected layers is the same in all networks.






