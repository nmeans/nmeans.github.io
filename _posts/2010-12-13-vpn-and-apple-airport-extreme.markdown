---
layout: post
title: VPN and Apple's Airport Extreme
category: posts
---
Video baby monitors and 2.4 GHz wireless networking do not play well together. This is the fact that led to my purchase of a refurbished Apple Airport Extreme from Best Buy a few weeks ago. I still have a few devices that are 802.11g-only, so going simultaneous dual-band was the only way I could get reliable performance for my computers and keep all my legacy kit at least marginally online.

It was about a week after installing the Airport Extreme and living in no-interference bliss that I realized my VPN connection to my hosting provider wasn't working. We host <strike>[newenough.com](http://www.newenough.com/)</strike> [MotorcycleGear.com](http://www.motorcyclegear.com/) with [Softlayer](http://www.softlayer.com/), and thanks to their wonderful private network infrastucture, I'm able to firewall off all ports except 80 and 443 from the public Internet. To SSH to any of our boxes, I need to connect through Softlayer's VPN gateway into the private network.

I couldn't. The VPN would authenticate just fine, but I wasn't receiving any traffic. If I changed my VPN settings to "Send all traffic over VPN connection", I could connect to NE's servers, but since Softlayer's private network is completely disconnected from the public Internet, I had no network access other than to my servers. 

But this was only when I was at home. Everything worked fine when I was at the office, and everything had worked fine from home before installing the Airport Extreme. I had my culprit.

I sent several emails back and forth with Softlayer's support department asking about oddities of working with their VPN and Apple networking gear, but I'm not sure anyone in their first-line tech support even understood the specifics of the problem. I also spent 30 minutes on the phone with Applecare, but they had no answers either.

Once I got a response from Reed F. in Softlayer's second level support department, though, the solution became obvious. Reed's excellent response:
> If I am not mistaken, most Apple gear tends to use a 10.x.x.x addressing schema, if
> this is the case, then it will conflict with the routes that are provided from the VPN
> device.

(As an aside, Softlayer's support department constantly amazes me. They're patient with the most mundane requests, always fast to respond, and driven to solve even issues like this where the problem is obviously not on their end. I can't recommend them highly enough if you're looking to lease a server.)

Apple's wonky default 10.0.1.x IP address scheme was conflicting with the 10.x.x.x scheme used by Softlayer's VPN. Softlayer chose that scheme, I'm sure, because most consumer network gear distributes 192.168.x.x IP addresses by default.

A quick switch of the Airport Extreme to using 192.168.1.x IP addresses and all was working as expected. If you're having trouble getting a VPN to work from behind an Airport Extreme (or Airport Express), that's definitely the first thing to try.
