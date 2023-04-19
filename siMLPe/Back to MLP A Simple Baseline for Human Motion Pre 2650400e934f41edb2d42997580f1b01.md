# Back to MLP: A Simple Baseline for Human Motion Prediction

Created time: April 19, 2023 10:42 AM
Last edited time: April 19, 2023 11:18 AM
Link: https://arxiv.org/abs/2207.01567
Status: Not started
Type: Paper
reviewer: Ke Guo
tags: pnp

## [Back to MLP: A Simple Baseline for Human Motion Prediction]([https://arxiv.org/abs/2207.01567](https://arxiv.org/abs/2207.01567))

### Note:

- By using a good design like Discrete Cosine Transform and the good loss function, even the small network can reach the SOTA

### Abstract:

- State-of-the-art approaches provide good results, however, they rely on deep learning architectures of arbitrary complexity, typically requiring multiple training stages and more than 2 million parameters
- In this paper, we show that, after combining with a series of standard practices, such as applying Discrete Cosine Transform (DCT), predicting residual displacement of joints and optimizing velocity as an auxiliary loss, a light-weight network based on multi-layer perceptrons (MLPs) with only 0.14 million parameters can surpass the state-of-the-art performance

### Process:

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled.png)

- DCT(Discrete Cosine Transform):

More precisely, given an input motion sequence of T frames, the DCT matrix D ∈ RT ×T can be calculated as:

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%201.png)

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%202.png)

- Loss:

Instead of predicting the absolute 3D poses from scratch, we let our network predict the residual between the future pose xT +t and the last input pose xT

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%203.png)

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%204.png)

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%205.png)

v for velocity which is computed as the time difference: vt = xt+1 − xt

### Result:

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%206.png)

- Ablation Study:

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%207.png)

![Untitled](Back%20to%20MLP%20A%20Simple%20Baseline%20for%20Human%20Motion%20Pre%202650400e934f41edb2d42997580f1b01/Untitled%208.png)

### Conclusion:

SIMLPE is composed of only fully connected layers, layer normalization, and transpose operations. The only non-linear operation is thus the layer normalization. While using much fewer parameters, SIMLPE achieves state-of-the-art performance on various benchmarks. The reported ablation study also demonstrates the interest of various design choices, highlighting the importance of temporal information fusion in this task. We hope the simplicity of SIMLPE will help the community to rethink the task of human motion prediction