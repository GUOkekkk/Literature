# USA-Net

paper:[https://arxiv.org/abs/2304.12164](https://arxiv.org/abs/2304.12164)

demo:[https://usa.bolte.cc/](https://usa.bolte.cc/)

## [**USA Net: Unified Semantic and AffordanceRepresentations for Robot Memory](**[https://arxiv.org/abs/2304.12164](https://arxiv.org/abs/2304.12164)**)**

### Notes:

- How to let the robot to follow open-ended instructions like “go open the brown cabinet over the sink” / “take this can to the kitchen”

### Abstract:

- we present USA-Net, a simple method for constructing a world representation that encodes both the semantics and spatial affordances of a scene in a differentiable map
- course-grained discrete motion planners, such as occupancy grids which use large cell sizes to conserve memory, may fail to capture fine-grained semantic information, such as small details of a scene
- USA-Net, an implicit representation which captures both semantic and affordance information, and can be used to build a high-quality motion planner for navigating to open-ended goals specified by natural language
- supervision mechanisms which leverage the supervision signal from the affordance planner to jointly supervise the semantics of empty space, giving us a semantic map which is differentiable throughout the entire scene
- we evaluate USA-Net’s gradient-based planner which achieves up to 91.2% and 39.2% higher semantic similarity and shorter trajectories, respectively, over prior discrete planners

### Process:

- Build our representation takes as input a sequence of RGB images with corresponding per-pixel depths

![Untitled](USA-Net%20dadf91e9c59b4abdb3fbc5a45263a6a7/Untitled.png)

- To supervise the affordance prediction for our world representation, we train our model to predict the Signed Distance Function (SDF)
- The SDF map:

![Untitled](USA-Net%20dadf91e9c59b4abdb3fbc5a45263a6a7/Untitled%201.png)

- Semantic representation:

![Untitled](USA-Net%20dadf91e9c59b4abdb3fbc5a45263a6a7/Untitled%202.png)

### Result:

![Untitled](USA-Net%20dadf91e9c59b4abdb3fbc5a45263a6a7/Untitled%203.png)

### Conclusion:

USA-Net allows us to build an end-to-end differentiable motion planning system for autonomous robots based on an implicit scene memory which captures both affordances and semantic information. We see that our proposed gradient-based planner can use the USA-Net representation to both better optimize arriving at semantic goals, and to generate better, shorter paths. 

One potential direction for future research is to explore more complex planning strategies by adding additional objectives to the gradient planner. While our approach is already very flexible, there may be situations where more complex planning strategies are necessary to navigate through complex environments. For example, it may be beneficial to optimize for smoother paths, as in [29]. By incorporating additional objectives into the planner, we can potentially improve the performance and efficiency of the navigation system in these situations. 

Another important direction for future work is to construct the representation while the environment is being explored. In this paper, we focused on building plans on representations that are already fully constructed. If we could construct USANet while the environment is being explored, this might even enable language-driven exploration.