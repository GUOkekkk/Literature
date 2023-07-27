# UniAD

## [Planning-oriented Autonomous Driving]([https://arxiv.org/abs/2212.10156](https://arxiv.org/abs/2212.10156))

paper: [https://arxiv.org/abs/2212.10156](https://arxiv.org/abs/2212.10156)

demo: [https://opendrivelab.github.io/UniAD/](https://opendrivelab.github.io/UniAD/)

code: https://github.com/OpenDriveLab/UniAD

### Note:

- CVPR 2023 Best Paper
- Two old methods:
    - a. standalone multi-modules → it bares the risk of information loss across modules, error accumulation and feature misalignment due to the isolation of optimization target
    - b. a shared feature extractor and several task-specific heads → However, such a scheme may cause undesirable “negative transfer
- This method:  end-to-end autonomous driving unites all nodes. The choice and priority of preceding tasks should be determined in favor of planning. But end-to-en is inadequate in safety guarantee and interpretability.

### Abstract:

- Modern autonomous driving system is characterized as modular tasks in sequential order, i.e., perception, prediction, and planning. But they might suffer from accumulative errors or deficient task coordination.
- Planning of the self-driving car is the ultimate goal
- We introduce Unified Autonomous Driving (UniAD), a comprehensive framework up-to-date that incorporates full-stack driving tasks in one network.
- Tasks are communicated with unified query interfaces

### Process:

![Untitled](UniAD%20462a2abdf52f43f4a4fc358bbfb6e0b2/Untitled.png)

A key component is the query-based design to connect all nodes. Compared to the classic bounding box representation, queries benefit from a larger receptive field to soften the compounding error from upstream predictions. The key component to hit the ground running is the query design as interfaces connecting all nodes.

![Untitled](UniAD%20462a2abdf52f43f4a4fc358bbfb6e0b2/Untitled%201.png)

UniAD comprises four transformer decoder-based perception and prediction modules and one planner in the end.

- Specifically, a sequence of multi-camera images is fed into the feature extractor, and the resulting perspective-view features are transformed into a unified bird’s-eye-view (BEV) feature B by an off-the-shelf BEV encoder in BEVFormer
- In TrackFormer, the learnable embeddings that we refer to as track queries inquire about the agents’ information from B to detect and track agents
- MapFormer takes map queries as semantic abstractions of road elements (e.g., lanes and dividers) and performs panoptic segmentation of the map.
- MotionFormer captures interactions among agents and maps and forecasts per-agent future trajectories. This module makes joint predictions for all agents considered. Meanwhile, we devise an ego-vehicle query to explicitly model the ego-vehicle and enable it to interact with other agents in such a scene centric paradigm.
- OccFormer employs the BEV feature B as queries, equipped with agent-wise knowledge as keys and values, and predicts multi-step future occupancy with agent identity preserved.
- Planner utilizes the expressive ego-vehicle query from MotionFormer to predict the planning result, and keep itself away from occupied regions predicted by OccFormer to avoid collisions.

Shared matching. Since UniAD involves instance-wise modeling, pairing predictions to the ground truth set is required in perception and prediction tasks. Similar to DETR [8, 56], the bipartite matching algorithm is adopted in the tracking and online mapping stage. As for tracking, candidates from detection queries are paired with newborn ground truth objects, and predictions from track queries inherit the assignment from previous frames. The matching results in the tracking module are reused in motion and occupancy nodes to consistently model agents from historical tracks to future motions in the end-to-end framework.

### Result:

![Untitled](UniAD%20462a2abdf52f43f4a4fc358bbfb6e0b2/Untitled%202.png)

### Conclusion:

We discuss the system-level design for the autonomous driving algorithm framework. A planning-oriented pipeline is proposed toward the ultimate pursuit for planning, namely UniAD. We provide detailed analyses on the necessity of each module within perception and prediction. To unify tasks, a query-based design is proposed to connect all nodes in UniAD, benefiting from richer representations for agent interaction in the environment. Extensive experiments verify the proposed method in all aspects. Limitations and future work. Coordinating such a comprehensive system with multiple tasks is non-trivial and needs extensive computational power, especially trained with temporal history. How to devise and curate the system for a lightweight deployment deserves future exploration. Moreover, whether or not to incorporate more tasks such as depth estimation, behavior prediction, and how to embed them into the system, are worthy future directions as well.