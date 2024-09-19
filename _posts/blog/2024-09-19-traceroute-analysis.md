---
layout: post
title: Traceroute Analysis
categories: blog
tags: itp understanding-networks
description:
published: true
---

This week, I’m exploring the paths of my network transactions using the traceroute utility. I started with the websites that I visit most regularly, such as google.com and instagram.com. I wasn’t sure what I would do to analyze the traceroute outputs, so I decided to take screenshots of every website that I traced. Here are a couple of examples:

| ![](/media{{ page.url }}screenshot-terminal-window-traceroute-nyu.edu.png) |
| :------------------------------------------------------------------------: |
|        Screenshot of Terminal Window of `traceroute nyu.edu` Output        |

| ![](/media{{ page.url }}screenshot-terminal-window-traceroute-youtube.com.png) |
| :----------------------------------------------------------------------------: |
|        Screenshot of Terminal Window of `traceroute youtube.com` Output        |

It wasn’t until a few days later that I realized keeping the outputs as text files instead of screenshots would be a lot more useful, as it would be a lot easier to copy and paste the results, IP addresses in particular, from a text file to do any further analysis. That was also when I realized that I spent a lot of time typing out the commands and waiting for the results. More often than not, the tracing leads to endless unknown hosts, which means a lot of time has been wasted on waiting and checking.

I thought this was a perfect opportunity to write a shell script to automate the process. That way I can simply run the shell script whenever I connect to a new network, and work on my other stuff while the traceroute runs in the background. With some help from OpenAI’s ChatGPT, I was able to create a [shell script](https://gist.github.com/jackbdu/75a5c5579fb02646496169fe0f8eb2a2) that reads hostnames from a separate text file, runs traceroute to them in background, logs the traceroute outputs to separate text files for each host, and reports the progress until all traceroute processes are completed.

| ![](/media{{ page.url }}screenshot-terminal-window-vi-batch-traceroute.sh.png) |
| :----------------------------------------------------------------------------: |
|             Screenshot of Terminal Window of `batch-traceroute.sh`             |

I came up with a list of 25 sites that I am interested in tracing and saved them all in a text file. Afterwards, it was pretty much a painless experience to trace these many sites. I traced these websites on NYU Network at both 370 Jay St and at the Bobst Library, on my mobile network (Visible) at a restaurant as well as at home. I also tried it while connecting to NYU VPN at home, both NYU New York VPN and NYU Shanghai VPN.

| ![](/media{{ page.url }}screenshot-finder-window-traceroute-logs.png) |
| :-------------------------------------------------------------------: |
|         Screenshot of Finder Window of `traceroute` Log Files         |

It finally gets to the fun part—analyzing. The actual work isn’t as fun as I wish it were. I manually analyzed a few log files, using the whois utility to check the information on many of the IP addresses that appeared in the logs. While it was helpful to see the path it took for my laptop to connect to the various hosts, it was far from efficient. One possible solution is to write some kind of scripts to automate the process and maybe even generate charts for me based on the log files, but it would still take a lot of time. I’m totally interested in building it one day, but for the time being, I came up with another solution that boosts my efficiency.

Since all logs are saved into text files, I can now run various commands on them to help me better understand the paths. First, I organized the logs into folders based on the network environment under which the traceroute utility was run. Then, I’d open up a log file I’m interested in, and use the grep utility to search within all log folders the IP addresses that appeared in this log file one by one. This way, from the IP addresses closest to in the path to the IP address farthest away in the path, I got to see which other files contain the same IP address. That helps me to understand whether an IP address is associated with my network environment, or with a target host. It also helps me to see which IP addresses are shared among some of the paths.

| ![](/media{{ page.url }}screenshot-terminal-window-grep-utility-on-various-ips.png) |
| :---------------------------------------------------------------------------------: |
|       Screenshot of Terminal Window of `grep` Output on Various IP Addresses        |

This process helped me identify which IP addresses are of my interest so I could run whois on them to find out more. For instance, I found out that `199.109.105.5`, which appeared in 8 logs across two different locations, is associated with NYSERNet.

| ![](/media{{ page.url }}screenshot-terminal-window-whois-199.109.105.5.png) |
| :-------------------------------------------------------------------------: |
|        Screenshot of Terminal Window of `whois 199.109.105.5` Output        |

Whereas `99.109.107.202`, which also appeared in these 8 logs, is associated with AT&T (even though the hostname only indicates NYSERNet).

| ![](/media{{ page.url }}screenshot-terminal-window-whois-99.109.107.202.png) |
| :--------------------------------------------------------------------------: |
|        Screenshot of Terminal Window of `whois 99.109.107.202` Output        |

And of course, unsurprisingly, `17.1.146.86` is associated with Apple.

| ![](/media{{ page.url }}screenshot-terminal-window-whois-17.1.146.86.png) |
| :-----------------------------------------------------------------------: |
|        Screenshot of Terminal Window of `whois 17.1.146.86` Output        |

It was also interesting to see that when connected to NYU VPN at home, most traces are hidden from traceroute except for a few NYU-affiliated hosts.

| ![](/media{{ page.url }}screenshot-terminal-window-vi-nyu.edu-traceroute-log.png) |
| :-------------------------------------------------------------------------------: |
|          Screenshot of Terminal Window of `traceroute nyu.edu` Log File           |

Finally, I tried mapping some of the traceroute outputs with [traceroute mapper](https://stefansundin.github.io/traceroute-mapper/). The most interesting ones to me are the ones going between the US and China. Here are four different maps to qq.com in different network environments:

| ![](/media{{ page.url }}screenshot-browser-window-traceroute-mapper-qq.com-on-optimum-network.png) | ![](/media{{ page.url }}screenshot-browser-window-traceroute-mapper-qq.com-on-visible-mobile-network.png) |
| :------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------: |
|                               `traceroute qq.com on Optimum Network`                               |                               `traceroute qq.com on Visible Mobile` Network                               |

| ![](/media{{ page.url }}screenshot-browser-window-traceroute-mapper-qq.com-on-nyu-network.png) | ![](/media{{ page.url }}screenshot-browser-window-traceroute-mapper-qq.com-on-nyush-vpn-network.png) |
| :--------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------: |
|                               `traceroute qq.com` on NYU Network                               |                               `traceroute qq.com` on NYU Shanghai VPN                                |
