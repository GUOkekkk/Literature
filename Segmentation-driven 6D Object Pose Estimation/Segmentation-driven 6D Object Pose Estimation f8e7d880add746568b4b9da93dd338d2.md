# Segmentation-driven 6D Object Pose Estimation

Created time: May 9, 2023 2:32 PM
Last edited time: May 11, 2023 11:47 AM
Link: https://arxiv.org/abs/1812.02541
Status: In progress
Type: Paper
reviewer: Ke Guo
tags: DL, pnp

## [Segmentation-driven 6D Object Pose Estimation]([https://arxiv.org/abs/1812.02541](https://arxiv.org/abs/1812.02541))

### Notes:

- Could we use the 6D pose of the fixed object to get the camera pose? But the generalization ability is important
- Use [YCB_video]([https://paperswithcode.com/dataset/ycb-video](https://paperswithcode.com/dataset/ycb-video)) for the object 6D pose estimation
- [PoseCNN]([https://arxiv.org/abs/1711.00199](https://arxiv.org/abs/1711.00199)) seems better, it uses a pure CNN network instead of using DL+PnP(this paper)

### Abstract:

- we introduce a segmentation-driven 6D pose estimation framework where each visible part of the objects contributes a local pose prediction in the form of 2D keypoint locations. We then use a predicted measure of confidence to combine these pose candidates into a robust set of 3D-to-2D correspondences.
- our approach deals well with multiple poorly-textured objects occluding each other

### Process:

- We assume the objects to be rigid and their 3D model to be available.
- For the encoder, we use the Darknet-53 architecture of YOLOv3 which has proven highly effective and efficient for objection detection. For the decoders, we designed networks that output 3D tensors of spatial resolution S × S and feature dimensions Dseg and Dreg, respectively.

![Untitled](Segmentation-driven%206D%20Object%20Pose%20Estimation%20f8e7d880add746568b4b9da93dd338d2/Untitled.png)

- The size of the cell of the feature map is big
- In practice, we do not predict directly the keypoints’ 2D coordinates. Instead, for each one, we predict an offset vector with respect to the center of the corresponding grid cell, as illustrated by Fig. 3(b)

![Untitled](Segmentation-driven%206D%20Object%20Pose%20Estimation%20f8e7d880add746568b4b9da93dd338d2/Untitled%201.png)

![Untitled](Segmentation-driven%206D%20Object%20Pose%20Estimation%20f8e7d880add746568b4b9da93dd338d2/Untitled%202.png)

- In fact, this network only predicts the 2d keypoints(8 corners of the object) and their 3D position and then uses the RANSACPnP

### Result:

![Untitled](Segmentation-driven%206D%20Object%20Pose%20Estimation%20f8e7d880add746568b4b9da93dd338d2/Untitled%203.png)

- It seems to have a better performance than PoseCNN, but for me, PoseCNN is actually a real end-to-end 6D pose estimation. But the model generalization ability is a crucial problem for the transformation from object pose estimation to camera pose estimation.

### Conclusion:

We have introduced a segmentation-driven approach to 6D object pose estimation, which jointly detects multiple objects and estimates their pose. By combining multiple local pose estimates in a robust fashion, our approach produces accurate results without the need for a refinement step, even in the presence of large occlusions. Our experiments on two challenging datasets have shown that our approach outperforms the state of the art, and, as opposed to the best competitors, predicts the pose of multiple objects in real time.