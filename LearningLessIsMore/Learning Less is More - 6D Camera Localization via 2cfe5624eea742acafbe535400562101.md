# Learning Less is More - 6D Camera Localization via 3D Surface Regression

Last edited time: March 9, 2023 10:25 AM
Link: https://www.semanticscholar.org/paper/Learning-Less-is-More-6D-Camera-Localization-via-3D-Brachmann-Rother/6ca43ff71b3c0039e7feb6e0b9fc7cf5d779e535
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

## [****Learning Less is More - 6D Camera Localization via 3D Surface Regression****]([https://www.semanticscholar.org/paper/Learning-Less-is-More-6D-Camera-Localization-via-3D-Brachmann-Rother/6ca43ff71b3c0039e7feb6e0b9fc7cf5d779e535](https://www.semanticscholar.org/paper/Learning-Less-is-More-6D-Camera-Localization-via-3D-Brachmann-Rother/6ca43ff71b3c0039e7feb6e0b9fc7cf5d779e535))

### Notes:

- The main contribution of this paper is to only use one CNN network to get the scene coordinates  and give a new score function. But about how to calculate the pose of the camera, they still use the classical PnP, but the score function part is what I think is interesting.

### Abstract:

- Address the task of predicting the 6D camera pose from a single RGB image in a given 3D environment.
- The key contribution is to demonstrate and explain that learning a single component of this pipeline is sufficient.
- Using scene coordinates and the whole process inspired by [DSAC]([https://arxiv.org/abs/1611.05705](https://arxiv.org/abs/1611.05705))([https://arxiv.org/abs/2002.12324](https://arxiv.org/abs/2002.12324)) but a new score function;
- Interestingly, our approach surpasses existing techniques even without utilizing a 3D model of the scene during training, since the network is able to discover 3D scene geometry automatically, solely from single-view constraints

### Prcoess:

- Scene Coordinate Regression
- Pose Hypothesis Sampling(Generate a pool of hypotheses.)
- Hypothesis Selection

Use the softmax function, where h is the pose hypothesis:

![Untitled](Learning%20Less%20is%20More%20-%206D%20Camera%20Localization%20via%202cfe5624eea742acafbe535400562101/Untitled.png)

- Hypothesis Refinement

### Reuslt:

![Untitled](Learning%20Less%20is%20More%20-%206D%20Camera%20Localization%20via%202cfe5624eea742acafbe535400562101/Untitled%201.png)

### Conclusion:

The system can learn from small training sets, and still generalize well to unseen views. Training can utilize a 3D scene model, or discover scene geometry automatically. Our method scales to large outdoor scenes but fails on city-scale scenes like the challenging Cambridge Street scene