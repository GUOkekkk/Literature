# OrienterNet

## [****OrienterNet: Visual Localization in 2D Public Maps with Neural Matching****]([https://arxiv.org/abs/2304.02009](https://arxiv.org/abs/2304.02009))

paper: [https://arxiv.org/abs/2304.02009](https://arxiv.org/abs/2304.02009)

### Notes:

- Interesting Topic: Visual Localization in 2D Map
- Do not need the 3D map to rotate the robot itself
- Just input a single image(but need a coarse GPS as prior yo give a coarse position at first), we could map it to the open-street-map and get the camera pose

### Abstract:

- OrienterNet, the first deep neural network that can localize an image with sub-meter accuracy using the same 2D semantic maps that humans use.
- To enable this, we introduce a large crowd-sourced dataset of images captured across 12 cities from the diverse viewpoints of cars, bikes, and pedestrians. OrienterNet generalizes to new datasets and pushes the state of the art in both robotics and AR scenarios.
- the first approach that can localize single images and image sequences with sub-meter accuracy given the same maps that humans use
- The estimate is probabilistic and can therefore be fused with an inaccurate GPS prior or across multiple views from a multi-camera rig or image sequences
- Key to these capabilities is a new, large-scale training dataset of images crowd-sourced from cities around the world via the Mapillary platform.

### Process:

![Untitled](OrienterNet%208ce3bfcfb5244fc3a1eaff51e5fe4cb1/Untitled.png)

![Untitled](OrienterNet%208ce3bfcfb5244fc3a1eaff51e5fe4cb1/Untitled%201.png)

### Result:

![Untitled](OrienterNet%208ce3bfcfb5244fc3a1eaff51e5fe4cb1/Untitled%202.png)

### Conclusion:

OrienterNet is the first deep neural network that can localize an image with sub-meter accuracy within the same 2D planimetric maps that humans use. OrienterNet mimics the way humans orient themselves in their environment by matching the input map with a mental map derived from visual observations. Compared to large and expensive 3D maps that machines have so far relied on, such 2D maps are extremely compact and thus finally enable on-device localization within large environments. OrienterNet is based on globally and freely available maps from OpenStreetMap and can be used by anyone to localize anywhere in the world. We contribute a large, crowd-sourced training dataset that helps the model generalize well across both driving and AR datasets. OrienterNet significantly improves over existing approaches for 3-DoF localization, pushing the state of the art by a large margin. This opens up exciting prospects for deploying power-efficient robots and AR devices that know where they are without costly cloud infrastructures.