---
title: GSOC week2 - Transfer Learning on DETR - (May 31 ~ Juin 06, 2021)
date: 2021-06-06 21:37:44
category: GSOC 2021 Redhen
tags: [Machine Learning]
excerpt: 'Community bonding period with Redhen during Google Summer of Code 2021. Resume of first three meetings and first Milestone setting and transfer learning of DETR. (May 31 ~ Juin 06, 2021)'

index_img: /img/GSOC_2021/transfer_learning/transfer_learning.png
banner_img: /img/GSOC_2021/gsoc2021.png
comment: disqus
---
# Blog Resume
Community bonding period with Redhen during Google Summer of Code 2021. (May 31 ~ Juin 06, 2021)
* Resume of first three meetings
* Transfer Learning of DETR.

# Meetings
On Friday 21st May, I had my first meeting with three of my six mentors. They are [Mahnaz Parian-Scherb](https://dbis.dmi.unibas.ch/team/mahnaz-parian-scherb/) who recently finished her PHD degree at the University of Basel of majored in Multimedia Information Retrieval, and she is the mentor who will follow the whole project this summer. She helped me a lot during the preparatio of my GSOC proposal, [Daniel Alcaraz Carrión](https://sites.google.com/view/danielalcaraz) who is a cognitive linguist specialises in multimodal communication and [Inés Olza](https://sites.google.com/site/inesolza/home) who is a Tenured Researcher in Linguistics. It was a short meeting with self-presentations and a little presentation of my project. They confirmed that my project has a foreseeable value in multimodal communication as we need to retrieve information like hand gestures in huge volume of videos to do further research.

On Friday 28st May, The whole Redhen Lab held a very lively team meeting. 58 people participated in this meeting, where [12 selected students](https://www.redhenlab.org/summer-of-code/red-hen-lab-gsoc-2021-projects) in this year's program got to know each other and shared our projects. I am very glad to meet so many professors and students who have the same passion to meet here thanks to Redhen lab.

# Introduction of DETR
I wrote two blogs about [attention mechnism](/2021/03/31/attention/) and [DETR](/2021/04/04/DETR/) respectively. If these two terms are new for you, feel free to have a look at them by clicking the links. In conclusion, models based on Transformer are very good tools to extract both local information that represents the shape of the hand in one video frame and global information that represent the motions across several video frames.

# Transfer Learning on DETR
During this week's work, I read thoroughly [the official implementation of DETR](https://github.com/facebookresearch/detr) published by Facebook. This project uses only python with Pytorch as the machine learning framework  that makes it easy to use and easy to understand.
