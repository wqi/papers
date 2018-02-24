# Paper Details

* **Title**: Towards Diverse and Natural Image Descriptions via a Conditional GAN
* **Authors**: Bo Dai, Sanja Fidler, Raquel Urtasun, Dahua Lin
* **Link**: [https://arxiv.org/pdf/1703.06029.pdf](https://arxiv.org/pdf/1703.06029.pdf)
* **Tags**: Image Captioning, GANs
* **Year**: 2017

# Summary

### What

  * Captions produced by existing state of the art methods (such as those based on RNNs) are often overly rigid and lack variability, caused by MLE encouraging resemblance to "ground-truth" captions and suppressing other reasonable descriptions.
  * This paper proposes a new framework based on conditional generative adversarial networks (CGAN), which jointly learns a generator to produce captions conditioned on image encodings and a discriminator to assess how well a caption fits the visual content.
  * This paper also overcomes difficulties (vanishing gradients, error propagation) associated with training a GAN for sequence generation by using policy gradient to allow the generator to receive early feedback.
  * When testing the proposed method on two large datasets (MSCOCO and Flickr30k), it performed competitively in their user study against captions from real people and outperformed other methods with regards to semantic relevance, naturalness, and diversity of captions.
  
![Fig8](img/cgan_captioning/1.png?raw=true "Fig8")

### How

  * Overall formulation contains two separate networks:
  	![Fig4](img/cgan_captioning/4.png?raw=true "Fig4")
	1. Generator *G*: 
		* Takes two inputs: an image feature *f(I)* derived from a CNN (VGG16 	   in this case) and a random vector *z* used to introduce diversity in the output.
		* With *f(I)* and *z* as initial conditions, uses a LSTM net as a decoder to generate 		  sentences word by word.
		* Objective is to generate descriptions that are natural, i.e. indistinguishable from 		  what humans would say when presented with the same image.
	2. Evaluator *E*: 
		* Given an image *I* and a caption *S*, evaluates the quality of the description.
		* Has the same structure as *G*, but parameters are not tied with each other.
		* Objective is to distinguish between artificial descriptions (those from *G*) and real 		  ones from humans (from the training set).
  * Training *G* can be difficult, so the proposed method makes use of several clever tricks:
	  * Policy Gradient:
		  * Production of sentences is a discrete sampling process, which is generally			 *nondifferentiable*.
		  * Policy gradient, a technique from reinforcement learning, allows us to consider a 			 sentence as a sequence of actions, where choosing each word is an action.
		  * At each step, the policy takes the initial conditions and preceding words as inputs, 			 outputting a conditional distribution over the extended vocabulary.
		  * The reward of this sequence of actions is the score given by evaluator *E*.
		  * Using policy gradients, the generator becomes trainable with gradient descent.
	  * Early Feedback:
		  * One problem with policy gradient is that the reward can only be evaluated once a 			 sentence is completely generated, which could lead to *vanishing gradients* and 			 *slow convergence*.
		  * At intermediate time steps, an *expected future reward* is computed while the 			 sentence is partially generated, with expected output being approximated using 			 *Monte Carlo rollouts*.
		  * Providing early feedback to *G* along the way substantially improves the 			 effectiveness of the training process.
  * The loss function is tuned to encourage naturalness and relevance of caption outputs, with 	 adjustable weights for each term to empirically fine-tune the contribution of each 	 criteria on validation sets.

### Results
  * Datasets:
	  * Flickr30k
	  * MSCOCO
  * User Study:
	  * 30 human evaluators asked to choose the better caption for a particular image, given 	    two choices, 3000 total responses were collected.
	  * Proposed *G-GAN* from this paper is better than previous *G-MLE* in **61%** of cases.
	  * *G-MLE* better than human captions **9%** of cases, while *G-GAN* was much more 		 effective, winning over **24%** of the time.

	  ![Fig5](img/cgan_captioning/3.png?raw=true "Fig3")
  * Qualitative Comparison:
	  * *G-MLE* tends to generate descriptions that are almost the same when presented with 		 similar images, very little variation in structure is observed in the output.
	  * *G-GAN* produces captions with much more distinction and diversity, especially when *z* 	    is varied.
	  ![Fig6](img/cgan_captioning/2.png?raw=true "Fig6")
  * Failure Analysis:
	  * Analysis of failure cases showed that inclusion of incorrect details such as colors 		 (red/yellow hat) and counts (three/four people) were a common source of error
	  * A possible cause proposed is that because there are only a few samples for each 		particular details, there aren't enough training examples to allow the generator to 		capture these details reliably.
	  * Another proposed cause is that the focus on diversity and overall quality of 		captions may be encouraging the generator to include more details, taking the risk 		some details being incorrect.


