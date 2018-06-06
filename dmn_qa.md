# Paper Details

* **Title**: Dynamic Memory Networks for Visual and Textual Question Answering
* **Authors**: Caiming Xiong, Stephen Merity, Richard Socher
* **Link**: [arxiv](https://arxiv.org/pdf/1603.01417.pdf)
* **Tags**: Visual Question Answering, Textual Question Answering, Dynamic Memory Networks
* **Year**: 2016

# Summary

### What
* In past work, neural network architectures with memory and attention mechanisms have exhibited high accuracy in a variety of language tasks. 
* However, it was not shown if this performance could be reproduced when supporting facts are not explicitly marked during training or whether the architecture could be transferred to other modalities such as images. 
* To address these questions, this paper analyzes the dynamic memory network (DMN) architecture and proposes several improvements to its memory and input modules, enabling improved performance in VQA tasks. 
* These changes prove to be quite effective, with evaluation of the newly proposed DMN+ model on the bAbI-10k and VQA datasets showing state of the arts results in both visual and text question-answering tasks.


### Main Contributions
* This paper proposes a new input module for the DMN architecture, which uses a sentence-level encoder and input fusion layer to improve information flow between sentences.
* This paper also proposes a change to the memory component of DMN, using a modified GRU that incorporates attention gates that are computed using global knowledge over facts.
* Lastly, this paper demonstrates how the DMN architecture can be applied for the VQA task, introducing a new input module to represent images.


### Positive Points
* The proposed DMN+ model no longer requires the facts that are relevant for answering a particular question to be labelled during training, instead learning to select the important facts from a larger set.
* Because DMN+ no longer uses a word-level embedding, opting for sentence-level embedding combined with a fusion layer, facts in distant supporting sentences have more direct interaction.



### Negative Points
* One deficiency noted by the authors with DMN+ is that the choice of a more complex memory update component could prevent convergence on certain simpler tasks, with increased error observed in some cases.
* An additional deficiency noted was that visual tasks involving counting could prove difficult for DMN-based approaches as it would be difficult to resolve object that cross image patch boundaries.







