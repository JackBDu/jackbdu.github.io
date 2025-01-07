---
layout: post
title: Audio-Visual Experiment
categories: blog
tags: music audiovisual javascript p5js tonejs itp the-code-of-music
description:
published: true
---

![](/media{{ page.url }}20240131-daily-experiment-3d-donut-sound-visualization-1080p@60fps-still-1.jpg)

For the past two years, I have been doing lots of computational sketches that focused on visuals. This year, I am enrolled in a graduate course at ITP called the Code of Music, taught by [Luisa Pereira](https://www.luisapereira.net). I finally ran out of excuses for not experimenting with sound.

<!--more-->

For this first experiment, we were prompted to build a simple audio visual instrument in p5.js.

Coincidentally, I have just recently started learning shader in p5.js following [this very well-structured course](https://shadertime.betamovement.net) by [Elie Zananiri](https://betamovement.net/about/). Before even writing any shaders, I was already amazed how I could use vertices to define a 3d mesh constructed by a triangle strip, specify a unique color at each vertex, and the 3d mesh will be filled with color gradients that interpolate these colors. With this idea in mind, I started experimenting with a donut-esque mesh by altering its level of details, animating its vertex colors, and applying oscillation to its vertices.

| ![](/media{{ page.url }}20240128-daily-experiment-3d-zigzag-donut-rotating-720p@30fps.gif) |
| :----------------------------------------------------------------------------------------: |
|                               Experiment on January 28, 2024                               |
|           [ [View post on Instagram](https://www.instagram.com/p/C2pSE1JONX2/) ]           |

This served as a good foundation for my visual. Now it is time to choose audio.

I did not want my instrument to sound like a conventional instrument, so I was planning to record some random sounds. It came to my realization that I did not have time to identify sounds that I wanted to record, record them, and then edit them. So I turned to [freesound.org](https://freesound.org). I was searching for water sounds and came across [this very good quality paddle stroke sound pack](https://freesound.org/people/EpicWizard/packs/17730/).

![](/media{{ page.url }}freesound-org-water-paddle-strokes-sound-pack-screenshot.png)

This sound pack includes a decent collection of short paddle stroke sounds that I could use.

Following [this sample sketch](https://editor.p5js.org/luisa/sketches/9Gqsaazs2) from Luisa, I did some quick sketches to familiarize myself with tone.js.

![](/media{{ page.url }}p5js-web-editor-circular-waveform-sketch-screenshot.png)

Once acquinted with tone.js, I finally linked my audio to my visual.

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" loop>
      <source src="/media/{{ page.url }}20240131-daily-experiment-3d-donut-sound-visualization-1080p@60fps.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody>
  <tr><th>
    Experiment on January 31, 2024
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C2y9Onbu5nV/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/YIyVY4NZw">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

In this sketch, I am wrapping the audio waveform around the mesh and applying it as a factor to the radius. In addition, the amplitude of the audio is applied as a factor to the amplitude of the oscillation.

The first version incorporates a keyboard interaction. Later, I thought it would be more interesting to use a mouse to interact as if the mouse is paddling the water.

In the live demo below, you can click and drag your mouse around, and the water sound reacts to how fast you move your mouse.

<table style="width: 100%;">
  <thead><tr><th>
    <div style="width: 100%; padding-top: 75%; position: relative;">
      <iframe style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;" src="https://editor.p5js.org/jackbdu/full/u6KVNRbiv"></iframe>
    </div>
  </th></tr></thead>
  <tbody>
  <tr><th>
    Experiment on February 2, 2024
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C224c1vJTG4/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/u6KVNRbiv">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>
