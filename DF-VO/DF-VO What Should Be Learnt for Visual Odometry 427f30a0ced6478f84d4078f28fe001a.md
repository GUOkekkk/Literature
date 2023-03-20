# DF-VO: What Should Be Learnt for Visual Odometry?

Last edited time: March 9, 2023 2:49 PM
Link: https://arxiv.org/abs/2103.00933
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

## [DF-VO: What Should Be Learnt for Visual Odometry?]([https://arxiv.org/abs/2103.00933](https://arxiv.org/abs/2103.00933))

### Note:

- two alternative trackers(VO and PnP) out of which one is selected by the data-driven model selection module
- Mainly use the VO(Epipolar Geometry), depth information for the scale recovery, PnP-tracker is used as an auxiliary tracker when E-tracker tends to fail
- Interesting correspondence selection(Best-N selection & Local best-K selection), could be interesting for us to filter the bad matches
- Use self-supervised learning is interesting

### Abstact:

- Monocular VO suffer from scale-drift issue
- Deep neural networks can learn scene depths and relative camera in a self-supervised manner without acquiring ground truth labels
- By integrating multi-view geometry and deep learning on Depth and optical Flow
- a) we propose a method to carefully sample high-quality correspondences from deep flows and recover accurate camera poses with a geometric module; b) we address the scaledrift issue by aligning geometrically triangulated depths to the scale-consistent deep depths, where the dynamic scenes are taken into account.

### Process:

![Untitled](DF-VO%20What%20Should%20Be%20Learnt%20for%20Visual%20Odometry%20427f30a0ced6478f84d4078f28fe001a/Untitled.png)

### Result:

![Untitled](DF-VO%20What%20Should%20Be%20Learnt%20for%20Visual%20Odometry%20427f30a0ced6478f84d4078f28fe001a/Untitled%201.png)

### Conclusion:

- Integrating deep predictions with geometry gain the best from both domain
- show that a local optimization module is useful to further improve the VO result, which can be a future direction to improve our VO system