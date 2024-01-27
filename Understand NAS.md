# Neural Architecture Search

## Definition

Basically, it is applying **automatic machine learning pipeline** to **search the optimal neural network** based architecture for certain problems.

## Basic Concept of NAS
### Search Space

The search space of NAS is the space which present all the **architecture and parameters** can be used as candidates during the searching process. 

For the architecture type, take block type for example, we can have residual block, IBN block or indentity blocks as candidate when we build the search space.

For the parameter type, take channel number for certain block type for example, we can choose different values to build up different blocks when we build the search space.

Another thing worth mention is that for specific task type, you can create unique type of search space. For example, for object detection NAS, you can take output feature map number
value as different architecture type in your search space.

### Search Strategy

After we define the search space, it is important to **find the optimal architecture correctly and efficiently**. Thus, different search strategy has been developed for different tasks.

The details for different search strategy will be written in different files in the **TODO**

### Evaluation
- **Evaluation During NAS**: During the search process, there is an evaluation process for current architecture to generate a metric which is reported to the NAS system to decide how good this architecture is. 

- **Final Architecture Evaluation**: When the search ended, there will be another round of final full evaluation with the optimal NN architecture during the search. 

## Basic Type of NAS
### Multi Trial NAS
- **Search Space**: Different body part choices of a neural network, could be blocks type choice, layer parameters choice, or number of layers. For each trial, it will generate a different model and evaluate from that.[1]
- **Search Strategy**: Because each trial is independent, after some random sampled architecture is searched and evaluated, the optimization methods will choose the architecture with the best metrics and resample from there as a starting points.
  - Possible Search Strategy:
    - **Random Search**
    - **Grid Search**
    - **Evolution Search**
    - **Policy Based RL Search**
- **Total Search Efficiency**: The total time(*T*) is depending on the number of trials(*N*), the time for single trial(*t*) and max concurrency(*C*)
  - In general, *T = N * t / C*
### One Shot NAS
- **Search Space**: Most One Shot NAS exists one super model and the search space. The search space is the sub model space of the super model which contains different operators in the suprt model[2]
- **Search Strategy**: For we have a super model and try to search the sub space, most optimization method is based on graph optimization.
  - **TODO: Introduce different search strategies**
- **Total Search Efficiency**: With different optimization methods, it is hard to compute the exact efficiency but generally it is said to be more efficient than Multi Trial NAS for the total time for achieving the similar performance for the final architecture(See [3] to peek the interesting efficiency)
## Pros and Cons of NAS
### Advantage
**TODO**
### Disadvantage
**TODO**

## CheckList
- This is important for anyone who want to develop NAS related project, it contains a lot of relative questions: https://www.automl.org/wp-content/uploads/NAS/NAS_checklist.pdf
## Reference
[1] Ren, P., Xiao, Y., Chang, X., Huang, P. Y., Li, Z., Chen, X., & Wang, X. (2021). *A comprehensive survey of neural architecture search: Challenges and solutions.* ACM Computing Surveys (CSUR), 54(4), 1-34.

[2] Xiao, Y., Qiu, Y., & Li, X. (2020, February). *A survey on one-shot neural architecture search.* In IOP Conference Series: Materials Science and Engineering (Vol. 750, No. 1, p. 012223). IOP Publishing.

[3] Liu, H., Simonyan, K., & Yang, Y. (2018). *Darts: Differentiable architecture search.* arXiv preprint arXiv:1806.09055.
