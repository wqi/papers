# Paper

* **Title**: Perceptual Losses for Real-Time Style Transfer
and Super-Resolution
* **Authors**: Justin Johnson, Alexandre Alahi, Li Fei-Fei
* **Link**: https://arxiv.org/pdf/1603.08155.pdf
* **Tags**: Super-Resolution, Content Loss, Neural Network, Styles Transfer
* **Year**: 2016

# Summary

### What

  * Using MSE as the loss function in super-resolution and style transfer algorithms results in overly smooth images lacking high-frequency detail, as the per-pixel loss does not capture perceptual differences between output and ground-truth.
  * High-quality images can be generated using perceptual loss functions based instead on differences between high-level feature representations extracted from pre-trained CNNs.
  * This paper combines the benefits of feed-forward image transformation networks and perceptual loss functions for improved qualitative results in style transfer and single image super-resolution (SISR) tasks.
  * Single-Image Super Resolution
	  * Traditional metrics used to evaluate super-resolution performance are PSNR and SSIM, both of which have been shown to correlate poorly with human assessment of "image quality".
	  * Since PSNR is equivalent to per-pixel loss, a model trained to optimize for PSNR should always outperform a model trained to minimize feature reconstruction loss. As a result, this method is intended to showcase the qualitative improvement in quality.


### How

  * Pre-trained CNNs for image classification help address the shortcomings of per-pixel losses as the have already learned to encode the perceptual and semantic information we'd like to measure in our loss. 
  * The pre-trained loss network is used to define loss functions that measure the perceptual difference between output images and ground truth examples.
  * Single-Image Super Resolution
	  * Super-resolution network trained with feature reconstruction loss to allow transfer of semantic knowledge from loss networks
	  * Paper focuses on x4 and x8 scale super-resolution since larger scale factors require more semantic reasoning about input


### Results

  * Single-Image Super Resolution
	  * Compared to state of the art SRCNN, this model trained for feature reconstruction does a better job at reconstructing sharp details and find details, such as eyelashes on the baby image below.
	  * Feature reconstruction loss results in a slight cross-hatch pattern visible under magnification, which harms its PSNR and SSIM vs SRCNN.
	  * The same network with per-pixel loss results in fewer artifacts and higher PSNR, but the feature loss results in better fine details and more pleasing qualitative visual results.
	  * Performance for x4 evaluated on Set5 dataset.
	   
		| Method           | PSNR           | SSIM  |
		| -------------    |:-------------: | -----:|
		| Bicubic          | 28.43          | 0.8114|
		| SRCNN            | **30.48**          | **0.8628**|
		| **Per-Pixel Loss**   | 28.40          | 0.8205|
		| **Perceptual Loss**  | 27.09          | 0.7680|
	



![Sampling Process](img/perceptual_loss/1.png?raw=true "Sampling process")


-------------------------

# Details

* SISR Model Architecture and Training
  * Dataset: MS-COCO (10k images with 288x288 patches)
  * Pre-processing: Blur with Gaussian kernel of width 1.0 and downsample with bicubic interpolation
  * Batch size of 4 for 200k iterations using Adam with learning rate of 1*10^-3 with no weight decay or dropout
  * Minimize feature reconstruction loss at layer *relu2_2* from the VGG-16 loss network
  * Post-process by performing histogram matching between network output and LR input
