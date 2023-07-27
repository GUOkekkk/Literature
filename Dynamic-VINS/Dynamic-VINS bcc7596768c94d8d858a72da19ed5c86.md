# Dynamic-VINS

## [RGB-D Inertial Odometry for a Resource-restricted Robot in Dynamic Environments]([https://ieeexplore.ieee.org/document/9830851](https://ieeexplore.ieee.org/document/9830851))

paper: [https://ieeexplore.ieee.org/document/9830851](https://ieeexplore.ieee.org/document/9830851)

code: 

[https://github.com/HITSZ-NRSL/Dynamic-VINS](https://github.com/HITSZ-NRSL/Dynamic-VINS)

### Notes:

- we do not have the IMU, but the feature extraction and filter of dynamic environments

### Abstract:

- SLAM performs well in static environments but easily fails in dynamic environments
- This paper proposes a real-time RGB-D inertial odometry system for resource-restricted robots in dynamic environments named Dynamic-VINS
- three threads run in parallel: 1. object detection 2. feature tracking 3. state optimization
- Dynamic-VINS adopts grid-based feature detection and proposes a fast and efficient method to extract high-quality FAST feature points.
- Reduce dynamic objects’ influence on the estimation results consciously

### Process:

a realtime RGB-D inertial odometry for resource-restricted robots

![Untitled](Dynamic-VINS%20bcc7596768c94d8d858a72da19ed5c86/Untitled.png)

For efficiency, three main threads (surrounded by dash lines) run parallel.

- In the feature tracking thread, features are tracked with the help of IMU preintegration and detected by grid-based feature detection.
- The object detection thread detects dynamic objects in each frame in real-time
- Then, the state optimization thread will summarize the features information, object detection results, and depth image to recognize the dynamic features. A missed detection compensation module is conducted in case of missed detection. The moving consistency check procedure combines the IMU preintegration and historical pose estimation results to identify potential dynamic features. Finally, stable features and IMU preintegration results are used for the pose estimation. And the propagation of the IMU is responsible for an IMU-rate pose estimation result. Loop closure is also supported in this system, but this paper pays more attention to the localization independent of loop closure.

### Result:

![Untitled](Dynamic-VINS%20bcc7596768c94d8d858a72da19ed5c86/Untitled%201.png)

### Conclusion:

This paper presents a real-time RGB-D inertial odometry for resource-restricted robots in dynamic environments. Costefficient feature tracking and detection methods are proposed to cut down the computing burden. A lightweight object-detection-based method is introduced to deal with dynamic features in real-time. Validation experiments show the proposed system’s competitive accuracy, robustness, and efficiency in dynamic environments. Furthermore, DynamicVINS is able to run on resource-restricted platforms to output an instant pose estimation. In the future, the proposed approaches are expected to be validated on the existing popular SLAM frameworks. The missed detection compensation module is expected to develop into a moving object tracking module, and semantic information will be further introduced for high-level guidance on mobile robots or mobile devices in complex dynamic environments.