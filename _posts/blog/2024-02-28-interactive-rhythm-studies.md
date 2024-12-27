---
layout: post
title: Interactive Rhythm Studies
categories: blog
tags: itp the-code-of-music
description:
published: true
---

![](/media{{ page.url }}20240228-daily-experiment-physics-driven-interactive-rhythm-sequencer-1080p@60fps-still.jpg)

In this series of experiments, I started with very basic algorithmically-generated rhythms coupled with simple visual elements.

<!--more-->

| ![](/media{{ page.url }}20240217-daily-experiment-basic-rhythm-flowery-visuals-arranged-circularly-720p@30fps-clip.gif) |
| :---------------------------------------------------------------------------------------------------------------------: |
|                                             Experiment on Feburary 17, 2024                                             |
|                         [ [View post on Instagram](https://www.instagram.com/p/C3e9oieum5N/) ]                          |

Depsite the simplicity of the visuals, I found myself making more progress in the visual than the rhythm.

| ![](/media{{ page.url }}20240219-daily-experiment-basic-rhythm-triangle-visuals-arranged-circularly-720p@30fps-clip.gif) |
| :----------------------------------------------------------------------------------------------------------------------: |
|                                             Experiment on Feburary 19, 2024                                              |
|                          [ [View post on Instagram](https://www.instagram.com/p/C3jeGAouGUg/) ]                          |

I wanted to incorporate some physics in the creation of the rhythm, but I was not sure how I could do it. I decided to implement a basic rhythm sequencer as a starting point.

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" loop>
      <source src="/media/{{ page.url }}20240223-daily-experiment-drum-machine-dragging-support-added-1080p@60fps.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody>
  <tr><th>
    Experiment on Feburary 23, 2024
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C3uMxR8OYuQ/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/QxOHeLrBY">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

While physics simulation can be a bit unpredictable, a steady tempo can still be maintained if a sequencer remains the underlying mechanism. An idea came to me that I could add a bouncing bubble and let it toggle every beat it passes by.

Though it is simple enough to add one bouncing bubble, having multiple ones interact with either other is a different story. I eventually decided to use [matter.js](https://brm.io/matter-js/), a 2D physics engine, to take care of the physics aspect. In the demo below, you can click and drag a bubble if you would like. The bubbles eventually stop due to frications and there you have your rhthym.

<table style="width: 100%;">
  <thead><tr><th>
    <div style="width: 100%; padding-top: 75%; position: relative;">
      <iframe style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;" src="https://editor.p5js.org/jackbdu/full/sH4pFwgI1"></iframe>
    </div>
  </th></tr></thead>
  <tbody>
  <tr><th>
  Live demo of the interactive sequencer.
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C36spupsuZc/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/sH4pFwgI1">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>
