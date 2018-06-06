# Paper Details

* **Title**: 
Aligning Books and Movies: Towards Story-like Visual Explanations by Watching Movies and Reading Books
* **Authors**: Yukun Zhu, Ryan Kiros, Richard Zemel, Ruslan Salakhutdinov, Raquel Urtasun, Antonio Torralba, Sanja Fidler
* **Link**: [arxiv](https://arxiv.org/pdf/1506.06724.pdf)
* **Tags**: Visual Grounding, Content Alignment
* **Year**: 2015

# Summary

### What
* This paper aims to exploit books as a source of fine-grained information that cannot be inferred from visual content alone. 
* To achieve this goal, the authors introduce a method of aligning book excerpts to their corresponding movie clips, grounding rich descriptive explanations in the visual world. 
* The proposed method utilizes sentence-level and video-text neural embeddings in combination with a context-aware CNN to combine information effectively from multiple sources. 
* Evaluation on the newly introduced MovieBook dataset consisting of 11 books and their film adaptations shows good quantitative and qualitative performance across a variety of tasks.


### Main Contributions
* This paper introduces a novel sentence similarity measure based on a neural sentence embedding trained on millions of sentences from a large corpus of books.
* This paper also proposes a simple pairwise Conditional Random Field (CRF) to smooth alignments by encouraging them to follow a linear timeline across both book and video domains.
* Finally, this paper introduces the new MovieBook dataset to evaluate performance on the book-movie alignment tasks, consisting of 11 movie/book pairs annotated with over 2000 shot-to-second correspondences.


### Positive Points
* The alignment model has several interesting real-world use cases such as allowing media consumers to switch between storytelling formats at will or advanced natural language content search for video.
* The learned sentence embedding is general and can be applied to various tasks in other domains not considered in this paper, unlike the hand-designed similarity functions from previous approaches.



### Negative Points
* When applying the trained model to the CoCoBook task described in section 5.4, the stories generated may be strongly influenced by their priors and create detail that has no supporting evidence in the input image.
* This paper evaluates alignment performance at a paragraph level, but even a “success” in terms of recall could be up to 3 paragraphs or 5 sentences away. 










