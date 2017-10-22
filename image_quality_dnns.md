# Paper

* **Title**: Understanding How Image Quality Affects Deep Neural Networks
* **Authors**: Samuel Dodge and Lina Karam
* **Link**: https://arxiv.org/pdf/1604.04004.pdf
* **Tags**: Image Quality, Neural Networks, Object Recognition
* **Year**: 2016

# Summary

### What

  * Computer vision algortihsm are often trained and test on high quality image datasets, but input images cannot always be assume to be of high quality.
  * This paper evaluates 4 DNN models for image classification under 5 types of quality distortions: blur, noise, contrast, JPEG, and JPEG 2000 compression.
  * The results indicate the distortion level at which image classification performance begins to degrade and how this differs across network architectures.
  
![Image Distortion Types](img/image_quality_dnns/1.png?raw=true "Image distortions")

### How

  * Start by augmenting ImageNet dataset with different types of distortions.
  * Test on a 10,000 image subset out of the 50,000 images, consists of 10 randomly chosen images from each of the 1,000 categories.
  * Consider two measure of accuracy: top-1 classification accuracy and top-5 classification accuracy.

### Results
  * Results show that all neural networks tested are susceptible to blur and noise distortions, while mostly resilient to compression artifacts and contrast.
  * Even moderate blur reduces the accuracy of networks significanty, possibly because blur removes specific textures that a network may be using to classify an image.
  * Performance with noise falls off slower in VGG-16 and GoogleNet fall off slower, possible due to the deeper structure, allowing more room to learn features that are invariant to noise.
  * At noise standard deviation of 90, network classification performance is less than 20% on average, even though images at this level of distortion and still easily recognizable by humans.
  * Performance degradation is only observed with JPEG compression at very high levels of compression, so we can be reasonably confident that standard networks will perform well with compressed data.
	




-------------------------

# Details

* Comparison of network architectures benchmarked in this paper:
 
   | Method           | PSNR           | SSIM  | Number of Parameters |
	| :-------------:    |:-------------: | :-----:|:--------------------:|
	| Caffe Reference | 5 | 3 | 61 million |
	| VGG-CNN-S | 5 | 3 | 102 million |
	| VGG-16 | 13 | 3 | 138 million |
	| GoogleNet | 21 (inception layers) | 1 | 7 million |
	
* Graphs of classification performance with increasing levels of distortion:
![Classification Performance](img/image_quality_dnns/2.png?raw=true "Classification Performance")
