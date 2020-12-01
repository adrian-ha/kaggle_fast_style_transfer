# kaggle_fast_style_transfer
 Image-to-image translation has been an increasingly popular topic over the last years. One example of such a task is art style transfer. 
Style transfer algorithms in the context of art try to capture the general style of an artist or an image and apply it to one or many content pictures. 
As an example, think of your latest holiday picture and try to imagine how Monet or Van Gogh would have painted the scene.
There are several different structures that try to do this task. One of the main differences is whether the style and content picture(s) are paired. 
A great paper to read to get started with style transfer is [Gatys et al. (2016)](https://openaccess.thecvf.com/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf). 
In the below notebook I apply a faster alternative implementation that uses an encoder / decoder structure and uses a pre-trained Vgg19 model to compute the loss and train the model. 

Instance normalization is a normalization method that seems to work particularly well for style transfer which is why we will use it in the below implementation. More information can be found in [Ulyanov and Vedaldi (2017)](https://arxiv.org/pdf/1607.08022.pdf). 

Furthermore, I will use a perceptual loss as described in [Johnson et al. (2016)](https://arxiv.org/abs/1603.08155).
