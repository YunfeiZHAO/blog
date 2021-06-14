---
title: GSOC week0 - Homepage
date: 2021-05-23 12:13:53
category: GSOC 2021 Redhen
tags: [Event]
excerpt: 'Community bonding period with Redhen during Google Summer of Code 2021. An introduction to the GSOC, Redhen, and my project.
(May 17, 2021 - May 23, 2021)'

index_img: /img/GSOC_2021/gsoc.png
banner_img: /img/GSOC_2021/redhen.png
comment: disqus
---
# GSOC 2021
I am very happy to be accepted this year as a GSOC student in the Redhen lab. Google Summer of Code is a global program focused on bringing more student developers into open source software development. Students work with an open-source organization on a 10-week programming project during their break from school. [The organization list for 2021 is listed here](https://summerofcode.withgoogle.com/organizations/?sp-page=3) 

# Redhen Lab
The International Distributed Little Red Hen Lab™ is a global big data science laboratory and cooperative for research into multimodal communication. The main idea of the Redhen lab is cooperation. It is not like a traditional university where professors lead students to do research, while, in the Redhen Lab everyone makes contributions to make progress of research in the multimodal communication world. [The Redhen Lab home page](https://www.redhenlab.org/home) can be found here if you are interested in this community.

# Project description
Gesture recognition becomes popular in recent years since it can play an essential role in many fields, such as non-verbal communication, emotion analysis, human-computer interaction, etc.  We can notice that people use quite a lot of hand gestures in daily life. The research task is to detect hand gestures in raw news videos that are streams of RGB images. I propose a keypoints-based pose tracking system for human tracking and a Transformer and keypoints-based gesture detector for gesture detection to fulfill this task. This structure is composed of a keypoints extractor, a person tracker, and a gesture detector. So the mission has three main parts. The first part is to track people in temporal space.  In the second part, for each person, we use their hand keypoints features in temporal space to construct several keypoints sequences. The third part is to use these sequences to make predictions of the existence of gestures. I believe that for gesture detection tasks, both spatial and temporal information is important. So that is why we use the Transformer that can take into account the local shape information of hands in one frame and can also capture the global hand motion information across the frames. As hand gestures in news videos do not have a good definition of label class, we start with only detecting the existence of a hand gesture. The classification can be easily extended. The final evaluation will be done on Redhen's "Newscape Dataset".
