# Paper Details

* **Title**: Don't Decay The Learning Rate, Increase The Batch Size
* **Authors**: Samuel L. Smith, Pieter-Jan Kindermans & Quoc V. Le
* **Link**: https://arxiv.org/pdf/1711.00489.pdf
* **Tags**: CNN Training, Machine Learning, Computer Vision
* **Year**: 2017

# Summary

### What

  * This paper shows that it is possible to obtain the same learning curve on training and test sets by increasing batch size during training, instead of decaying the learning rate.
  * This paper also presents techniques for making use of vast batch sizes without hyper-parameter tuning to significantly reduce the number of parameter updates required during training.
  * The technique is shown to be generalizable across optimizers and demonstrated to be effective on SGD, SGD with momentum, Nesterov momentum, and Adam.
  * It reaches similar test accuracies after the same number of training epochs, but requires much fewer parameter updates, leading to shorter overall training time.
  * The number of parameter updates can be further reduced by increasing the learning rate and momentum, accompanied with a proportional change in batch size.
  * Inception-ResNet-V2 can be trained on ImageNet to 77% validation accuracy in under 2500 parameter updates, utilizing large training batches of 65536 images.

  
### How

  * Traditionally, the learning rate is reduced in order to achieve reduction in noise scale. However, we can achieve the same reduction in noise scale at a *constant learning rate* by increasing the batch size instead.
  * An efficient training procedure is to increase batch size at a constant rate until B ~ N/10, then reverting to decaying learning rates.
  * Previous work has proposed that the number of parameter updates required for training could be reduced by increasing learning rate and momentum coefficient while simulaneously scaling B. Empirically, it was found in this paper that this slightly reduces the final test set accuracy.
  * When training with high momentum, additional training epochs should be introduced to allow the dynamics to catch up.
  * Since this issue arises every time the noise scale *g* is changed, the authors recommend that one only increases the momentum as a method of last resort, after first identifying the largest stable learning rate.

### Results
* **Simulated Annealing on a Wide ResNet**
  	* Experiments performed on CIFAR-10 using a 16-4 wide ResNet architecture
  	* Three implementations explored:
  		1. Decaying learning rate
			* Constant batch size
			* Learning rate decays by factor of 5 at each step
  		2. Hybrid
  			* Batch size increase by factor of 5 at first step, constant afterwards
  			* Constant learning rate at first step, decays by factor of 5 at subsequent steps
  			* Mimics training procedure on VRAM limited systems
  		3. Increasing batch size
  			* Batch size increases by factor of 5 at each step
  			* Constant learning rate
	* When plotting test set accuracy after each epoch, all three schedules exhibited indistinguishable plots, showing that reduction of learning rate is unnecessary as long as noise scale is reduced.![Plot of performance with different schedules.](https://i.imgur.com/JDL4rts.png)
	* However, when plotting test set accuracy vs. number of parameter updates, it is clear that increasing the batch size has a significant advantage over reducing the learning rate.

* **Increasing The Effective Learning Rate**
	* When training with the original scheulde, ~80000 updates were required to reach a final test accuracy of 94.3%.
	* Increasing batch size in the schedule reduced the number of updates to ~29000 with a final accuracy of 94.4%.
	* Increasing initial learning rate in addition to increasing batch size resulted in under 64500 updates with a final accuracy of 94.5%.
	* Combining increased momentum coefficient with both increasing learning rate as well as batch size can reduce the number of updates to less than 2500, but suffers in test accuracy at 93.3%.
	* It is clear that the final schedule had not converged within the 90 epochs allocated, as explained in the "How" section above. 
	* ![Plot of performance with different schedules.](https://i.imgur.com/8JzhWqV.png)



