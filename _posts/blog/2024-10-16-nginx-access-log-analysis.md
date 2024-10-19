---
layout: post
title: Nginx Access Log Analysis
categories: blog
tags: itp understanding-networks
description:
published: true
---

This week, I am continuing my network experiment with an Nginx setup on my AWS E2C virtual machine. I followed [How To Install Nginx on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04) to install nginx and [How To Secure Nginx with Let's Encrypt on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04) to get my free TLS/SSL certificate. The default Nginx page is currently available at [http://100.26.63.206/](http://100.26.63.206/) and it will most certainly become unavailable if you are reading this post more than a couple of months later. In addition, I set up two server blocks for [https://hi.jbd.lol/](https://hi.jbd.lol/) (with TLS/SSL certificate) and [http://ad.jbd.lol/](http://ad.jbd.lol/) (without TLS/SSL certificate), which are also likely to go away later, depending on whether or not I decide to keep the jbd.lol domain next year. Furthermore, I have an A Record pointing [www.ad.jbd.lol](http://www.ad.jbd.lol) to the IP same address as [http://ad.jbd.lol/](http://ad.jbd.lol/), and I have an URL Redirect Record pointing [www.hi.jbd.lol](http://www.hi.jbd.lol) to [https://hi.jbd.lol](https://hi.jbd.lol).

I used to manage a DreamHost Virtual Private Server (VPS) for work and I was mostly using its web dashboard. DreamHost’s abstraction made the whole web hosting process easy, but I was always curious what was going on under the hood. For instance, I remember there was a one-click button for adding and renewing the Let's Encrypt certificate. Now, I learned a more manual process for obtaining a certificate from Let’s Encrypt Certificate Authority and how certbot can be configured to renew the certificate automatically.

One of the most surprising things I found was that my domain started pointing to my Nginx page as soon as I added an A Record (Address Mapping Record) to my domain's DNS setting. I was surprised that there was no configuration needed in my Nginx setup. To further test out this idea, I configured a new A Record that points [http://alan.jbd.lol](http://alan.jbd.lol) to the IP address of Alan’s Nginx page (with his consent) and it worked. Does this mean anyone can point to my default Nginx page? There must be some configuration or protection setup we can do to avoid this\! Or should I simply disable the default page? I will leave these questions to Tome's class.

After leaving the server running for more than 24 hours, I found 603 requests in Nginx’s access log. One particular IP address `213.232.87.232` really stood out because it seemed to be strategically making many requests to files that potentially contain sensitive information, such as `/secrets.json`, `/server.key`, `/.ssh/id_ed25519`.

Below is a complete list of requests from this IP address:

```
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config.yml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/wp-admin/setup-config.php	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/server.key	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/backup.zip	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.svn/wc.db	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/user_secrets.yml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/etc/shadow	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.env.production	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/etc/ssl/private/server.key	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/wp-config.php	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config.json	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/secrets.json	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.ssh/id_ecdsa	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/	HTTP/1.1"	200	95	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config/database.php	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/_vti_pvt/service.pwd	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/api/.env	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/backup.sql	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/cloud-config.yml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/backup.tar.gz	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.git/HEAD	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.ssh/id_rsa	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/database.sql	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.env	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/server-status	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/_vti_pvt/authors.pwd	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/phpinfo.php	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config.xml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/dump.sql	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config/production.json	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config.yaml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/config.php	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/docker-compose.yml	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.vscode/sftp.json	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/web.config	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/feed	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/_vti_pvt/administrators.pwd	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.ssh/id_ed25519	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.kube/config	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
213.232.87.232	-	-	[15/Oct/2024:09:47:49	+0000]	"GET	/.aws/credentials	HTTP/1.1"	404	134	"-"	"Go-http-client/1.1"
```

Running `whois` on this IP shows that it is associated with PacketHub S.A. and NordVPN. The [relationship between the two seems unclear](https://whoisyourvpn.com/network/packethub/). Of course, whoever was running this malicious operation is way too smart to expose their own IP address.

Below is the complete output from `whois`:

```
% IANA WHOIS server
% for more information on IANA, visit http://www.iana.org
% This query returned 1 object

refer:        whois.ripe.net

inetnum:      213.0.0.0 - 213.255.255.255
organisation: RIPE NCC
status:       ALLOCATED

whois:        whois.ripe.net

changed:      1993-10
source:       IANA

# whois.ripe.net

inetnum:        213.232.87.0 - 213.232.87.255
netname:        NORDVPN-L20190921
descr:          Packethub S.A.
country:        NL
org:            ORG-PS409-RIPE
admin-c:        AG25300-RIPE
tech-c:         AG25300-RIPE
status:         ASSIGNED PA
mnt-by:         de-tt1data-1-mnt
mnt-routes:     de-tt1data-1-mnt
created:        2019-09-21T12:49:37Z
last-modified:  2020-12-19T11:43:54Z
source:         RIPE

organisation:   ORG-PS409-RIPE
org-name:       Packethub S.A.
org-type:       other
address:        Office 76, Plaza 2000, 50 Street and Marbella, Bella Vista
address:        Panama City
address:        Panama
phone:          +5078336503
admin-c:        AG25300-RIPE
tech-c:         AG25300-RIPE
abuse-c:        PSID1-RIPE
mnt-by:         TERRATRANSIT-MNT
mnt-ref:        TERRATRANSIT-MNT
mnt-ref:        de-net1-1-mnt
mnt-ref:        de-kiservices-1-mnt
mnt-ref:        de-kis2-1-mnt
mnt-ref:        de-tt1data-1-mnt
mnt-ref:        de-stumpner-1-mnt
mnt-ref:        de-wn-1-mnt
created:        2020-12-19T10:54:00Z
last-modified:  2020-12-19T11:37:56Z
source:         RIPE # Filtered

person:         Alina Gatsaniuk
address:        Office 76, Plaza 2000, 50 Street and Marbella, Bella Vista
address:        Panama City
address:        Panama
phone:          +5078336503
nic-hdl:        AG25300-RIPE
mnt-by:         TERRATRANSIT-MNT
created:        2020-12-19T10:53:01Z
last-modified:  2020-12-19T10:53:01Z
source:         RIPE # Filtered

% Information related to '213.232.87.0/24AS136787'

route:          213.232.87.0/24
origin:         AS136787
mnt-by:         de-tt1data-1-mnt
created:        2022-04-22T12:54:46Z
last-modified:  2022-04-22T12:54:46Z
source:         RIPE

% Information related to '213.232.87.0/24AS49981'

route:          213.232.87.0/24
origin:         AS49981
mnt-by:         de-tt1data27-1-mnt
mnt-by:         mnt-de-tt1data63-1
mnt-by:         mnt-de-tt1data38-1
mnt-by:         de-tt1data-1-mnt
mnt-by:         mnt-de-tt1data36-1
mnt-by:         mnt-de-tt1data32-1
created:        2019-11-22T10:47:15Z
last-modified:  2019-11-22T10:47:15Z
source:         RIPE

% This query was served by the RIPE Database Query Service version 1.114 (SHETLAND)
```

Similarly, two other IP addresses, `209.38.248.17` and `64.226.78.121` made numerous requests to files such as `/.DS_Store`, `/.env`, and `/.git/config`. This made me wonder, “What kind of sensitive information is stored in `.DS_Store` files?” I know they are generated by macOS’s Finder and I came across them way too often in people’s GitHub repositories. Most people seem to ignore them (even though they probably should have made git to do so instead). After some research, I found that [`.DS_Store` could potentially contain passwords or SSL certificates](https://hackernoon.com/what-happened-after-i-scanned-26-million-domains-for-exposed-ds_store-files). For those of you who tend to accidentally include `.DS_Store` in git commits, please [let git ignore it globally](https://dev.to/lpheller/quickly-ignore-dsstore-files-globally-ecd).

Both `209.38.248.17` and `64.226.78.121` appear to be associated with DigitalOcean, LLC. In particular, the latter is associated with TunnelBear, a VPN service.

Finally, I found one other IP address `8.211.162.45` that made interesting requests to my server. It seems to be requesting DNS records, but I am not entirely sure why. This IP address appears to be associated with Alibaba Cloud (Singapore) Private Limited.

![A screenshot of browser window showing nginx access log in Google spreadsheet](/media{{ page.url }}screenshot-browser-google-spreadsheet-nginx-access-log.png)

One thing all requests from these four IP addresses have in common is that the requests were made through Go-http-client. I wonder why it is so popular among these people.
