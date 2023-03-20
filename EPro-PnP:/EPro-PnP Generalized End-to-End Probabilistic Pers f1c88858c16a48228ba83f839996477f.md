# EPro-PnP: Generalized End-to-End Probabilistic Perspective-n-Points for Monocular Object Pose Estimation

Last edited time: March 20, 2023 3:17 PM
Link: https://arxiv.org/abs/2203.13254
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

I first discovered my passion in computer graphics and image processing as a hobbyist 3D artist obsessed with 3D modeling, rendering, game modding, and later photography. From my own experience
I learned the significance of advanced algorithms in freeing people’s creativity and reducing human
labor in the digital world, which now motivates me to take the role of a researcher.

## [EPro-PnP: Generalized End-to-End Probabilistic Perspective-n-Points for Monocular Object Pose Estimation]([https://arxiv.org/abs/2203.13254](https://arxiv.org/abs/2203.13254))

### Note:

- Although this paper is for the object pose estimation not the camera pose, but the discuss of the PNP and deep learning is worth to learn.
- Interpreting PnP as a differentiable layer to add it be a part of the deep learning model.

### Abstract:

- EPro-PnP, a probabilistic PnP layer for general end-to-end pose estimation, which outputs a distribution of pose on the SE(3) manifold, essentially bringing categorical Softmax to the continuous domain.
- Closing the gap between PnP-based method and the taskspecific leaders on the LineMOD 6DoF pose estimation and nuScenes 3D object detection benchmark

### Process:

- Deterministic pose is non-differentiable, but the probability density of pose is apparently differentiable, just like categorical classification scores

![Untitled](EPro-PnP%20Generalized%20End-to-End%20Probabilistic%20Pers%20f1c88858c16a48228ba83f839996477f/Untitled.png)

- the Kullback-Leibler (KL) divergence between the predicted and target pose distributions is minimized as the loss function which can be efficiently implemented by the Adaptive Multiple Importance Sampling algorithm.
- Moreover, just like the attention mechanism, the corresponding weights can be trained to automatically focus on important point pairs, allowing the networks to be designed with inspiration from attention-related work.
- The balance between uncertainty and discrimination enables locating important correspondences in an attention-like manner. This inspires us to take elements from attention-related work

### Result:

![Untitled](EPro-PnP%20Generalized%20End-to-End%20Probabilistic%20Pers%20f1c88858c16a48228ba83f839996477f/Untitled%201.png)

### Conlusion:

For application, EPro-PnP can inspire novel solutions such as the deformable correspondence, or it can be simply integrated into existing PnP-based networks. Beyond the PnP problem, the underlying principles are theoretically generalizable to other learning models with nested optimization layer, known as declarative networks