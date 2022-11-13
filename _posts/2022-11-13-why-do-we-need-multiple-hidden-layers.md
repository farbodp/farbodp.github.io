---
layout: post
title: Why do we need multiple hidden layers?
---

The logic behind stacking multiple layers in deep neural networks is not clear yet. But there are a few strong reasons that we can explain. First reason is that by increasing the number of layers (depth of the network), the size of each layer (width of each layer) decreases. In other words, for a fixed accuracy, we need much more neurons in a shallow network compared to a deep, low-width network. So instead of one big shallow network with many neurons, we can have an efficient deep network with fewer neurons. Two below figures are from the [Deep Learning](https://www.deeplearningbook.org/) (2015) Book by Aaron Courville, Ian Goodfellow, and Yoshua Bengio:

![depth_acc.png]({{ site.baseurl }}/images/depth_acc.png)

![acc_params.png]({{ site.baseurl }}/images/acc_params.png)

As you can see in Fig 6.6, as the number of layers increases, test set accuracy increases for a fixed layer width. However, this is not the case for layer width, as one can see in Fig 6.7. It can be seen that increasing the layer width is not as effective as increasing the depth. Based on these two figures, we can conclude that stacking multiple layers is a very effective tradition in deep learning. It helps with the generalization ability of the model and reduces the overfitting.
The second reason is that we can get more high-level features in deep neural networks. Feature extraction in deep learning works in a hierarchical manner. As an example, we can consider object detection in CNNs. In CNNs, first convolution layers extract low-level features such as edges. Then in the deeper layers, more complex and high-level features such as objects are extracted. In a sense, multiple layers act as filters that denoise the input images and extract the relevant information.

To summarize, we can say that stacking multiple layers in deep learning have the following advantages:

1. Increase the network accuracy in an efficient manner (compared to shallow networks).
2. Reduce overfitting by increasing the generalization ability of the model.
3. Extract high-level features in a hierarchical manner.
4. Act as filters and denoise inputs
<!-- Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub. -->