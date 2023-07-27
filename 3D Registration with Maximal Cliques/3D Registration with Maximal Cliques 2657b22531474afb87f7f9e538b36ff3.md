# 3D Registration with Maximal Cliques

## [3D Registration with Maximal Cliques]([https://arxiv.org/abs/2305.10854](https://arxiv.org/abs/2305.10854))

paper: [https://arxiv.org/abs/2305.10854](https://arxiv.org/abs/2305.10854)

code: [https://github.com/zhangxy0517/3D-Registration-with-Maximal-Cliques](https://github.com/zhangxy0517/3D-Registration-with-Maximal-Cliques)

### Notes:

- Maybe it could be used to improve the VO accuracy
- some hyper-paras might be difficult to choose
- there are some interesting features in this paper like Harris3D and fully convolutional geometric features

### Abstract:

- we present a 3D registration method with maximal cliques (MAC).
- MAC effectively increases registration accuracy, outperforms various state-of-the-art methods and boosts the performance of deep-learned methods. MAC combined with deep-learned methods achieves stateof-the-art registration recall of 95.7% / 78.9% on 3DMatch / 3DLoMatch.
- Using point-to-point feature correspondences is a popular and robust solution to the PCR problem. But feature matching usually contains outliers, resulting in great challenges to accurate 3D registration.
- Classical Methods: Although RANSAC-based methods are simple and efficient, their performance is highly vulnerable when the outlier rate increases, and it requires a large number of iterations to obtain acceptable results.
- DL Methods: investigating more discriminate keypoint feature descriptors or more effective correspondence selection techniques, but deep-learned based methods require a large amount of data for training and usually lack generalization on different datasets
- we propose a geometric-only 3D registration method based on maximal cliques (MAC)
- Compared with the maximum clique, MAC is a looser constraint and is able to mine more local information in a graph.
- The best hypothesis is selected to perform registration using popular hypothesis evaluation metrics in the RANSAC family

### Process:

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%201.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%202.png)

The graph space can more accurately depict the affinity relationship between correspondences than the Euclidean space. Therefore, we model the initial correspondences as a compatibility graph where correspondences are represented by nodes and edges link nodes that are geometrically compatible.

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%203.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%204.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%205.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%206.png)

the maximum clique is a very tight constraint that only focuses on the global consensus information in a graph. Instead, we loosen the constraint and leverage maximal cliques to mine more local graph information.

Calculate the weight of the clique to reduce the number of maximal cliques. And a node could be included by multiple maximal cliques and we only retain the one with the greatest weight.

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%207.png)

Here, we propose several techniques to further filter the maximal cliques

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%208.png)

### Result:

Not sure if this metric is too loose:

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%209.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%2010.png)

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%2011.png)

Ablation Studies:

![Untitled](3D%20Registration%20with%20Maximal%20Cliques%202657b22531474afb87f7f9e538b36ff3/Untitled%2012.png)

### Conclusion:

In this paper, we presented MAC to solve PCR by using the maximal clique constraint to generate precise pose hypotheses from correspondences. Our method achieves state-of-the-art performance on all tested datasets and can adapt to deep-learned methods to boost their performance. 

Limitation. Sometimes MAC produces accurate hypotheses but may fail to find them.