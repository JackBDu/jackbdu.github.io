---
layout: post
title: Interactive Melody Explorations
categories: blog
tags: itp the-code-of-music
description:
published: true
---

![](/media{{ page.url }}20240310-daily-experiment-draw-melodies-with-hand-refined-1080p@60fps-still.jpg)

For this series, I wanted to create a simple interface for "drawing" melodies on the screen. I started with a mouse interaction where clicking and dragging the mouse drew a sequence of linked nodes along the path of the cursor movement. It worked much like how you would expect any drawing app to work. The melody would start playing as soon as you release your mouse. The nodes were sequentially highlighted as their corresponding notes were played.

<!--more-->

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" loop>
      <source src="/media/{{ page.url }}20240302-daily-experiment-draw-melody-with-various-durations-1080p@60fps.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody>
  <tr><th>
    Experiment on March 2, 2024
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C4C1GEjO_ze/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/YDtrVTdIL">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

In order to add variations in note durations, I first mapped the duration to the distance between neighboring nodes. This turned out to appear counter-intuitive as moving mouse faster resulted in longer notes. In later revisions, I decided to map the note durations in a way that roughly reflected how long each nodes were drawn.

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" loop>
      <source src="/media/{{ page.url }}20240305-daily-experiment-draw-colorful-multiple-melodies-1080p@60fps.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody>
  <tr><th>
    Experiment on March 5, 2024
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C4KnkS_uIkg/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/yvcaOVdym">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

I landed on a color theme of muted colors for the nodes and used the blur filter to create a glowing effect for active nodes. The pitch of each note depended on the y axis.

<table style="width: 100%;">
  <thead><tr><th>
    <div style="width: 100%; padding-top: 75%; position: relative;">
      <iframe style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;" src="https://editor.p5js.org/jackbdu/full/gE3zSWGU3"></iframe>
    </div>
  </th></tr></thead>
  <tbody>
  <tr><th>
  Live demo of the melody painter.
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C4PWD9vsIm2/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/owQNVYo14">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

To add a more magical effect, instead of mouse interaction, I utilized the hand pose model in ml5.js to let people [draw melodies with their hand](https://www.instagram.com/p/C4eOPboMBP2/). More specifically, pinching your thumb and index finger would trigger the drawing mode while spreading them out would clear all nodes. I also experimented with a pie-shaped status indicator, but it stood out too much against the overall minimalistic aesthetic.
