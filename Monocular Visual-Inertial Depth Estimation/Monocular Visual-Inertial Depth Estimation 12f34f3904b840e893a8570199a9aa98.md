# Monocular Visual-Inertial Depth Estimation

# Monocular Visual-Inertial Depth Estimation[[https://arxiv.org/abs/2303.12134](https://arxiv.org/abs/2303.12134)]

paper: [https://arxiv.org/abs/2303.12134](https://arxiv.org/abs/2303.12134)

code: https://github.com/isl-org/VI-Depth

### Notes:

- Depth Estimation is useful for 3D Vision(ICP or PnP also we need a good backend, only use frontend, it is very hard to get a promising result)
- Align no-scale monocular depth to scale VIO(triangulation features based on camera pose) by using Global Alignment(least-squares) and Local Alignment(Learning-Based)

### Abstract:

- a visual-inertial depth estimation pipeline that integrates monocular depth estimation and visual-inertial odometry to produce dense depth estimates with metric scale
- Our approach performs global scale and shift alignment against sparse metric depth
- We demonstrate successful zero-shot transfer from synthetic TartanAir to real-world VOID data and perform generalization tests on NYUv2 and VCU-RVI.
- However, monocular approaches that rely solely on visual data still exhibit scale ambiguity. Incorporating inertial data can help resolve scale ambiguity, and most mobile devices already contain inertial measurement units (IMUs).
- fully-dense metrically accurate depth predictions
- We seek to bridge these approaches by leveraging monocular depth estimation models trained on diverse datasets and recovering metric scale for individual depth estimates.
- Our pipeline is modular and is agnostic to the monocular depth estimation model and VIO system being used; it should thus benefit from continual improvement in these modules. → It means this method is the bridge between the monocular depth estimation.

### Process:

We develop a modular three-stage pipeline for visual-inertial depth estimation.

![Untitled](Monocular%20Visual-Inertial%20Depth%20Estimation%2012f34f3904b840e893a8570199a9aa98/Untitled.png)

**Global scale Alignment:** 

Each depth frame from Monocular Depth Estimator is no-scale, therefore, use a global scare and global shift on the depth frame, the value is from least-squares by depth frame and VIO sparse depth keypoints. 

**Local scale Alignment:** 

The region within the convex hull defined by the anchors is filled via linear interpolation of anchor values. (Dense the sparse VO depth keypoints map)

![Untitled](Monocular%20Visual-Inertial%20Depth%20Estimation%2012f34f3904b840e893a8570199a9aa98/Untitled%201.png)

### Result:

![Untitled](Monocular%20Visual-Inertial%20Depth%20Estimation%2012f34f3904b840e893a8570199a9aa98/Untitled%202.png)

### Conclusion:

![Untitled](Monocular%20Visual-Inertial%20Depth%20Estimation%2012f34f3904b840e893a8570199a9aa98/Untitled%203.png)