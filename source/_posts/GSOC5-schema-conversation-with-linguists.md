---
title: GSOC week5 - Schema of the project and a conversation with a linguist - (Juin 21 ~ Juin 27, 2021)
date: 2021-06-23 11:00:00
category: GSOC 2021 Redhen
tags: [Gesture temperal detection]
excerpt: 'Coding period with Redhen during Google Summer of Code 2021. A meeting with a linguist and the illustration of gestures temporal detections.
(Juin 21 ~ Juin 27, 2021)'

index_img: /img/GSOC_2021/week5/gesture.jpg
banner_img: /img/GSOC_2021/gsoc2021.png
comment: disqus
---

# Blog Resume
Coding period with Redhen during Google Summer of Code 2021. (Juin 21 ~ Juin 27, 2021)
* Resume of the fourth meeting.
* The illustration of the first milestone model.

# Meetings
On Wednesday 23st Juin, I had our regular meeting with my mentors [Mahnaz Parian-Scherb](https://dbis.dmi.unibas.ch/team/mahnaz-parian-scherb/) and [Cristóbal Pagán Cánovas](https://sites.google.com/site/cristobalpagancanovas/). Cristóbal Pagán Cánovas is a linguist and he gives us a very prefessional view of the project and his advice.

During this meeting, we reach a consensus that the temporal location of gestures (The start point and the endpoint of a gesture) is more meaningful than the classification of a gesture in the perspective of linguistic research.

Why gestures' labels are not the key to our project? Computer engineers always want to model the classification of gesture in the same way as other classification problems such as car classification, object classification, etc. As for the detection problem, computer engineers tend to model gesture detection the same way as detecting a car on the road. But gesture detection is more like finding a needle in a haystack. Firstly, there are too many gestures that have the same linguistic meaning. People from different countries with different cultural backgrounds in different circumstances will use different gestures to express the same thing. Secondly, the same gesture may also have different meanings. For example, when we speak, the same phrase with different tones and different speaker's emotion represents completely different meaning. So the analysis part of a gesture is a very challenging task for linguists.

What do computer engineers should do, and what this project's value? To understand human behaviors and gesture meaning, a computer engineer may use his or her professional skill to provide linguists with indicators and statistical analysis of data. For instance, where the gesture starts and where the gesture ends. The probability of the existence of a gesture in this detected segmentation in a video.  The influence of a big movement of a hand key point to a certain gesture to occur.

Based on the ideas of this meeting, I am going to make a diagram of my model and a foreseeable estimation of its final results.