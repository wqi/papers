# Paper Details

* **Title**: Grounding of Textual Phrases in Images by Reconstruction
* **Authors**: Anna Rohrbach, Marcus Rohrbach, Ronghang Hu, Trevor Darrell, Bernt Schiele
* **Link**: [arxiv](https://arxiv.org/pdf/1511.03745.pdf)
* **Tags**: Visual Grounding, Attention
* **Year**: 2015

# Summary

### What

* Associating text phrases with visual content (grounding) is a challenging problem with many applications in the domain of HCI and information retrieval. 
* This paper proposes a novel approach to learn “grounding” by encoding phrases using a RNN language model and then learning to attend to the relevant image regions in order to reconstruct the input phrases. 
* The authors explore three types of models based on their proposed approach: unsupervised, supervised, and semi-supervised. 
* Evaluation of these models on the Flickr30k and ReferItGame datasets show significant improvements in performance over the existing state of the art.

### Main Contributions
* This paper introduces a novel approach to learn “grounding” in an unsupervised manner by encoding phrases using a RNN language model and then learning to attending to the relevant image regions, evaluating the quality of reconstruction of original input phrases.
* This paper introduces three variants of their proposed approach with varying levels of supervision, allowing for impressive improvements in accuracy with minimal labelled data. 


### Positive Points
* Of the three variants proposed, even the unsupervised model outperforms the existing state of the art. The semi-supervised model is especially efficient at exploiting the reconstruction loss, which allows it to outperform the existing state of the art consistently by a large margin.
* The proposed approach from this paper is quite general and can be extended to other tasks such as image segmentation.

### Negative Points
* The proposed approach has an especially tough time correctly grounding phrases to clothing and body parts, possibly due to confusion between people and their clothing/body parts. The authors have proposed jointly modelling phrases and adding spatial relations to improve in this area.
* The proposed approach still struggles to ground complex phrases that require strong language understanding or modelling of relations between objects, as demonstrated in their qualitative results (Figure 4).




 