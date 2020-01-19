---
title: "Swinging with trigonometry"
layout: post
date: 2020-01-18 11:42
image: /assets/images/markdown.jpg
headerImage: false
tag:
- game development
- math
- pygame
category: blog
author: nishanth
comments: true
description: Building a simply physics based game using pygame.
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

## Introduction

As a result of commuting, I've found myself back playing mobile phone and web games on the train.
It's a nice pass time, but I recently came around a game that although seems remarkably simple, it's actually
a ton of fun to play (plus it gets really challenging).
<a href="https://www.newgrounds.com/portal/view/724232">Handulum +</a> is a physics based game where you can
"catch" a falling ball and swing it along a pendulum. I got decently far, but wanted to see what it 
would take to actually recreate this sort of physics engine. I'm not really a game developer, but
I've been really interested in developing more low level graphics for creative side projects and
though this would be a good place to start. Check out Handulum + below though, its miles beyond
anything I could create!

<figure align="center">
    <video height="300" width="500" autoplay="" loop>
        <source src="https://video.twimg.com/tweet_video/EOkWxJhWoAYWYPH.mp4" type="video/mp4">
        </source>
    </video>
</figure>

The first thing I did was choose my ecosystem. Since my day job mostly revolves around Python,
I quickly found myself reading into <a href="https://www.pygame.org/wiki/GettingStarted"> PyGame</a>.
The syntax was brief enough and it could draw circles and lines, which was more than enough on the graphics
side for me. My main goal here was to recreate the physics involved, not spend too much time
trying to make it pretty (although that might be a fun extension to this project). A few 
<a href="http://www.petercollingridge.co.uk/tutorials/pygame-physics-simulation/">tutorials</a>
later, I now had a bouncing ball that somewhat emulated gravity.

But this game obviously required a bit more than bouncing. I needed to figure out how to
get the ball to move in circle, and even more, observe some conservation of momentum
as it attached and released from the pendulum. This was certainly more challenging
than I had initially thought, and quickly found myself lost in Google searches and
<a href="https://en.wikipedia.org/wiki/Pendulum_(mathematics)#Simple_gravity_pendulum">endless equations</a>
describing motion in "simple" pendulums (not so simple for me!).

When I first started, I simply tried to do everything via code, but I quickly found the ball
moving in all sorts of crazy ways, and not getting and progress.
In the end, I found it best to just draw it out, and pull out some handy-dandy trigonometry.
What's not shown below are the 10+ other pages of scribbles that I threw away along the process.

<p align="center">
  <img src="/assets/images/pendulum/trig.jpg" title="Does this resemble trigonomotry?">
</p>

I realized  were two key aspects that I had to consider:
- Converting forces in x and y directions to an angular direction via trigonometry (thanks
    to SOH-CAH-TOA).
- Understanding that angular velocity can be represented as linear velocity (in x and y
    direction) via the angle of the tangent, which luckily enough is also calculable
    via trigonometric equations.


Overall, this took me quite a bit longer than I expected, but I did end up learning a lot
and brushing up on some mathematics that I had long forgotten. Doing this in Python made
this project a lot easier as I was very comfortable code organization and structuring
everything in an object oriented manner. Take a look at the prototype below:

<div style='position:relative; padding-bottom:calc(78.50% + 44px)'><iframe src='https://gfycat.com/ifr/FlamboyantColossalIndianglassfish' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>

If you're even more curious, feel free to fork the repo and try running it yourself.
Let me know what you think.

Repo: <a href="https://github.com/nishanthmerwin/handball">HandBall</a>

