---
title: "Making sense of XKCD"
layout: post
date: 2019-01-28 11:42
image: /assets/images/markdown.jpg
headerImage: false
tag:
- visualization
- data science
category: blog
author: nishanth
comments: true
description: Using NLP and computer vision techniques to sort XKCD comics
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

## Introduction

Who doesn't love [XKCD](https://xkcd.com/)? A while back, around the start of my grad school, I came across a relevant machine learning comic from Randall (see below). Today, we're going to throw some NLP and topic modeling into a pile and hope something fun comes out the other end.

<figure align="center">
  <img src="https://imgs.xkcd.com/comics/machine_learning.png" title="The pile gets soaked with data and starts to get mushy over time, so it's technically recurrent.">
  <figcaption>Test caption.</figcaption>
</figure>

First things first, lets download some of these comics. Altogether, Randall Munroe (author of XKCD) has been extremely productive and has created over 2100 comics since the inception of XKCD on January 1st 2006! Looking at this, he is scarily consistent, averaging about 13 comics a month. The first month is an outlier, I imagine he had a butt load of comics he had drawn and released them all onto the internet at once. But I truly admire his consistency!

<p align="center">
  <img src="/assets/images/xkcd/productivity.png" title="My attempt at recreating some XKCD-esque charts">
</p>

Next, lets gather some more data. Thankfully, the folks at [Explained XKCD](https://www.explainxkcd.com/wiki/index.php/Main_Page) have annotated each of these comics with a transcript as well as their own explanations for each. This, along with the actual images, meant I had a rich dataset to work with of roughly unstructured text and their corresponding comics.

### We have data, now what?

The title of this section accurately describes how I felt at this stage in the project. With work, I usually have a goal or end project, but I wanted to use this dataset to learn some new skills. So, I thought to try a bit of topic modelling. I really like this technique because it essentially allows the data to "self-organize"! Basically, based on the co-occurance of specific words, we can identify several topics that are commonly used in XKCD comics. After surprisingly little actual coding, I was able to build a Latent Ditrecht Allocation (LDA) model that identified 10 topics of interest.

Creating the model itself was pretty simple:


1. Lemmatizing all words identified in both transcript and explanations of the comic. Gensim / NLTK libraries helped out a lot here!
2. Create a dictionary, and remove all words that appear relatively infrequently.
3. Use gensim to build an LDA model across 10 topics, passing over the data 20 times.

And with that, we get the following topics revealed.


| Topic Number 	|                                        Words                                       	| What I think it means? 	|
|:------------:	|:----------------------------------------------------------------------------------:	|:----------------------:	|
|       0      	|       megan, black, ponytail, friend, game, panel, year, beret, number, phone      	|  People and timelines  	|
|       1      	|      stapl, momentum, len, megan, cat, repair, beret, ponytail, pointer, black     	|           ??           	|
|       2      	|       cabl, jack, geek, ingredi, pump, verb, guest, sister, factori, weekend       	|         Cables?        	|
|       3      	|  barrel, bowl, polar, weekend, screenshot,   float, dozen, flowchart, flash, sleep 	|         Barrels        	|
|       4      	|       gold, megan, michael, pool, sheet, love, backpack, feynman, peni, bird       	|          Gold?         	|
|       5      	|        band, fluid, song, wikipedia, megan, bush, word, game, monster, music       	|           ??           	|
|       6      	|        elev, twitter, megan, reddit, cabl, friend, kernel, river, user, lake       	|           ??           	|
|       7      	| skateboard, senat, steve, firefli, escal, summer, paul, democrat, republican, adam 	|         Politics       	|
|       8      	|    chess, pokemon, knight, hors, basketbal, sister, player, captur, piec, board    	|    Chess and pokemon   	|
|       9      	|       virus, backup, keyboard, chip, belt, dougla, drone, black, beret, ghost      	|           ??           	|
{:.mbtablestyle}


Looking through some of these, there were some that were surprisingly accurate. For example, barrels is a recurring theme in his works, and was deserving of a whole topic on its own. Other topics such as 2, 5, 6 and 9 were very rarely observed.


### Lets search by topic!

From here, I started playing around to see how we could sort and search for these topics among all of these comics. In particular, I wanted to share this with all of you.
So, using the LDA model for each of these topics, I wanted to create a web app with SLIDERS! Realistically, you can use the sliders to identify
the mix of these topics you want, and with my website, I'll identify the top five comics that match your search. Kinda like the DJ booth of XKCD comics!

I built this pretty rapidly using Flask to act as the backend + server side rendering engine. Heroku allows you to deploy flask applications with ease, and for free so you can find it all on there.



- [WebApp](https://protected-mesa-78784.herokuapp.com/)
- [WebApp Source code](https://github.com/nishanthmerwin/xkcd_lda_flaskapp)
- [GitHub code for this analysis](https://github.com/nishanthmerwin/xkcd_lda)


Overall, I was pretty impressed with this dataset. In the end, I wanted to put something out before diving too much into the data science-y aspects of it, as I could have diven much deeper! For anyone curious, here are a few more ideas I had / might pursure with this dataset:

- Sentiment analysis (How positive / negative / angry do each of the comics read?)
- Image analysis using deep learning
    - Can we cluster according to these topics that we identified?
- How many topics is ideal? What words are most common?
- With StyleGAN out there now, can we generate some of these drawings of Megan / beret man?





