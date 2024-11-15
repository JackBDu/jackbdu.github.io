---
layout: post
title: Laser Cutting Experiments
categories: blog
tags: itp introduction-to-fabrication
description: 
published: true
---

This week, I have been experimenting with laser cutting. I wanted to continue incorporating computational thinking into my process, so the first thing I thought of was to create a p5.js sketch for the laser cutter. Although raster files can be used for etching, I think it would be more interesting to generate a vector path for the laser cutter.

<!--more-->

After some research, I found [an open-source project](https://github.com/zenozeng/p5.js-svg) that provides a SVG runtime for p5.js. In order to use it in a p5.js project, first include `<script src="https://unpkg.com/p5.js-svg@1.5.1"></script>` in the index.html file.

![](/media{{ page.url }}20230929-p5js-svg-setup-script-tag.png)

Then specify SVG as the renderer in `createCanvas()`.

![](/media{{ page.url }}20230929-p5js-svg-setup-specifying-renderer.png)

Now, everything we draw in p5.js will be rendered as an SVG element.

![](/media{{ page.url }}20231002-p5js-svg-setup-web-inspector.png)

After some initial experiments with the SVG runtime, I decided to test it out with one of my old sketches, which could convert any reference image to a drawing formed by scribbles (in the sketch below, the reference image is a QR code). To my surprise, it worked right away after doing the steps above.

![](/media{{ page.url }}20230930-p5js-web-editor-svg-experiment-scribble-filter-jackbdu-instagram-qr-code.png)

I did not yet find any easy way to export the sketch as a SVG file, instead, I grabbed the SVG code directly from the web inspector and pasted it into a blank .svg file. That way, I could do some final edits in Adobe Illustrator.

![](/media{{ page.url }}20231002-illustrator-svg-experiment-scribble-filter-jackbdu-instagram-qr-code.png)

In Adobe Illustrator, I resized the scribble (yes, singular, because it was a single continous scribble) and fitted it onto a 2.125 x 2.125 inch square with rounded corners, which was the short side of a credit card.

Below is a timelapse of the engraving process:

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" poster="">
      <source src="/media{{ page.url }}IMG_9353.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody><tr style="text-align: center;"><th></th></tr></tbody>
</table>

Then I did some more tests with other old sketches. One was a flowery design formed by repeated sprial patterns.

![](/media{{ page.url }}20230930-p5js-web-editor-svg-experiment-scribble-filter-three-petal-flowers.png)

![](/media{{ page.url }}20230930-illustrator-svg-experiment-scribble-filter-three-petal-flowers.png)

Another one was the same scribble sketch with a self-portrait as the input.

![](/media{{ page.url }}20230930-p5js-web-editor-svg-experiment-scribble-filter-jackbdu-self-portrait-16x16.png)

Here are all the small tests I did:

![](/media{{ page.url }}20231001-ZVE03798.jpg)

Finally, moving to a design for a larger piece. I decided to use the self-portrait and add more a bit more details to it.

![](/media{{ page.url }}20230930-p5js-web-editor-svg-experiment-scribble-filter-jackbdu-self-portrait-32x32.png)

In Adobe Illustrator, I separated the outline and the scribble into two layers.

![](/media{{ page.url }}20231001-illustrator-scribble-filter-jackbdu-self-portrait-32x32.png)

I sent engraving and cutting as two separate jobs to the Epilog Laser Engraver.

![](/media{{ page.url }}20231001-epilog-dashboard-scribble-filter-jackbdu-self-portrait-32x32-scribbles-with-custom-settings.png)

![](/media{{ page.url }}20231001-epilog-dashboard-scribble-filter-jackbdu-self-portrait-32x32-outline-with-custom-settings.png)

![](/media{{ page.url }}IMG_9399.jpg)

Here is a timelapse of the whole process, which took about half an hour:

<table style="width: 100%;">
  <thead><tr><th>
    <video controls width="100%" preload="auto" poster="">
      <source src="/media{{ page.url }}IMG_9401.mp4" type='video/mp4'>
    </video>
  </th></tr></thead>
  <tbody><tr style="text-align: center;"><th>
  </th></tr></tbody>
</table>

Here is the final result:

![](/media{{ page.url }}20231001-ZVE03686.jpg)

![](/media{{ page.url }}20231001-ZVE03835.jpg)

Some more closeup shots:

![](/media{{ page.url }}20231001-ZVE03731.jpg)

![](/media{{ page.url }}20231001-ZVE03746.jpg)
