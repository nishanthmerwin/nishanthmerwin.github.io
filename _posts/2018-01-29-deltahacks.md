---
title: "Building an object recognition mobile app"
layout: post
date: 2018-01-29 11:42
image: /assets/images/markdown.jpg
headerImage: false
tag:
- machine learning
- python
- tensorflow
- Android Studio
category: blog
author: nishanth
comments: true
description: Our project for DeltaHacks IV
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

## Introduction

This past weekend, I participated in [DeltaHacks IV](http://deltahacks.com/) at McMaster, and got a chance to meet, learn and collaborate with a lot of awesome people. Our team decided to tackle one of the challenges posted, to improve workplace safety. Our idea was to create an object recognition mobile application that employees could use to easily identify the dangers and safety protocols required to operate the equipment around them.

Together with [Ryan](https://github.com/RyanNourbaran) and [Sujan](https://github.com/Sujan-Kandeepan), we built SafetyFirst.

<iframe src='https://gfycat.com/ifr/ThinFastDanishswedishfarmdog' frameborder='0' scrolling='no' width='720' height='400' allowfullscreen></iframe>


## The technology

A lot of this app was made possible through the work done by Google's research team. In 2017, their team released several [object recognition models](https://github.com/tensorflow/models/tree/master/research/object_detection) trained on the [COCO](http://cocodataset.org) dataset. While they all work well, we chose to use the "Single Shot Multibox Detector (SSD) with MobileNet" due to its rapid prediction time. After trying a few others, we found that this model could provide reliable results in seconds running on just a CPU.

To use this model, we built a simple webserver using [Flask](http://flask.pocoo.org/) to expose a single endpoint. This endpoint, when deployed receives images base64 encoded and embedded within a JSON object. At this point, the image is decoded in the backend and sent through the network for classification, and bounding box prediction. Using PIL, the bounding boxes of each prediction are drawn on the image before sending it back to the user, along with prediction data. To deploy this application, we used [Heroku](https://www.heroku.com/). Although I had never used it before, it's surprisingly simple to expose a Flask application through there.

The front end of this application was built using [Android Studio](https://developer.android.com/studio/index.html). This was entirely built by Sujan, and he did an amazing job. This app currently allows users to take pictures, send it to the webserver for prediction, and then display the results.

Feel free to poke around or fork our [git repo](https://github.com/nishanthmerwin/deltahacks4_arsafety). Happy hacking! 


## Acknowledgements

A big thanks to DeltaHacks IV organizing committee, your hard work made all of this possible. Another thank you to AccelorMital Dofasco for awarding us with the Workplace Safety prize. 



