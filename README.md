# PLS-based Pruning

This repository contains an independent implementation of PLS-based pruning method that is inspired by the paper proposed in:

[Pruning Deep Neural Networks using Partial Least Squares](https://arxiv.org/abs/1810.07610)

It is an iterative method that trains a convolutional neural network (CNN), computes the importance of each filter using the Partial Least Squares (PLS) and the Variable Importance in Projection (VIP) and, then, prunes the least important layers before fine-tuning the model.

As shown in the paper, the same approach could be applied to different datasets (CIFAR10, ImageNet, etc.) and using state-of-the-art architectures (i.e., ResNet). As the idea here is just to demonstrate how the method can be used in practice, we will just use the MNIST database and very simple CNN. In particular, the proposed CNN has three convolutional layers (16, 32 and 64 filters, respectively) and is followed by ReLU and MaxPooling. 

Similar to the authors, we also apply a global pooling operation to convert a mxm filter into a single value that is used in the PLS to compute the filter importance. We evaluate two approaches, the global max and average pooling. 

Finally, we used as a baseline the simple L1-norm of the filter as a proxy for the feature importance.

Table 1. # parameters / accuracy before and after using the pruning for 5 iterations
Approach | Before | After |
     --- |    --- |   --- | 
PLS (Avg) | 23,946 / 0.9785 | 5,799 / 0.9835 |
PLS (Max) | 23,946 / 0.9785 | 8,340 / 0.9826 | 
L1-Norm | 23,946 / 0.9785 | 9,671 / 0.9646 | 