# LOL

## [LOL: Lidar-only Odometry and Localization in 3D point cloud maps*]([https://arxiv.org/pdf/2007.01595.pdf](https://arxiv.org/pdf/2007.01595.pdf))

paper: [https://arxiv.org/pdf/2007.01595.pdf](https://arxiv.org/pdf/2007.01595.pdf)

code: https://github.com/RozDavid/LOL

### Notes:

- Lidar-only Odometry
- In this paper, it has the premade target map, so mainly it is a localization problem.

### Abstract:

- to correct the accumulated drift of the Lidar-only odometry we apply a place recognition method to detect geometrically similar locations between the online 3D point cloud and the a priori offline map.
- we integrate a state-of-the-art Lidaronly odometry algorithm with a recently proposed 3D point segment matching method
- Also, we propose additional enhancements in order to reduce the number of false matches between the online point cloud and the target map, and to refine the position estimation error whenever a good match is detected.
- Parallel a Lidar odometry and mapping algorithm is running to calculate the estimated consecutive poses from the streaming Lidar point clouds in real-time, while the global position updates are recognized against a previously known point cloud of a target map.
- Using IMU info will improve the performance. But those modules should work independently, to avoid dangerous situations from sensor malfunction.
- Using solely Lidar data has its difficulties also: a. low frequency; b. sparse points but still computationally expensive in real time

### Process:

SLAM: Place recognition → Detect loop-closure situations but all in online map(Mapping part)

This paper: Place recognition → between online and offline map

![Untitled](LOL%20efbb2d3ae6b7470fafcb260c4d6bc1e6/Untitled.png)

In case of pure Lidar odometry the LOAM algorithm scores among the highest. For the place recognition frontend we chose to integrate the SegMap.

*Just a mix of two methods, not so interesting, if needed, read more details* 

### Result:

![Untitled](LOL%20efbb2d3ae6b7470fafcb260c4d6bc1e6/Untitled%201.png)

Could decrease the accumulated error, but it is logical, cause it used the place recognition to refine the pose.

### Conclusion:

To conclude, this method solves the problem of Lidaronly odometry and localization in predefined 3D point cloud maps. Our algorithm consists of two state-of-the-art algorithms integrated in such a way to complement each other deficiencies and to highlight their advantages. Furthermore, we completed our solution with an advanced RANSAC filtering for additional certainty and ICP matching of the local- and target maps for increased precision.