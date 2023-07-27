# SuperPoint+LightGlue

## [LightGlue: Local Feature Matching at Light Speed]([https://arxiv.org/abs/2306.13643](https://arxiv.org/abs/2306.13643))

paper: [https://arxiv.org/abs/2306.13643](https://arxiv.org/abs/2306.13643)

code: [https://github.com/cvg/LightGlue](https://github.com/cvg/LightGlue)

### Notes:

- The SuperPoint is really good in the pose estimation problem, even we do not use the SuperGlue/LightGlue but just simple distance filter we could get a good performance
- But the main point of this reading task is to find how the input shape and model shape will influence the correspondence performance.
    - So the shape only influence the SuperPoint not the Glue part
- LightGlue is really quite new and has some new innovations in Transformer especially for the spatial problem.

### Abstract:

- LightGlue(quite a new method), a deep neural network that learns to match local features across images
- SuperGlue, as with other Transformer-based models, is notoriously hard to train, requiring computing resources that are inaccessible to many practitioners.
- This is achieved by 1) predicting a set of correspondences after each computational blocks, and 2) enabling the model to introspect them and predict whether further computation is required.

### Process:

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled.png)

The feature is normalized(it is normal for a deep learning problem, for the gradient exploding problem), so the input size could be used for the feature reconstruction.

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%201.png)

**The interesting part:** **Positional encoding** is a critical part of attention as it allows addressing different elements based on their position. We note that, in projective camera geometry, the position of visual observations is equivariant w.r.t. a translation of the camera within the image plane: 2D points that stem from 3D points on the same fronto-parallel plane are translated in an identical way and their relative distance remains constant. This calls for an encoding that only captures the relative but not the absolute position of points.

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%202.png)

### Result:

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%203.png)

### Conclusion:

we combine the power of attention mechanisms with insights about the matching problem and with recent innovations in Transformer. Both its depth and width are adaptive: 1) the inference can stop at an early layer if all predictions are ready, and 2) points that are deemed not matchable are discarded early from further steps.

## [****SuperPoint: Self-Supervised Interest Point Detection and Description****]([https://arxiv.org/abs/1712.07629](https://arxiv.org/abs/1712.07629))

paper: [https://arxiv.org/abs/1712.07629](https://arxiv.org/abs/1712.07629)

code: https://github.com/rpautrat/SuperPoint

### Notes:

- The DL method to extract the keypoints and their descriptors

### Abstract:

- a self-supervised framework for training interest point detectors and descriptors
- our fully-convolutional model operates on full-sized images and jointly computes pixel-level interest point locations and associated descriptors in one forward pass
- Homographic Adaptation, a multi-scale, multihomography approach for boosting interest point detection repeatability and performing cross-domain adaptation
- The good keypoint should be stable and repeatable from different lighting conditions and viewpoints
- Instead of using human supervision to define interest points in real images, we present a self-supervised solution using self-training

### Process:

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%204.png)

Homographic Adaptation is designed to enable selfsupervised training of interest point detectors. It warps the input image multiple times to help an interest point detector see the scene from many different viewpoints and scales (see Section 5). We use Homographic Adaptation in conjunction with the MagicPoint detector to boost the performance of the detector and generate the pseudo-ground truth interest points (see Figure 2b). The resulting detections are more repeatable and fire on a larger set of stimuli; thus we named the resulting detector SuperPoint.

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%205.png)

### Result:

![Untitled](SuperPoint+LightGlue%201a2c866714a74d06a30c21c61ef84550/Untitled%206.png)

### Conclusion:

We have presented a fully-convolutional neural network architecture for interest point detection and description trained using a self-supervised domain adaptation framework called Homographic Adaptation. Our experiments demonstrate that (1) it is possible to transfer knowledge from a synthetic dataset onto real-world images, (2) sparse interest point detection and description can be cast as a single, efficient convolutional neural network, and (3) the resulting system works well for geometric computer vision matching tasks such as Homography Estimation. Future work will investigate whether Homographic Adaptation can boost the performance of models such as those used in semantic segmentation (e.g., SegNet [1] ) and object detection (e.g., SSD [14]). It will also carefully investigate the ways that interest point detection and description (and potentially other tasks) benefit each other. Lastly, we believe that our SuperPoint network can be used to tackle all visual data-association in 3D computer vision problems like SLAM and SfM, and that a learningbased Visual SLAM front-end will enable more robust applications in robotics and augmented reality.