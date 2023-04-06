# End-to-End Learnable Geometric Vision by Backpropagating PnP Optimization#

Created time: March 23, 2023 1:01 PM
Last edited time: March 28, 2023 10:43 AM
Link: https://arxiv.org/abs/1909.06043
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

## [End-to-End Learnable Geometric Vision by Backpropagating PnP Optimization]([https://arxiv.org/abs/1909.06043](https://arxiv.org/abs/1909.06043))

### Note:

- CODE: https://github.com/BoChenYS/BPnP
- Two methodso to incorporate a geometric optimization solver in a deep learning architecture
    1. Differentiable RANSAC
        
        [Dsac-differentiable ransac for camera localization. In CVPR, 2017]([https://arxiv.org/abs/1611.05705](https://arxiv.org/abs/1611.05705))
        
        [Expert sample consensus applied to camera re-localization]([https://arxiv.org/abs/1908.02484](https://arxiv.org/abs/1908.02484))
        
        [Neural-guided ransac: Learning where to sample model hypotheses]([https://arxiv.org/abs/1905.04132](https://arxiv.org/abs/1905.04132))
        
    2. Derive gradients from an independent optimization block for backpropagation learning
        
        [Optnet: Differentiable optimization as a layer in neural networks]([https://arxiv.org/abs/1703.00443](https://arxiv.org/abs/1703.00443))
        
        [On differentiating parameterized argmin and argmax problems with application to bi-level optimization]([https://arxiv.org/abs/1607.05447](https://arxiv.org/abs/1607.05447))
        

### Abstract:

- BPnP, a novel network module that backpropagates gradients through a Perspective-nPoints (PnP) solver to guide parameter updates of a neural network
- Based on implicit differentiation, we show that the gradients of a “self-contained” PnP solver can be derived accurately and efficiently, as if the optimizer block were a differentiable function
- Since our approach can be extended to other optimization problems, our work helps to pave the way to perform learnable geometric vision in a principled manner.

### Process:

![Untitled](End-to-End%20Learnable%20Geometric%20Vision%20by%20Backpropa%2046d03f19f72d40479518ce27abbb23c2/Untitled.png)

![Untitled](End-to-End%20Learnable%20Geometric%20Vision%20by%20Backpropa%2046d03f19f72d40479518ce27abbb23c2/Untitled%201.png)

![Untitled](End-to-End%20Learnable%20Geometric%20Vision%20by%20Backpropa%2046d03f19f72d40479518ce27abbb23c2/Untitled%202.png)

### Result:

![Untitled](End-to-End%20Learnable%20Geometric%20Vision%20by%20Backpropa%2046d03f19f72d40479518ce27abbb23c2/Untitled%203.png)

![Untitled](End-to-End%20Learnable%20Geometric%20Vision%20by%20Backpropa%2046d03f19f72d40479518ce27abbb23c2/Untitled%204.png)

### Conclusion:

BPnP leverages on implicit differentiation to address computing the non-explicit gradient of this geometric optimization process.  We developed an end-to-end trainable object pose estimation pipeline with BPnP, which outperforms the current state-of-the-art. Our experiments show that exploiting 2D-3D geometry constraints improves the performance of a feature-based training scheme. The proposed BPnP opens a door to vast possibilities for designing new models. We believe the ability to incorporate geometric optimization in end-to-end pipelines will further boost the learning power and promote innovations in various computer vision tasks.