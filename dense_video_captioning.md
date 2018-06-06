# Paper Details

* **Title**: Dense-Captioning Events in Videos
* **Authors**: Ranjay Krishna, Kenji Hata, Frederic Ren, Li Fei-Fei, Juan Carlos Niebles
* **Link**: [arxiv](https://arxiv.org/pdf/1705.00754.pdf)
* **Tags**: Video Captioning, Dense Captioning
* **Year**: 2017

# Summary

### What
* Most natural videos contain numerous events, but many previous approaches to captioning often lack output detail under these conditions, failing to recognize and articulate the full range of events. 
* To address this problem, this paper introduces a new model that is able to identify all events in a single pass of the video while simultaneously describing the detected events with natural language, producing significant improvements in output quality on the newly-introduced task of dense-captioning events. 
* On the ActivityNet Captions dataset, this newly introduced method also shows state of the art performance on video retrieval as well as localization.


### Main Contributions
* This paper introduces the task of dense-captioning events, which requires a model to generate a set of descriptions for multiple events in a video and localize them in time.
* This paper introduces a captioning module that can use context from past and future events output by the proposal module to generate higher quality sentences in dense-captioning tasks.
* This paper introduces the new ActivityNet Captions dataset, with 20k videos designed to evaluate the performance of dense-captioning models. 


### Positive Points
* Adding context to captioning models results in a notable improvement in output quality and can be generalized to improve performance in other related tasks such as video retrieval as well.
* The new ActivityNet Captions dataset provides an action-focused alternative to other captioning datasets and provides a great base for future research in dense-captioning.


### Negative Points
* When proposed segments in videos have high overlap, the proposed model has a tough time distinguishing between events, which can cause it to repeat captions.
* The authors report results only using traditional evaluation metrics such as BLEU, METEOR, and CIDER. It would be useful to evaluate the quality of results with human surveys. 








