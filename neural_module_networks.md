# Paper Details

* **Title**: Deep Compositional Question Answering with Neural Module Networks
* **Authors**: Jacob Andreas, Marcus Rohrbach, Trevor Darrell, Dan Klein
* **Link**: [arxiv](https://arxiv.org/pdf/1511.02799.pdf)
* **Tags**: Visual Question Answering, Modular Networks
* **Year**: 2015

# Summary

### What
* Visual question answering is a task that is fundamentally compositional in nature, with many questions sharing similar substructure. 
* This property is exploited by the authors of this paper through their proposed “neural module network” (NMN), which composes collections of jointly-trained neural “modules” into deep networks for question answering. 
* The proposed approach decomposes questions into their linguistic substructures and uses these structures to dynamically instantiate compound module networks. 
* This proves to be a highly effective strategy, with NMNs beating out previous approaches on the VQA natural image dataset and achieving state of the art results on a newly introduced dataset of complex questions about abstract shapes.



### Main Contributions
* This paper introduces NMNs, a general architecture for discretely composing jointly-trained neural modules into deep networks.
* This paper shows how NMNs can be constructed from the output of a semantic parser, achieving state of the art performance in visual question answering tasks.
* This paper also introduces a new dataset of challenging, highly compositional questions about abstract shapes that is more complex than previous benchmarks.



### Positive Points
* The proposed approach to visual question answering produces an intermediate output of layouts from natural language questions, improving transparency and making it easier for humans to understand what the model is learning.
* One especially interesting implication of neural “modules” is that they can be used to construct a form of SQL with visual understanding, creating powerful real-world use cases.


### Negative Points
* While outperforming existing methods overall, NMNs are not better in every category and have been shown to perform worse on yes/no questions due to overfitting.
* With only 8 instances in the newly introduced SHAPES dataset, it may be too simple to fully evaluate a model’s ability to recognize objects of various classes.







