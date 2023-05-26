# SCoRe Forest for Camera Relocalization

## [Scene Coordinate Regression Forests for Camera Relocalization in RGB-D Images]([https://openaccess.thecvf.com/content_cvpr_2013/papers/Shotton_Scene_Coordinate_Regression_2013_CVPR_paper.pdf](https://openaccess.thecvf.com/content_cvpr_2013/papers/Shotton_Scene_Coordinate_Regression_2013_CVPR_paper.pdf))

paper: [https://openaccess.thecvf.com/content_cvpr_2013/papers/Shotton_Scene_Coordinate_Regression_2013_CVPR_paper.pdf](https://openaccess.thecvf.com/content_cvpr_2013/papers/Shotton_Scene_Coordinate_Regression_2013_CVPR_paper.pdf)

### Notes:

- No need for the keypoints descriptors
- need to know the 3D scene in advance

### Abstract:

- Inferring the pose of an RGB-D camera relative to a known 3D scene given only a single acquired image
- Only simple depth and RGB pixel comparison features are used by the regression forest
- The camera pose is inferred using a robust optimization scheme
- Preemptive RANSAC then iterates sampling more pixels at which to evaluate the forest, counting inliers, and refining the hypothesized poses.

### Process:

- **Regression Forests:**
    
    A regression forest is an ensemble of T decision trees, each consisting of split (internal) and leaf nodes. 
    
- **Preemptive RANSAC:**

![Untitled](SCoRe%20Forest%20for%20Camera%20Relocalization%20b3c45bcce7884e21988d05d5310f0cc4/Untitled.png)

![Untitled](SCoRe%20Forest%20for%20Camera%20Relocalization%20b3c45bcce7884e21988d05d5310f0cc4/Untitled%201.png)

![Untitled](SCoRe%20Forest%20for%20Camera%20Relocalization%20b3c45bcce7884e21988d05d5310f0cc4/Untitled%202.png)

### Result:

![Untitled](SCoRe%20Forest%20for%20Camera%20Relocalization%20b3c45bcce7884e21988d05d5310f0cc4/Untitled%203.png)

### Conclusion:

We have demonstrated how scene coordinate regression forests (SCoRe Forests) can be trained to directly predict correspondences between image pixels and a scene’s world space. For known environments, SCoRe Forests thus offer an alternative to the traditional pipeline of sparse feature detection, description, and matching. Our efficient RANSAC optimization is able to sparsely sample image pixels at which to evaluate the forest. The comparison on the challenging new 7 Scenes dataset with two baselines indicates that our algorithm achieves state of the art camera relocalization. As future work we believe that our approach will extend very naturally to RGB-only test images. We also plan to investigate sampling additional training data by rendering new views from 3D scene reconstructions. Finally, we hope that an optimized implementation could be extended to support on-line model learning and relocalization.