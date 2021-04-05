---
title: 'DETR: DEtection TRansformer'
excerpt: You only look once? I do not even have to look. A popular application of Transformer in computer vision. 
index_img: /img/DETR/elephant.png
banner_img: /img/DETR/cows.png
date: 2021-04-04 23:55:48
tags: [Paper reading]
math: true
mermaid: true
comment: disqus
---

# Introduction
Before reading this article, you may have a look at my previous article [^2]["Transformer? Attention!"](https://blog.yunfeizhao.com/2021/03/31/attention/) in which I explain "Attention mechanism" and "The Transformer". Early in 2020, Facebook AI proposed a new way to use the Transformer in object detection task in paper [^1]["End-to-End Object Detection with Transformers"](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123460205.pdf)  in which they present a new method that view object detection as a direct set prediction problem.  For now, it only has its basic version that means that it still has quite a lot of potential and can be optimized. However, it has already significantly outperformed competitive baselines for accuracy and run-time. 

There are four special characteristics for this model:

1. DETR predicts all objects at once,  and is trained end-to-end.
2. DETR does not have multiple hand-designed components that encode prior knowledge, like sliding window, spatial anchors, non-maximal suppression, large set of proposals, or window centers.
3. DETR does not require any customized layers, and thus can be reproduced easily in any framework that conatins standard CNN and transformer classes.
4. DETR can be easily generalized to produce panoptic segmentation in a unified manner.

Training code and pretrained models are available at ["End-to-End Object Detection with Transformers"](https://github.com/facebookresearch/detr).

# Model Architecture

[^1] ["End-to-End Object Detection with Transformers"](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123460205.pdf)

<p align="center">
<img src="/img/DETR/detr_architecture.png" alt="DETR directly predicts (in parallel) the final set of detections by combining a common CNN with a transformer architecture. During training, bipartite matching uniquely assigns predictions with ground truth boxes. Prediction with no match should yield a “no object” (∅) class prediction.
" style="width:800px;">
</p>

The overall DETR architecture is surprisingly simple. It contains three main components.

1. A CNN backbone to extract a compact feature representation.
2. An encoder-decoder transformer.
3. A simple feed forward network(FFN) that makes the final detection prediction.

## Backbone

Starting from the initial image $x_{img}\in R^{3\times H_0\times W_0}$(with 3 color channels) and All imput image are batched together, applying 0-padding adequately to ensure they all have the same dimensions ($H_0, W_0$) as the largest image of the batch. The conventional CNN backbone generats a lower-resolution activation map $f\in R^{C\times H\times W}$ as a **set of image features**. The dimensions of this feature map are $C = 2048$ and $H,W = \frac{H_0}{frac}, \frac{W_0}{frac}$ where **frac** is 32 for DETR and 16 for DETR DC5.

## Transformer encoder

Each encoder layer has a standard architecture ([^3] ["Attention is all you need"](https://arxiv.org/abs/1706.03762))and consist of a multi-head self-attention module and a feed forward network (FFN). The encoder follows the following steps:

1. Use a $1\times1$ convolutional kernal to reduces the channel dimension of the high-level activation map $f$ of dimension $R^{C\times H\times W} $ to a new feature map $z_0$ of dimension $R^{d\times H\times W}$ where $d$ is smaller than $C$.
2. Collapse $z_0$ into one dimension, resulting in a $d\times HW$ feature map which is the input sequence for the encoder.
3. The transformer architecture is permutation-invariant, we supplement it with fixed **positional encodings** that are added to the input of **each attention layer**.

## Transformer decoder

The decoder follows the standard architecture of the transformer too, transforming $N$ embeddings of size $d$ using multi-headed self- and encoder-decoder attention mechanism.  To be noted that this model decodes the $N$ objects in parallel at each decoder layer(not autoregressive). Since the decoder is permutation-invariant, the N input embeddings must be different to produce different results. These input embeddings are **learnt positional encodings** that we refer to as ***Object Queries***. These queries are added to the input of each attention layer similarly to the encoder.

It follows the following steps:

1. The $N$ object queries are transformed into an output embedding by the decoder.
2. The output embeddings are independent decoded into box coordinates and class labels by a **feed forward network**, resulting N final predictions.

Using self- and encoder-decoder attention over these embeddings, the model globally reasons about all objects together using **pair-wise relations between them**, while being able to use **the whole image as context**.

## Prediction feed-forward networks(FFNs)



# Citation

```
@article{zhao_DETR2021, 
    title={DETR: DEtection TRansformer}, 
    url={https://blog.yunfeizhao.com/2021/04/04/DETR/}, 
    journal={https://blog.yunfeizhao.com/}, 
    author={ZHAO, Yunfei}, year={2021}, month={Mar}}
```

<iframe src="https://gitcdn.link/repo/YunfeiZHAO/blog/main/donation_unit/index.html" style="overflow-x:hidden;overflow-y:hidden; border:0xp none #fff; min-height:240px; width:100%;"  frameborder="0" scrolling="no" allowtransparency="true"></iframe>

# References
[^1]: Nicolas Carion, Francisco Massa et al. ["End-to-End Object Detection with Transformers"](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123460205.pdf)ECCV 2020.
[^2]: Yunfei ZHAO ["Transformer? Attention!"](https://blog.yunfeizhao.com/2021/03/31/attention/).

[^3]: Ashish Vaswani, et al. ["Attention is all you need"](https://arxiv.org/abs/1706.03762) NIPS 2017.

