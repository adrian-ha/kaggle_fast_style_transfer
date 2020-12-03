# Style Transfer

Image-to-image translation has been an increasingly popular topic over the last years. One example of such a task is style transfer. Style transfer algorithms in the context of art try to capture the general style of an artist or an image and apply it to one or many content pictures. As an example, think of your latest holiday pictures and try to imagine how Monet or Van Gogh would have painted the scenes. 

There are several different structures and algorithms that try to accomplish this task. They differ in their structural set-up and slightly different applications. One of the main differences is whether the style and content picture(s) are paired (image translation one-to-one, one-to-many or many-to-many). 

I will focus on one-to-one style transfer and two implementations (two separate notebooks):
* Part 1: Original style transfer by [Gatys et al (2016)](https://openaccess.thecvf.com/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf)
* Part 2: Fast style transfer by [Johnson et al (2016)](https://arxiv.org/pdf/1603.08155.pdf)

## Short model summary

Let's beginn by providing a brief overview of the two different implementations.

### Image Style Transfer Using Convolutional Neural Networks by [Gatys et al (2016)](https://openaccess.thecvf.com/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf)

Style transfer relies on separating the content and style of an image. The main idea of this paper is that we can use different layers of pre-trained CNNs to separate the style and content of images. Assuming we have one content and one style image we try to create a new target image that contains our desired content and style components: 
* objects and their arrangement are similar to that of the content image
* style, colors, and textures are similar to that of the style image

The below illustrates the main idea of the paper:
<img src="https://miro.medium.com/max/2260/1*sBNwIsv5pPQQqHHEAkBHIw.png" alt="image1" width="500"/>

In the notebook I will initialize the target image as a copy of the content image and then update and slowly transform it. The loss is calculated based on the VGG19 feature model. The model allows to change between mse and mae loss.

### Perceptual Losses for Real-Time Style Transfer and Super-Resolution by [Johnson et al (2016)](https://arxiv.org/pdf/1603.08155.pdf)

This paper build on the work of Gatys et al. and provides a faster (proxy) implementation. According to the paper the proposed method is hundreds of times faster than the original optimization-based method. 
The authors propose to train a residual feedforward network instead of amending the target picture. However, they also use the loss function as proposed by Gatys et al. The network is a encoder / decoder architecture with residual layers that takes the content image as input and returns the style-transformed image. 
<img src="https://miro.medium.com/max/1574/1*Um82GJ99gauIOh0U-S11hQ.png" alt="image2" width="500"/>

We will also use the VGG19 feature model for the perceptual loss. Furthermore, I will use instance normalization based on [Ulyanov and Vedaldi (2017)](https://arxiv.org/pdf/1607.08022.pdf).
