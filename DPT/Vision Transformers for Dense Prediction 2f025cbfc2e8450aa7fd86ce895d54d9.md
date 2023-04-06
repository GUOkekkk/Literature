# Vision Transformers for Dense Prediction

Created time: March 31, 2023 3:34 PM
Last edited time: April 4, 2023 9:21 AM
Link: https://arxiv.org/abs/2103.13413
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL

## Vision Transformers for Dense Prediction([https://arxiv.org/abs/2103.13413](https://arxiv.org/abs/2103.13413))

### Note:

- A good example for how to use multi transformers to solve an image based problem

### Abstract:

- dense vision transformers: an architecture that leverages vision transformers in place of convolutional networks as a backbone for dense prediction tasks
- assemble tokens from various stages of the vision transformer into image-like representations
- Our experiments show that this architecture yields substantial improvements on dense prediction tasks, especially when a large amount of training data is available

### Process:

- use the vision transformer (ViT) as a backbone architecture, combine the feature representations into the final dense prediction using a convolutional decoder
- Since transformers are set-to-set functions, they do not intrinsically retain the information of the spatial positions of individual tokens. The image embeddings are thus concatenated with a learnable position embedding to add this information to the representation. The ViT additionally adds a special token that is not grounded in the input image and serves as the final, global image representation which is used for classification

![Untitled](Vision%20Transformers%20for%20Dense%20Prediction%202f025cbfc2e8450aa7fd86ce895d54d9/Untitled.png)

- ViT-Base, which uses the patch-based embedding procedure and features 12 transformer layers;
- ViT-Large, which uses the same embedding procedure and has 24 transformer layers and a wider feature size D;
- ViT-Hybrid, which employs a ResNet50 to compute the image embedding followed by 12 transformer layers.

Convolutional Decoder:

The feature representations are progressively fused into the final dense prediction. We propose a simple three-stage Reassemble operation to recover image-like representations from the output tokens of arbitrary layers of the transformer encoder:

![Untitled](Vision%20Transformers%20for%20Dense%20Prediction%202f025cbfc2e8450aa7fd86ce895d54d9/Untitled%201.png)

### Result:

![Untitled](Vision%20Transformers%20for%20Dense%20Prediction%202f025cbfc2e8450aa7fd86ce895d54d9/Untitled%202.png)

### Conclusion:

We have introduced the dense prediction transformer, DPT, a neural network architecture that effectively leverages vision transformers for dense prediction tasks. Our experiments on monocular depth estimation and semantic segmentation show that the presented architecture produces more fine-grained and globally coherent predictions when compared to fully-convolutional architectures. Similar to prior work on transformers, DPT unfolds its full potential when trained on large-scale datasets.