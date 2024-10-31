---
layout: post
title: RESTful Web Microservices
categories: blog
tags: itp understanding-networks
description:
published: true
---

This week, I am experimenting with RESTful web microservices. I set up an nginx server block at [https://api.jbd.lol](https://api.jbd.lol). I wrote a Node.js script based on Tom Igoe's [NodeWithNginx](https://github.com/tigoe/NodeExamples/tree/main/NodeWithNginx) to provide three microservices.

The first one is [apps/date](https://api.jbd.lol/apps/date), which displays the current date on the server. I am using the `figlet` utility to convert the date text to ASCII art to make it a bit more fun.

![](/media{{ page.url }}screenshot-browser-microservices-date.png)

The second one is [apps/blog](https://api.jbd.lol/apps/blog), which displays a random blog post of mine for understanding networks. If you refresh the page, it will show a randomly selected page each time.

![](/media{{ page.url }}screenshot-browser-microservices-blog.png)

The last one is [apps/weather](https://api.jbd.lol/apps/weather), which displays weather information of Brooklyn, NY. I am using OpenWeather's API for showing the current weather.

![](/media{{ page.url }}screenshot-browser-openweather-api-current-weather.png)

In addition, I included the ability to use [apps/weather?lat=xx.xx&lon=xx.xx](https://api.jbd.lol/apps/weather?lat=40.68&lon=-73.94) to specify a specific latitude and longitude.

![](/media{{ page.url }}screenshot-browser-microservices-weather.png)
