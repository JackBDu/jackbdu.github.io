---
layout: post
title: Networked Game Controller
categories: blog
tags: itp understanding-networks
description:
published: true
---

In the Understanding Networks class this week, Tom Igoe showed the class the [Ball Drop Game](https://tigoe.github.io/BallDropGame/). In Tom’s own words, the Ball Drop Game is “a multiplayer game in which players collaborate to keep a ball from hitting the ground”. To play this game, all players need to be on the same network as the game, which is a networked application written in Processing. When we played it for the first time, we all connected to the game using the `netcat` utility via a command line interface. The `netcat` utility established TCP (Transmission Control Protocol) connections from our laptops to Tom’s laptop, where the Ball Drop Game server application was running.

There were some constraints that made the game particularly challenging. First off, we were controlling our paddle by typing a directional command and pressing the returning key, which was far from intuitive for most of us. Secondly, we did not have fine control over the horizontal movement of the paddle. The paddle moves left and right by increment equivalent to half of its own size. Lastly, the vertical movement of the paddle was super slow, so it was pretty difficult for us to move down quickly to save a ball. Lastly, we can only score when the ball bounces on a new paddle. In other words, the score stays the same if the ball keep bouncing on the same paddle.

Fortunately, that was not the only way to play this game. We were tasked to build a physical controller for this game!

I decided to use a [Seeed Studio XIAO ESP32S3](https://www.seeedstudio.com/XIAO-ESP32S3-p-5627.html) board for this project because the XIAO series boards have been recommended to me by numerous friends for its affordability and super compact size. I bought a few of them over the summer, so I thought this would be a good opportunity to try one of them out.

I started with a minimal prototype on a breadboard, with five buttons and five LEDs. One of the buttons was for initiating a connection to the server application while the other four buttons were for four directions. The LEDs were there to indicate the connection status and to offer visual feedback when directional buttons were pressed.

|           ![](/media{{ page.url }}IMG_6575.jpg)           |
| :-------------------------------------------------------: |
| Networked Game Controller Minimal Prototype on Breadboard |

With the help of Tom’s [example code](https://github.com/tigoe/BallDropGame/tree/main/BallDropWifiJoystickClient), which was written for one button and a joystick, it was fairly easy to modify the code to get the prototype to work.

I considered designing and 3D printing a custom case, but I found something even better\! On the ITP/IMA junk shelf, I found a cute egg-shaped controller. I had no idea what the controller was originally for, but it had quite an ergonomic grip and it even came with a long antenna. One of the biggest issues, however, was that the controller only came with two buttons, up and down. Upon opening the controller, I thought it would be a fun challenge to try to fit four buttons in it.

| ![](/media{{ page.url }}IMG_6571.jpg) | ![](/media{{ page.url }}IMG_6573.jpg) |

I was a bit disappointed that I could not find the right buttons at the ITP/IMA shop, but I was lucky enough to find four in my own collection at home.

After some careful planning and hours of soldering and tweaking, I was pretty happy that I was able to fit most components within the casing.

| ![](/media{{ page.url }}IMG_6604.jpg) | ![](/media{{ page.url }}IMG_6607.jpg) |

<table style="width: 100%;">
  <thead>
  <tr>
  <th>
    <video controls width="100%" preload="auto">
      <source src="/media{{ page.url }}IMG_6608_720p.mp4" type='video/mp4'>
    </video>
  </th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <th>
  Networked Game Controller - Testing
  </th>
  </tr>
  </tbody>
</table>

I left the back of the controller half open so I could easily attach and detach my XIAO microcontroller as well as accessing its USB-C port. I did not end up using the controller the antenna as it was a bit unncessary.

| ![](/media{{ page.url }}20240926-67_03102.jpg) |

With the help of a bit of hot glue, the casing worked pretty well with the four buttons underneath. The LEDs also lit up very nicely through the plastic.

I had to also revise the code so that pressing all four buttons initiates the connection (or disconnection). In addition, I prioritized accuracy over speed by only sending one directional command at a time when a button was pressed.

<table style="width: 100%;">
  <thead>
  <tr>
  <th>
    <video controls width="100%" preload="auto">
      <source src="/media{{ page.url }}img_6615_720p.mp4" type='video/mp4'>
    </video>
  </th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <th>
  Networked Game Controller - Demo
  </th>
  </tr>
  </tbody>
</table>

When we played the game again in class with our physical controllers, the score improved significantly! We managed to block the ball to one side of the wall and keep scoring by alternating between two players :)

| ![](/media{{ page.url }}IMG_6620.jpg) |
