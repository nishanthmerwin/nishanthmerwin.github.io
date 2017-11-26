---
title: "Hello and jless"
layout: post
date: 2017-11-24 11:42
image: /assets/images/markdown.jpg
headerImage: false
tag:
- json
- CLI
- linux
category: blog
author: nishanth
description: Introduction and quick tip
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---

## Introduction

Hi all! Welcome to my blog. As you might already know, 
I'm currently heading towards the end of my graduate career and thought 
about all of the things I've learned through my time here. To keep some record 
of it and share a few of my experiences, I'm publishing some tidbits of knowledge 
here.
Keep posted, and while I have you, I'll show you a neat little trick I use 
daily.


## jless

I use the JSON format almost everywhere, and it provides a simple medium
to transfer data interplatform, and is readable by almost anything. On the CLI,
I use `jq` to view this. To make this even easier, I use the `jless` CLI command,
which makes this process much more unix-esque.

Insert this into your `.zshrc` or `.bashrc` and your good to go!
```
jless() { jq . $1 -C | less -R; }
``` 
<iframe src='https://gfycat.com/ifr/ImpartialTemptingGreatdane' frameborder='0' scrolling='no' width='714' height='400' allowfullscreen></iframe>

