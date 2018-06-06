# Paper Details

* **Title**: Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks
* **Authors**: Jun-Yan Zhu, Taesung Park, Phillip Isola, Alexei A. Efros 
* **Link**: [arxiv](https://arxiv.org/pdf/1703.10593.pdf)
* **Tags**: Image-to-Image Translation, GANs
* **Year**: 2017

# Summary

### What
* Image-to-image translation is a class of vision and graphics problems with the goal of learning a mapping between an input domain and an output domain, often using a training set of aligned image pairs. 
* In some tasks, paired data can be difficult or even impossible to obtain. 
* This paper aims to address this issue by presenting an approach for unsupervised image-to-image translation that takes advantage of adversarial and cycle consistency loss to create realistic images in highly under-constrained situations. 
* In evaluation on a variety of image translation tasks, the proposed CycleGAN outperforms existing methods, nearing the performance of supervised approaches in some cases. 



### Main Contributions
* This paper introduces the CycleGAN method, capable of capturing the characteristics of one image collection and determining how these characteristics can be translated into a different image collection, all without the use of any paired training examples.
* This paper demonstrates how cycle-consistency can be exploited to reduce the space of possible mapping functions, in addition to reducing training instability and preventing the occurrence of mode collapse.



### Positive Points
* Looking at the quantitative results, CycleGAN takes a significant step forward and produces images that are closer in quality to the best supervised image-to-image translation method (Pix2Pix) than previous unsupervised methods.
* Unlike previous work, CycleGAN does not rely on task-specific, predefined similarity functions or assume that the input and output have to lie in the same low-dimensional embedding space.


### Negative Points
* In some tasks such as photo->map, the image output from CycleGAN is still clearly nonsensical, with curved lines for roads and intersections that don’t line up, as the model has no semantic understanding of visual content and context.
* Translations performed on images that appear in the training set still produce output that is often more appealing than that from test data, a fact that is more evident when browsing the online supplementary material than in the provided figures.









