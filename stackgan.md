# Paper Details

* **Title**: StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks
* **Authors**: Han Zhang, Tao Xu, Hongsheng Li, Shaoting Zhang, Xiaogang Wang, Xiaolei Huang, Dimitris Metaxas
* **Link**: [arxiv](https://arxiv.org/pdf/1612.03242.pdf)
* **Tags**: Image Synthesis, GANs
* **Year**: 2016

# Summary

### What
* Synthesizing high-quality images from text descriptions is a challenging problem in computer vision that was previously intractable at higher resolutions, with older methods exhibiting unstable performance beyond 64x64 without the use of additional supervision. 
* In this paper, the authors propose a method of generating photo-realistic images up to 256x256 in size by decomposing the difficult problem of image synthesis into more manageable sub-problems through a sketch-refinement process. 
* The resulting StackGAN network takes advantage of a novel conditioning augmentation technique to improve image diversity and stabilize training, ultimately achieving state of the art results on benchmark datasets.


### Main Contributions
* This paper proposes a novel stacked GAN architecture that decomposes the difficult problem of generating high-resolution images into more manageable sub-problems.
* This paper also proposes a novel conditioning augmentation technique that stabilizes CGAN training and improves the diversity of generator output, in addition to smoothing the latent conditioning manifold.
* Additionally, this paper summarizes the results of extensive qualitative and quantitative experiments that serve to measure and demonstrate the effectiveness of various components in a successful text-to-image model.


### Positive Points
* StackGAN is able to beat previous state of the art results even without the use of additional conditioning variables on location constraints, with an even larger improvement over comparable methods that don’t require external supervision.
* The resulting latent data manifolds are smooth, enabling interpolation between sentence embeddings, which could allow for more fine-tuned control over output and improved human interpretability. 


### Negative Points
* The sentence embedding models used to translate natural language descriptions into latent representations can’t be reused and must be retrained for different domains.
* StackGAN still produces relatively poor results on datasets with complexity beyond a single domain, such as MSCOCO. It is possible that the model does not have the capacity to represent such complex relationships. 






