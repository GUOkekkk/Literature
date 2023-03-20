# OpenLORIS-Scene Dataset

Last edited time: March 10, 2023 9:09 AM
Link: https://lifelong-robotic-vision.github.io/dataset/scene
Status: Reviewed
Type: dataset
reviewer: Ke Guo
tags: slam

### Note:

- The term, Lifelong SLAM, is interesting
- The OpenLORIS-Scene dataset aims to help evaluate the maturity of SLAM and scene understanding algorithms for real-world deployment, by providing *visual*, *inertial*and *odometry* data recorded with real robots in real scenes, and ground-truth robot trajectories acquired by motion capture system or high-resolution LiDARs. Multiple trajectories are provided for each scene, to capture scene changes caused by human activities, day-night shifts and other factors, which are crucial to address for long-term robot autonomy
- New metrics:

![Untitled](OpenLORIS-Scene%20Dataset%20efcd2356c22544e6bf3499996270dd1e/Untitled.png)

### Result:

- Under some situations, the IMU could strongly keep the performance

![Untitled](OpenLORIS-Scene%20Dataset%20efcd2356c22544e6bf3499996270dd1e/Untitled%201.png)