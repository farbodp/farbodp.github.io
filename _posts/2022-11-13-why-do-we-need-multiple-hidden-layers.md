---
layout: post
title: Why do we need multiple hidden layers?
---

Deep neural networks stack numerous hidden layers, although the reasoning behind this is yet unclear. However, there are a few strong arguments that we can accept. The first reason is that as the network's depth (number of layers) increases, each layer's width (size) decreases. In other words, a shallow network requires significantly more neurons for a fixed accuracy than a deep, low-width network. Therefore, we can have an efficient and equally-effective deep network with fewer neurons rather than a large shallow network with many neurons. The following two images are taken from the book [Deep Learning](https://www.deeplearningbook.org/) by Aaron Courville, Ian Goodfellow, and Yoshua Bengio (2015):

![depth_acc.png]({{ site.baseurl }}/images/depth_acc.png)

![acc_params.png]({{ site.baseurl }}/images/acc_params.png)

As shown in Fig. 6.6, the number of layers increases test set accuracy for a certain layer width.
This is not the case for layer width, as seen in Fig 6.7.
As can be seen, increasing the layer width does not have the same impact as increasing the depth.
Based on these two figures, we can conclude that stacking several layers is a highly effective deep learning tradition.
It improves the model's generalization capabilities and lowers overfitting.

The second reason is that deep neural networks can provide more high-level features. Deep learning feature extraction operates in a hierarchical fashion. Consider object detection in CNNs as an example. The earliest convolution layers in CNNs extract low-level characteristics such as edges. The deeper layers extract more complicated and high-level features, such as objects. Multiple layers operate as filters, reducing noise from the input pictures and extracting useful information.

To recap, stacking numerous layers in deep learning has the following benefits:

1. Improve network accuracy in a cost-effective manner (compared to shallow networks).
2. Reduce overfitting by improving the model's generalization capability.
3. Hierarchically extract high-level features.
4. Act as filters and reduce noise from inputs.