# DSAC: Differentiable RANSAC for Camera Localization

Last edited time: March 9, 2023 10:34 AM
Link: https://arxiv.org/abs/1611.05705
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

## [DSAC: Differentiable RANSAC for Camera Localization]([https://arxiv.org/abs/1611.05705](https://arxiv.org/abs/1611.05705))

### Note:

- This team already proposed a new method, but this idea to transfer the RANSAC to a differentiable layer to the deeplearning model is heuristic.

### Abstract:

- RANSAC hypothesis selection procedure is non-differentiable.
- By reinforcement learning, namely to replace the deterministic hypothesis selection by a probabilistic selection for which we can derive the expected loss.
- We demonstrate that by directly minimizing the expected loss of the output camera poses, robustly estimated by RANSAC, we achieve an increase in accuracy.

### Process:

- Generate a pool of hypotheses
- Score hypotheses
- Select best hypothesis

Probabilistic Selection (DSAC):

Where parameters v influence the selection directly via the scoring function s(h, Y ; v), and parameters w influence the quality of competing hypotheses h

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled.png)

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled%201.png)

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled%202.png)

- Refine hypothesis

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled%203.png)

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled%204.png)

### Result:

![Untitled](DSAC%20Differentiable%20RANSAC%20for%20Camera%20Localization%202e154499c73c4618beab17d474940ff8/Untitled%205.png)

### Conlusion:

DSAC can be deployed in any deep learning pipeline where robust optimization is beneficial, for example learning structure from motion or SLAM end-to-end.