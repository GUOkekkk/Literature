# Detector-Free SfM

## [Detector-Free Structure from Motion]([https://arxiv.org/abs/2306.15669](https://arxiv.org/abs/2306.15669))

paper: [https://arxiv.org/abs/2306.15669](https://arxiv.org/abs/2306.15669)

code: https://github.com/zju3dv/DetectorFreeSfM

### Notes:

- Maybe it could be used to improve the indoor VO(especially with low texture information)
- SfM has open-source systems such as Bundler [47] and COLMAP
- Eliminating the keypoint detection phase can help avoid poor detection affecting the overall SfM system and benefit the reconstruction of challenging texture-poor scenes.

### Abstract:

- We propose a new structure-from-motion framework to recover accurate camera poses and point clouds from **unordered images**
- Traditional **detector-based SfM** is difficult for **texture-poor scenes**
- our framework first reconstructs **a coarse SfM** model from **quantized detector-free matches**.
- Then, it refines the model by a novel iterative refinement pipeline, which **iterates between an attention-based multi-view matching module to refine feature tracks** and a **geometry refinement module to improve the reconstruction accuracy.**
- Detector-free matchers have shown a strong capability for matching lowtextured regions with the help of the detector-free design and the attention mechanism. They often use a coarseto-fine matching strategy for efficiency
- Problem: This pair-dependent nature leads to fragmentary feature tracks when running pair-wise matching over multiple views, which makes detector-free matchers not directly applicable to existing SfM systems

### Process:

- To solve the inconsistency issue of detector-free matching, our SfM framework reconstructs the scene in a coarse-to-fine manner, which first builds a coarse SfM model with the quantized matches, and then iteratively refines the model towards higher accuracy.
- Specifically:
1. First matches image pairs with a detector-free feature matcher, e.g., LoFTR. 
2. In the coarse reconstruction phase, we quantize the feature locations by rounding them into a coarse grid to improve consistency and reconstruct a coarse SfM model. This coarse model provides initial camera poses and scene structures for the later refinement phase.
3. Next, we propose an iterative refinement pipeline that alternates between a feature track refinement phase and a geometry refinement phase to improve pose and point cloud accuracy.
4. The feature track refinement module is built on a novel transformer-based multi-view matching network, which enhances the discrimitiveness of extracted features by encoding positional and multi-view context with self- and cross-attention mechanisms

![Untitled](Detector-Free%20SfM%20feaac8be846d49458cf89c8a0e099aef/Untitled.png)

![Untitled](Detector-Free%20SfM%20feaac8be846d49458cf89c8a0e099aef/Untitled%201.png)

- Quantization: Force multiple subpixel matches that are close to each other to merge into a single grid node
- Multi-View Matcher:

![Untitled](Detector-Free%20SfM%20feaac8be846d49458cf89c8a0e099aef/Untitled%202.png)

### Result:

![Untitled](Detector-Free%20SfM%20feaac8be846d49458cf89c8a0e099aef/Untitled%203.png)

### Conclusion:

We propose a new detector-free SfM framework to recover camera poses and point clouds from unordered images. In contrast to traditional SfM systems that depend on keypoint detection at the beginning, our framework leverages the recent success of detector-free matchers to avoid early determination of keypoints which may break down the whole SfM system if the detected keypoints are not repeatable, which often occur in challenging texture-poor scenes. Extensive experiments demonstrate that our framework outperforms detector-based SfM baselines across all datasets and metrics.  **But** the overall mapping phase will be inevitably slower than the previous detector-based pipelines, especially on large-scale scenes