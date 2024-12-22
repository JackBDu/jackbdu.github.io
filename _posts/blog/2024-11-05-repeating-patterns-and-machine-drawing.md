---
layout: post
title: Repeating Patterns and Machine Drawing
categories: blog
tags: print-and-code analog
description:
published: true
---

![](/media{{ page.url }}20241105-67_03426.jpg)

In my past code sketches, I have created patterns in various forms. Most of the time, the patterns were formed simply by repeating the same visual. In a recent class, Tega gave us a systematic overview of different approaches to make patterns. It was mind blowing to see how extensively people have studied patterns. In particular, I was very much drawn into Truchet tiles.

<!--more-->

Before implementing Truchet tiles, I first recreated five classic artworks featuring unique patterns.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-schotter-by-georg-nees-recreation.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-hommage-a-barbaud-no-1-tribute-to-barbaud-by-vera-molnar-recreation.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-structures-of-squares-by-vera-molnar-recreation.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-quatre-elements-distribues-au-hasard-by-vera-molnar-recreation.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-shift-by-bridget-riley-recreation.png)

I had a lot of fun writing code for these. One thing that kept coming up as I worked on these exercises was the grid. Essentially, all of these sketches incorporated a grid of tiles in different ways. When I implemented Truchet tiles, I conveniently started with the grid code that I already had. For each tile, the sketch randomly chooses one of the two tile options.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles.png)

It is just amazing how you can create mesmerizing patterns like this with only two different tiles. And adding a color makes the pattern even more interesting.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-duo-color.png)

I am very much fascinated by how the patterns look seamless as long as the edges of each tile stays the same. Instead of perfectly round arcs, I decided to write multiple versions of “arcs”.

First, I simply threw in some randomness and made the arc look scribbly.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-scribbly-arcs-using-randomness.png)

Simply changing a parameter or using randomness in a slightly different way will result in quite different scribbles.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-scribbly-arcs-using-randomness-v2.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-scribbly-arcs-using-randomness-v3.png)

Then, I experimented with bezier curves.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-scribbly-arcs-using-quadratic-bezier-curves-and-randomness.png)

I tried removing some randomness to give a more uniformed look.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-bezier-curves.png)

I also tried stretching the bezier curves.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-bezier-curves-stretched.png)

I made the curves flowery and then with spiral.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-bezier-curves-flowery.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-bezier-curves-spiral.png)

When I changed one of the parameters, I was pleasantly surprised to see these squarish tiles.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-with-bezier-curves-spiral-squarish.png)

These gave me a good variety of curves and here comes the fun part—all of them are mutually compatible. So I can combine them all together!

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-different-styles-in-grid.png)

Of course, it became more fun when I repeated the same logic and added randomness when choosing each chunk of tiles of a particular style.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-mixed-styles-3x3.png)

By varying the size of these chunks, the visuals appear quite different.

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-mixed-styles-2x2.png)

![](/media{{ page.url }}browser-screenshot-p5js-web-editor-truchet-tiles-mixed-styles-1x1.png)

Finally, I used the AxiDraw pen plotter to draw these patterns with various ink colors and paper colors.

![](/media{{ page.url }}20241105-67_03269.jpg)

![](/media{{ page.url }}20241105-67_03322.jpg)

![](/media{{ page.url }}20241105-67_03359.jpg)

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-3x3-yellow-on-black-timelpase-cropped-720p@30fps.mp4" type='video/mp4'>
</video>

Here are the finished drawings:

![](/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-3x3-yellow-on-black.jpg)

![](/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-2x2-blue-on-black.jpg)

![](/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-1x1-green-on-black.jpg)

![](/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-3x3-purple-on-purple.jpg)

![](/media{{ page.url }}20241105-axidraw-mixed-truchet-tiling-2x2-yellow-on-orange.jpg)
