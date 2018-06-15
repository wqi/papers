# Paper Details

* **Title**: 
SoundNet: Learning Sound Representations from Unlabeled Video
* **Authors**: Yusuf Aytar, Carl Vondrick, Antonio Torralba
* **Link**: [arxiv](https://arxiv.org/pdf/1610.09001.pdf)
* **Tags**: Multi-Modal Learning, Transfer Learning, Audio Recognition
* **Year**: 2016

# Summary
If you would prefer to consume this summary in a presentation format, slides are available [here](https://docs.google.com/presentation/d/1cQ3gSQvpA7UfFbvYv9KDCRH7I7LOPBvcyWLDbo73QBE/edit?usp=sharing).

## Introduction
### Motivation
* Acoustic scene classification is an important problem with a variety of real-world use cases.
* In recent years, object and speech recognition performance have been revolutionized by the emergence of massive labeled datasets.
* Unfortunately, corresponding progress in natural sound understanding has proceeded at a slower pace, in large part due to a lack of comprehensive labeled datasets.


### Problem Overview
This paper poses and seeks the answers to two questions:

1. Can we take advantage of the natural synchronization between vision and sound to acquire training data more easily?
	* Unlabeled video can be economically acquired at massive scales from online sources.
	* Acoustic representations and embeddings could be learned directly from unlabeled video.
2. Can discriminative knowledge from well-trained visual models be transferred into the audio domain?
	* Unlabeled video could act as a bridge between the visual and audio domains.


## Related Work
### Audio Recognition
* Previous work in large-scale audio understanding has been primarily focused on the tasks of music and speech recognition.
* Acoustic scene classification has largely been dominated by classical general classifiers (SVMs, GMMs) and manually crafted sound features (MFCCs, spectrograms).
* Some exploration of the relationship between vision and sound modalities has been conducted in the domain of deep learning, but in the opposite direction: producing sound from images

### Transfer Learning
* Transfer learning has been widely studied for vision tasks such as object detection, but transferring from vision to other modalities has only recently become possible with the emergence of high-performance visual models.
* Previous work in teacher-student models has explored compression of discriminative knowledge from complex models to simpler models, while attempting to retain accuracy.
* SoundNet builds upon this work, extending it beyond homogeneous input/ouput modalities.


## Method
### Dataset
* Flickr contains a wealth of short, natural, and unedited video clips that capture a variety of sounds in everyday, in-the-wild situations.
* Dataset constructed by querying for popular tags and dictionary words.
* More than 2 million videos were collected, each ranging from a few seconds to several minutes minutes in length. 
* Dataset consisted of over a year of continuous natural sound and video playback.


### Model Objective
* Student Teacher Learning
	* SOTA visual models teach SoundNet to recognize scenes and objects from corresponding audio tracks in videos.
	* Learning is jointly supervised by visual models designed for both scene and object classification.
	* For each example, teacher and student networks aim to have the same output probability distribution.
	* Downside is that SoundNet does not understand the meaning or context of the audio it is classifying, it is simply learning to reproduce output distributions from visual teacher networks.
* Loss Function
	* Utilizes KL-divergence to penalize SoundNet output distributions that differ from their visual supervisors.
	* Fully differentiable, allowing for optimization via back-propagation and SGD.


### CNN Architecture
* Convolutional Network
	* Series of 1-D convolutions followed by ReLU nonlinearities.
	* Operates directly on raw audio waveform input.
* Variable Length Input/Output
	* Fully convolutional network making use of only convolutional and pooling layers.
* Network Depth
	* Large amounts of video data enable use of deep architectures without significant overfitting.
	* 5 and 8 layer networks with 3 max-pooling layers each are explored.


### Sound Classification
* Sound categories we wish to recognize may not appear in visual content. For example, sneezing is an action that is hard to capture on video but readily apparent in audio.
* Semantic meaning can be attached to sounds with a specific strategy:
	1. Ignore output layer of network and use internal representation as feature extractor.
	2. Pick a layer in the network to use as input feature for classifier.
	3. Train a linear SVM using a small amount of labeled sound data for concepts of interest.


## Results
### Experimental Setup
* Train models for various tasks using split unlabeled training video dataset extracted from Flickr:
	* 2,000,000 training examples
	* 140,000 held-out validation examples
* Report classification accuracy of trained network on 3 different datasets:
	* DCASE - Natural sounds from 10 types of scenes, 30 seconds long
	* ESC-50 - Environmental sounds from 50 categories, 5 seconds long
	* ESC-10 - Subset of ESC-50 with only 10 categories

### Baseline Approach
* Convolutional Autoencoder for Sound:
	* Same # of layers as SoundNet: 4 encoder layers, 4 decoder layers
	* Encoder layers use same first 4 conv layers as SoundNet.
	* Decoder layers use fractionally strided convolution layers to upsample.
* Implementation Details:
	* Trained with same video dataset with MSE loss for several days.
	* Deeper autoencoders were also explored, but performed worse.

### Sound Classification Performance
* SoundNet posts SOTA results in sound classification on both ESC-10 and ESC-50, nearing human performance in some cases.
* Some common confusions include: laughing/hens, footsteps/door knocks, and insects/washing machines.
![](https://i.imgur.com/0b1lRZV.png)

### Acoustic Scene Classification Performance
* SoundNet also posts SOTA results in acoustic scene classification, beating the previous best method by 10%.
![](https://i.imgur.com/o7n3RqQ.png)

## Analysis
### Ablation Analysis
* Loss and Teacher Net 
	* KL loss performs much better than L2 loss.
	* Increased visual supervision performs better.
	* Progress in sound understanding may be furthered by building stronger vision models.
* Network Depth
	* 8 layer network performs better than 5 layer.
	* Suggests depth is helpful for sound understanding.
	* Even deeper networks may perform even better, so long as large amounts of data are available .
* Supervision
	* 5 layer network for scratch init performs better, since 8 layer overfits to small dataset.
	* Unlabeled video with more data performs better.
	* Suggests unlabeled video is a powerful signal for sound understanding.

![](https://i.imgur.com/e0Egy9M.png)

### Multi-Modal Recognition
* When comparing visual vs. audio embeddings for the task of scene classification, the authors noted that audio features contain a considerable amount of semantic information by themselves.
* However, sound does not offer much information beyond visual features, as combining visual+audio embeddings only offers a 2% improvement in performance on the scene classification task.
* Looking at t-SNE embeddings between the two types of features, it is clear that it is easier to differentiate between scenes using visual features.
![](https://i.imgur.com/LrfNAqr.png)


















