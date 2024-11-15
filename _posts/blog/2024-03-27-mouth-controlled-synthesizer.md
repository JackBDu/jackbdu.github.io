---
layout: post
title: Mouth-Controlled Synthesizer
categories: blog
tags: itp the-code-of-music
description:
published: true
---

In my previous experiments, I integrated hand pose detection in my sketch. Hand-driven interaction feels magical, but also somewhat conventional. For this new series, I wanted to try something less conventional—mouth-driven interaction.

I used the FaceMesh model in ml5.js. This model can take a webcam feed as an input and detect 468 keypoints of facial landmarks. Conveniently, ml5.js offers a very simple way to access a subset of the keypoints, such as the ones of lips. However, I noticed one of the keypoints was missing, which I believe originated an issue in TensorFlow.js (the library that ml5.js is based on). I subsequently reported this issue to the [ml5.js team](https://github.com/ml5js/ml5-next-gen/issues/107) and the [TensorFlow.js team](https://github.com/tensorflow/tfjs/issues/8221). The ml5.js team addressed this very quickly with a temporary fix. Meanwhile, I created my own arrays of keypoints as I wanted to separte the interior and exterior contour of the lips.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240316-daily-experiment-ml5-facemesh-mouth-contour-1080p@60fps_compressed-clip.mp4" type='video/mp4'>
</video>

To emphasize the mouth as the controller, I dynamically scaled the lip contours to always fit the canvas, no matter the direction or distance of detected face. I also did not want to leave the canvas blank when there was no face detected, so I recorded the keypoints of a neutural face and used them as the default placeholder. Furthermore, to create a smooth experience, I was using an interporlation function so that noises and jitters in the tracking were reduced signicantly.

<video width="100%" preload="auto" autoplay playsinline loop muted>
  <source src="/media{{ page.url }}20240317-daily-experiment-ml5-facemesh-large-mouth-1080p@60fps_compressed-clip.mp4" type='video/mp4'>
</video>

With a well developed visual, it was finally time to focus on the mapping of mouth movements to the sythesizer parameters. I chose to use the FMSynth built into the Tone.js library as it offered a lot of flexibilty.

After numerous experimentations, I landed on these controls:

The opening and closing of mouth triggers the start and end of sythesized sound. The pitch of the sound depends on the tilt of the detected face before triggering the start.

<video width="100%" preload="auto" autoplay playsinline loop muted controls>
  <source src="/media{{ page.url }}20240319-daily-experiment-ml5-facemesh-open-mouth-and-tilt-head-to-synth-1080p@60fps_compressed-clip.mp4" type='video/mp4'>
</video>

Once a sound synthesis starts, the opening of the mouth changes the volume and tilting your head clockwise or counter-clockwise detunes the sound (tilting also changes the frequency of the vibrato effect, which was added later).

<video width="100%" preload="auto" autoplay playsinline loop muted controls>
  <source src="/media{{ page.url }}20240321-daily-experiment-ml5-facemesh-open-mouth-and-tilt-head-to-synth-with-detuning-1080p@60fps_compressed-clip.mp4" type='video/mp4'>
</video>

Similarly, shaking your head left or right changes the harmonicity of the playing sound, and lifting or lowering your chin changes the modulation index.

<video width="100%" preload="auto" autoplay playsinline loop muted controls>
  <source src="/media{{ page.url }}20240322-daily-experiment-ml5-facemesh-open-mouth-and-shake-head-to-change-harmonicity-1080p@60fps_compressed-clip.mp4" type='video/mp4'>
</video>

With a combination of these movements, the synthesizer produces some pretty eerie sounds, quite suitable for this mouth-focused visual. Unmute the video below to hear the sound.

<video width="100%" preload="auto" autoplay playsinline loop muted controls>
  <source src="/media{{ page.url }}20240325-daily-experiment-ml5-facemesh-open-mouth-synth-with-adjustable-vibrato-1080p@60fps_compressed.mp4" type='video/mp4'>
</video>

Finally, you can try a [Live Demo](https://editor.p5js.org/jackbdu/full/jmvG6ZQwR).
