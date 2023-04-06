# Coarse- and Fine-grained Attention Network with Background-aware Loss for Crowd Density Map Estimation

Created time: March 28, 2023 10:42 AM
Last edited time: March 28, 2023 12:58 PM
Link: https://arxiv.org/abs/2011.03721
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL, attention

## [Coarse- and Fine-grained Attention Network with Background-aware Loss for Crowd Density Map Estimation]([https://arxiv.org/abs/2011.03721](https://arxiv.org/abs/2011.03721))

### Note:

- To Learn what is the coarse attention, but actually it just created a coarse attention map based on the CNN instead of using attention mechanism. But, the coarse-to-fine, this architecture is good to learn.

### Abstract:

- a novel method Coarse- and Fine-grained Attention Network (CFANet) for generating high-quality crowd density maps and people count estimation
- from-coarse-to-fine progressive attention mechanism
- Crowd Region Recognizer (CRR) + Density Level Estimator (DLE) + a multi-level supervision mechanism(for backpropagation of gradient)
- not only outperform previous state-of-the-art methods in terms of count accuracy but also improve the image quality of density maps as well as reduce the false recognition ratio.

### Process:

- Attention map(assign attention weights to regions with different density.): in one attention map, the background area has a weight close to 0, and the low-density area has relatively low weights, and the high-density area has relatively high weights
- Background-aware Structural Loss (BSL): take account of structural similarity, counting accuracy and false recognition ratio

![Untitled](Coarse-%20and%20Fine-grained%20Attention%20Network%20with%20Ba%203f5ee2f5614146a5aefd675b97961682/Untitled.png)

### Result:

![Untitled](Coarse-%20and%20Fine-grained%20Attention%20Network%20with%20Ba%203f5ee2f5614146a5aefd675b97961682/Untitled%201.png)

### Conclusion:

In this paper, we present a new model named Coarse- and Fine-grained Attention Network (CFANet) for high-quality crowd density map generation and people counting. By incorporating Crowd Region Recognizer (CRR) and Density Level Estimator (DLE) to estimate coarse- and finegrained attention maps, feature maps for regressing the density maps are refined on multi-scale and the network can better focus on the crowd region. We also adopt multilevel supervision to help facilitate the backpropagation of gradient and reduce overfitting. In addition, we propose a novel and effective loss function named Background-aware Structural Loss (BSL), which can achieve better counting accuracy and enhance structural similarity as well as reduce false recognition ratio. Combining proposed CFANet with BSL can outperform current state-of-the-art methods on most mainly used datasets.