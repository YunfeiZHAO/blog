---
title: GSOC week0 - Homepage
date: 2021-05-23 12:13:53
category: GSOC 2021 Redhen
tags: [Event]
excerpt: 'Community bonding period with Redhen during Google Summer of Code 2021. An introduction to the GSOC, Redhen, and my project.
(May 17, 2021 - May 23, 2021)'

index_img: /img/GSOC_2021/gsoc.png
banner_img: /img/GSOC_2021/gsoc2021.png
comment: disqus
---
# GSOC 2021
I am very happy to be accepted this year as a GSOC student in the Redhen lab. Google Summer of Code is a global program focused on bringing more student developers into open source software development. Students work with an open-source organization on a 10-week programming project during their break from school. [The organization list for 2021 is listed here](https://summerofcode.withgoogle.com/organizations/?sp-page=3) 

# Redhen Lab
The International Distributed Little Red Hen Lab™ is a global big data science laboratory and cooperative for research into multimodal communication. The main idea of the Redhen lab is cooperation. It is not like a traditional university where professors lead students to do research, while, in the Redhen Lab everyone makes contributions to make progress of research in the multimodal communication world. [The Redhen Lab home page](https://www.redhenlab.org/home) can be found here if you are interested in this community.

# Project Description
Gesture recognition becomes popular in recent years since it can play an essential role in many fields, such as non-verbal communication, emotion analysis, human-computer interaction, etc.  We can notice that people use quite a lot of hand gestures in daily life. The research task is to detect hand gestures in raw news videos that are streams of RGB images. I propose a keypoints-based pose tracking system for human tracking and a Transformer and keypoints-based gesture detector for gesture detection to fulfill this task. This structure is composed of a keypoints extractor, a person tracker, and a gesture detector. So the mission has three main parts. The first part is to track people in temporal space.  In the second part, for each person, we use their hand keypoints features in temporal space to construct several keypoints sequences. The third part is to use these sequences to make predictions of the existence of gestures. I believe that for gesture detection tasks, both spatial and temporal information is important. So that is why we use the Transformer that can take into account the local shape information of hands in one frame and can also capture the global hand motion information across the frames. As hand gestures in news videos do not have a good definition of label class, we start with only detecting the existence of a hand gesture. The classification can be easily extended. The final evaluation will be done on Redhen's "Newscape Dataset".

# Weekly Report
<p>
    <a style="color:#FF851B ;font-size: 24px;">Community Bonding Period</a> 
    <a style="float: right;font-weight: bold;">(From May 17, 2021 till June 7, 2021)</a>
</p>

* [Week 0 Homepage](/2021/05/23/GSOC0-homepage/) <a style="float: right;">(May 17 ~ May 23, 2021)</a>
* [Week 1 Report: Setup Singularity on HPC](/2021/05/30/GSOC1-singularity/) <a style="float: right;">(May 24 ~ May 30, 2021)</a>
* [Week 2 Report: Transfer Learning for DETR](/2021/06/06/GSOC2-Transfer-Learning/) <a style="float: right;">(May 31 ~ Juin 06, 2021)</a>

<p>
    <a style="color:#FF851B ;font-size: 24px;">Coding Period Before the First Evaluation</a> 
    <a style="float: right;font-weight: bold;">(First evaluation time July 12 - 16, 2021)</a>
</p>

* [Week 3 Report]() <a style="float: right;">(Juin 07 ~ Juin 13, 2021)</a>
* [Week 4 Report]() <a style="float: right;">(Juin 14 ~ Juin 20, 2021)</a>
* [Week 5 Report](/2021/06/23/GSOC5-schema-conversation-with-linguists/) <a style="float: right;">(Juin 21 ~ Juin 27, 2021)</a>
* [Week 6 Report]() <a style="float: right;">(Juin 28 ~ July 04, 2021)</a>
* [Week 7 Report]() <a style="float: right;">(July 05 ~ July 11, 2021)</a>

<p>
    <a style="color:#FF851B ;font-size: 24px;">Coding Period Before the Final Evaluation</a> 
    <a style="float: right;font-weight: bold;">(Final evaluation time August 16 - 23, 2021)</a>
</p>

* [Week 8 Report]() <a style="float: right;">(July 12 ~ July 18, 2021)</a>
* [Week 9 Report]() <a style="float: right;">(July 19 ~ July 25, 2021)</a>
* [Week 10 Report]() <a style="float: right;">(July 26 ~ August 01, 2021)</a>
* [Week 11 Report]() <a style="float: right;">(August 02 ~ August 08, 2021)</a>
* [Week 12 Report]() <a style="float: right;">(August 09 ~ August 15, 2021)</a>

[Final result](/2021/08/22/GSOC-final-2021/) <a style="float: right;">(August 31, 2021)</a>

# Related Papers
## Computer Vision
[1]: Nicolas Carion, Francisco Massa et al. ["End-to-End Object Detection with Transformers"](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123460205.pdf)ECCV 2020.
[2]: Zhe Cao, Gines Hidalgo, Tomas Simon,  Shih-En Wei, Yaser Sheikh et al. ["OpenPose: Realtime Multi-Person 2D PoseEstimation using Part Affinity Fields"](https://ieeexplore.ieee.org/document/8765346) IEEE Transactions on Pattern Analysis and Machine Intelligence.  Date of publication: 17 July 2019.

## Dataset
[1]:  Chunhui Gu, Chen Sun, David A. Ross, Carl Vondrick et al. ["AVA: A Video Dataset of Spatio-temporally Localized Atomic Visual Actions"](https://openaccess.thecvf.com/content_cvpr_2018/papers/Gu_AVA_A_Video_CVPR_2018_paper.pdf) CVPR 2018.


# Links for this project
* [GSOC 2021 Yunfei ZHAO Github](https://github.com/YunfeiZHAO/gsoc-redhen-2021)
* [Project page on Redhen](https://www.redhenlab.org/summer-of-code/red-hen-lab-gsoc-2021-projects)
* [Original proposal of this project](https://www.overleaf.com/read/jwnknydxtpdh)

<iframe src="https://pocket.yunfeizhao.com/donation_unit" style="overflow-x:hidden;overflow-y:hidden; border:0xp none #fff; min-height:240px; width:100%;"  frameborder="0" scrolling="no" allowtransparency="true"></iframe>