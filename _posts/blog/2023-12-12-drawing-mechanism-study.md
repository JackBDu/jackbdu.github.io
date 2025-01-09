---
layout: post
title: Drawing Mechanism Study
categories: blog
tags: itp fabricating-mechanical-automatons
description:
published: true
---

![](/media{{ page.url }}drawing-mechanism-study-cover-photo.jpg)

Inspired by 18th-century automatons such as [the writer and the draughtsman](https://en.wikipedia.org/wiki/Jaquet-Droz_automata) by Jaquet-Droz, I wanted to create my own drawing automatons. In particular, I am hoping to build more accessible drawing automatons with a focus on enhanced programmability. As a first step, I decided to design a mechansim for drawing scribbly lines.

<!--more-->

After some research, I landed on a 4-bar linkage design. I started with prototypes in MotionGen, which gave me a basic idea of the feasibility.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}motion-gen-simulation-drawing-mechanism-short-arms.mov_compressed.mp4" type='video/mp4'>
</video>

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}motion-gen-simulation-drawing-mechanism-long-arms.mov_compressed.mp4" type='video/mp4'>
</video>

Then I designed the linkages in Fusion 360 and assembled a minimal physical prototype.

![](/media{{ page.url }}drawing-mechanism-prototype.jpg)

That gave me more confidence, which led to a working prototype that actually drew on paper.

<video width="100%" preload="auto" controls>
  <source src="/media{{ page.url }}drawing-mechanism-prototype-v2.mov_compressed.mp4" type='video/mp4'>
</video>

In order to achieve some basic programmability, I took inspiration from Spirograph and designed modular components for this mechanism. With different combinations and configurations of the linkages, the mechansim could draw a variety of scribbles.

![](/media{{ page.url }}drawing-mechanism-modular-plate.png)

![](/media{{ page.url }}drawing-mechanism-modular-gears.png)

![](/media{{ page.url }}drawing-mechanism-modular-linkage-arm.png)

In addition, I improved the pen holding mechansim, which would secure the pen in place while allowing free rotation at the axle.

![](/media{{ page.url }}drawing-mechanism-modular-linkage-arm-with-pen-holder.png)

For the next step, I am hoping to expand beyond scribbly lines and create more intricate images. For instance, I plan to design modular components that are algorithmically generated for drawing different tiles, which could then be combined to form different patterns.
