---
layout: post
title: Bug Musicans
categories: blog
tags: music audiovisual web javascript p5js matterjs tonejs itp the-code-of-music
description:
published: true
---

[ [Try Bug Musicans](https://editor.p5js.org/jackbdu/full/rhLypl-x7) ]

![](/media/{{ page.url }}bug-musician-cover-photo.jpg)

This series of experiments started with something completely unrelated to music. I remember seeing ragdoll characters commonly used in video games and artworks either to invoke a surreal feeling or for a comedic effect. I wanted to try implementing it in p5.js with the help of a physics library.

<!--more-->

Box2D is one of those popular physics engine for 2D graphics, but Matter.js seems to have gained popularity in recent years partially due to its native impelmentation in JavaScript. After reading its documentation and watching a couple of Coding Train videos on it, I finally decided to use matter.js.

To me, a ragdoll is essentially a human skeleton with physics built-in. The most minimal starting point I could think of was to create one joint.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240326-daily-experiment-matterjs-pendulum-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

From there, I added multiple joints to form a human form.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240328-daily-experiment-matterjs-skeleton-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

Then, I added interactivity so the body can be dragged around. The interaction felt quite different when I switched between applying a gravity and not.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240330-daily-experiment-matterjs-skeleton-with-zero-gravity-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240331-daily-experiment-matterjs-skeleton-collapsing-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

While that was an interesting experiment that was definitely worth going back some day, I became bored with it pretty quickly and started to generate bodies that were not in human forms at all. What if it had more than four limbs? What if it had many segments of bodies? What if the bodies branched out? The possibilities were endless. I came up with a data structure for representing these various combinations of body forms and started generating all kinds of weird shapes.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240402-daily-experiment-matterjs-centipede-skeleton-zero-gravity-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

Eventually, I found these forms to look most interesting when they were symmetrical. Maybe that was because most creatures in the nature are symmetrical? Or maybe humans (or just me?) are biased towards symmetrical shapes? When these forms were symmetrical, they started to like bugs. Due to the experimental nature and the time constraint, I focused more on the structure of these creatures and simply used ellipses for all body parts and segments.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240405-daily-experiment-matterjs-symmetrical-bug-generation-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

Having created this weird bug generator coupled with a physics engine, I decided to apply it to the musical experiments that I had been doing. I created a virtual string instrument for these bugs.

<video width="100%" preload="auto" controls loop>
  <source src="/media{{ page.url }}20240409-daily-experiment-matterjs-bug-musicans-waveform-strings-1080p@60fps-clip.mp4" type='video/mp4'>
</video>

In the live demo below, you can click on the virtual instrument to create as many bugs as you wish. Once the bugs are created and released, they would crawl around on their own, sometimes interacting with each other. When its head comes in contact with a string, the string would vibrate and make a particular sound. As the bugs wander around on this virtual instrument, they create a kind of surreal symphony. Alternatively, you could also drag a bug around to "play" this instrument directly.

<table style="width: 100%;">
  <thead><tr><th>
    <div style="width: 100%; padding-top: 75%; position: relative;">
      <iframe style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;" src="https://editor.p5js.org/jackbdu/full/rhLypl-x7"></iframe>
    </div>
  </th></tr></thead>
  <tbody>
  <tr><th>
  Live demo of Bug Musicans.
  </th></tr>
  <tr><th>
    [ <a href="https://www.instagram.com/p/C5mf7_XsM7u/">View post on Instagram</a> | <a href="https://editor.p5js.org/jackbdu/sketches/rhLypl-x7">View source code in p5.js Web Editor</a> ]
  </th></tr>
  </tbody>
</table>
