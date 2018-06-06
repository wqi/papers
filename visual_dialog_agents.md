# Paper Details

* **Title**: Learning Cooperative Visual Dialog Agents with Deep Reinforcement Learning
* **Authors**: Abhishek Das, Satwik Kottur, José M. F. Moura, Stefan Lee, Dhruv Batra
* **Link**: [arxiv](https://arxiv.org/pdf/1703.06585.pdf)
* **Tags**: Deep Reinforcement Learning, Visual Question Answering, Dialog Agents
* **Year**: 2017

# Summary

### What

* This paper aims to develop agents that can understand visual content and communicate their understanding using natural language. 
* To achieve this goal, the authors pose a cooperative “image guessing” game between two agents – Q-Bot and A-Bot who communicate in natural language dialog so that Q-Bot can select an unseen image from a lineup of images. 
* Using deep reinforcement learning, the policies of these agents are learned end-to-end, simulating a potentially unlimited number of game plays along the way. 
* Evaluation in large-scale real-image experiments show significant performance improvements over the existing methods, with RL agents producing exchanges that are less repetitive and more image-discriminative.


### Main Contributions
* This paper introduces the first goal-driven training method for visual question answering dialog agents, improving upon previous work based on supervised learning.
* Using images from a simple synthetic world, the authors demonstrate the automatic emergence of grounded language and communication among visual dialog agents with no human supervision.
* The authors show that introducing RL to the training process results in significant performance improvements over agents trained in a strictly supervised manner.


### Positive Points
* While the supervised Q-Bot simply learns to mimic the questions that humans ask, the RL trained Q-Bot shifts strategies and asks questions that A-Bot is better at answering. This leads to more informative dialog and better synergy.
* The interactions between RL-trained agents are more diverse, less prone to repetitive and safe exchanges that don’t carry meaningful information and are shown to be more image-discriminative.
* The “guessing game” posed by the authors does not require any bounding box annotations and reward/error can be computed by simple Euclidean distance, allowing for an unlimited number of game plays to be simulated.


### Negative Points
* While less prone to getting stuck in infinite repeating dialog loops, this issue nonetheless still affects the RL agents, albeit at slightly longer intervals
* RL agents are also still affected by “forgetfulness”, the observed phenomenon where performance of agents becomes worse after several rounds, even though more information is strictly available.





