---
layout: post
title: Node-Based Interactive Music
categories: blog
tags: itp the-code-of-music
description: 
published: true
---

While we were exchanging ideas of what we could do with Tone.js and p5.js, [Henry Chen](https://www.instagram.com/metadata_0/) came up with this idea of a node-based system for interacting with music in a virtual 3D environment, in which moving one node could simultaneously affect multiple other nodes that affect the music. We agreed that creating a 2D version first could serve as a very good starting point.

<!--more-->

We debated with ourselves how we should collaborate and ultimately decided that Henry would focus on sound (Tone.js) while I focus on visual (p5.js).

I started with implementing basic draggable nodes in p5.js. As I started working on making the nodes draggable, I debated if I should use HTML elements or even SVG graphics as nodes. It would be much easier to add event listeners to them to handle mouse interaction than implementing it in p5.js canvas. I eventually still decided to use p5.js canvas, because the canvas would allow me to add more interesting visuals later on and I thought it would be a fun challenge as well.

![](/media{{ page.url }}p5js-web-editor-basic-draggable-nodes-screenshot.png)

It did end up taking me quite some time in order to take into consideration all kinds of scenarios to avoid unexpected behavior, but the satifiscaiton of seeing it work perfectly was worth all the effort.

Next, I added text, indicating each node's role as well as normalized value based on its distance to the parent node. Each node's color also changes based on its value.

![](/media{{ page.url }}p5js-web-editor-basic-colorful-draggable-nodes-with-text-screenshot.png)

The next day, I spent a lot of time cleaning up the code so it is more organized and readable. I also experimented with a new style for the links between nodes. The links now consist of small circles filled with colors interpolating between colors of different nodes.

<table style="width: 100%;">
  <thead><tr><th>
    <div style="width: 100%; padding-top: 75%; position: relative;">
      <iframe style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;" src="https://editor.p5js.org/jackbdu/full/k9koNakbV"></iframe>
    </div>
  </th></tr></thead>
  <tbody>
  <tr><th>
  Live demo of interactive nodes (Click and drag to interact).
  </th></tr>
  <tr><th>
    [ <a href="https://editor.p5js.org/jackbdu/sketches/k9koNakbV">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>

