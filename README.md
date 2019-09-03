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



