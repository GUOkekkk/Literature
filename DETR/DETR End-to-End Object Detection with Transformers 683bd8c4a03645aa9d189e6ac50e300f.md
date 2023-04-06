# DETR: End-to-End Object Detection with Transformers

Created time: March 30, 2023 5:01 PM
Last edited time: March 31, 2023 1:47 PM
Link: https://arxiv.org/abs/2005.12872
Status: Reviewed
Type: Paper
reviewer: Ke Guo
tags: DL

## [DETR: End-to-End Object Detection with Transformers]([https://arxiv.org/abs/2005.12872](https://arxiv.org/abs/2005.12872))

CODE: [https://github.com/facebookresearch/detr](https://github.com/facebookresearch/detr).

### Notes:

- Use the Transformer on the image object detection, which I think is somewhat similar to the PnP problem, especially for the 2D position encoding part!

### Abstract:

- views object detection as a direct set prediction problem
- the new framework, called DEtection TRansformer or DETR, are a set-based global loss that forces unique predictions via bipartite matching, and a transformer encoder-decoder architecture
- DETR can be easily generalized to produce panoptic segmentation in a unified manner
- Compared to most previous work on direct set prediction, the main features of DETR are the conjunction of the bipartite matching loss and transformers with (non-autoregressive) parallel decoding

### Process:

- Object detection set prediction loss: forces unique matching between predicted and ground truth:
    
    (This part is not interesting for us)
    

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled.png)

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%201.png)

- DETR architecture:

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%202.png)

- 2D Position Encoding:

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%203.png)

### Result:

- DETR for object detection:

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%204.png)

- DETR for panoptic segmentation:

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%205.png)

- Visualize the attention:

![Untitled](DETR%20End-to-End%20Object%20Detection%20with%20Transformers%20683bd8c4a03645aa9d189e6ac50e300f/Untitled%206.png)

### Conclusion:

We presented DETR, a new design for object detection systems based on transformers and bipartite matching loss for direct set prediction. The approach achieves comparable results to an optimized Faster R-CNN baseline on the challenging COCO dataset. DETR is straightforward to implement and has a flexible architecture that is easily extensible to panoptic segmentation, with competitive results. In addition, it achieves significantly better performance on large objects than Faster R-CNN, likely thanks to the processing of global information performed by the self-attention. This new design for detectors also comes with new challenges, in particular regarding training, optimization and performances on small objects. Current detectors required several years of improvements to cope with similar issues, and we expect future work to successfully address them for DETR.