---
layout: post
title: What should you do if training loss does not decrease? (part 1)
---

I was working on a time-series classification problem for my PhD thesis a few of months ago.
I was experimenting with a decoder-less transformer, similart to [BERT](https://arxiv.org/abs/1810.04805).
The problem was that no matter what I did, the training loss would not decrease.
I worked on this problem for almost 5 weeks.
At first, I focused on fine-tuning hyper-parameters.
My first thought was that the issue was the learning rate.
I performed a lot of study on learning rate choices and the well-known learning rate schedulers.
I was thinking that I was using an incorrect learning rate, which resulted in either skipping or failing to achieve the minima.
As shown in the image below: 

![lr-types.png]({{ site.baseurl }}/images/lr-types.png)
*source: http://www.bdhammel.com/learning-rates/*

I experimented with all of the learning rate schedulers.
I tried almost all of the schedulers in this [kaggle link](https://www.kaggle.com/code/isbhargav/guide-to-pytorch-learning-rate-scheduling/notebook). Training loss was not decreasing no matter what.
I was upset since my paper submission date had passed.
I attempted so many techniques that I may detail them in another post, but for now, I'll just focus on the solution.
I had these two lines somewhere in my pre-processing code: 

```python
X_train = shuffle_along_first_axis(X_train)
y_train = shuffle_along_first_axis(y_train)
```
where `shuffle_along_first_axis` is defined as:

```python
def shuffle_along_first_axis(arr: np.ndarray):
    arr_len = arr.shape[0]
    shuffled_indices = np.random.permutation(arr_len)
    return arr[shuffled_indices]
```

I guess you can see my error by looking at these two blocks of code. I was shuffling `X` and `y` arrays independently. As a result, the labels no longer correlate to the associated input. This critical (and dumb) error cost me nearly two months of my life. I discovered this mistake by overfitting the network with only a few samples. However, as I increased the number of samples to more than ten, the training loss stopped to decrease. So I discovered that something is wrong with my data. The problem was resolved when I removed these two lines of code, and then the network began to learn. I hope this advice will be useful to you and will help you to save some time.

### TL;DR
Always double-check your shuffling code to ensure that `X` and `y` are shuffled together.