# PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation

Last edited time: March 20, 2023 11:44 AM
Link: https://arxiv.org/abs/1612.00593
Status: In progress
Type: Paper
reviewer: Ke Guo
tags: pnp

****PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation****

### Note:

- Deal with the problem that the permutation invariance of points in the input
- a network that consumes N 3D point sets needs to be invariant to N
- In order to make a model invariant to input permutation, three strategies exist: 1) sort input into a canonical order; 2) treat the input as a sequence to train an RNN, but augment the training data by all kinds of permutations; 3) use a simple symmetric function to aggregate the information from each point.