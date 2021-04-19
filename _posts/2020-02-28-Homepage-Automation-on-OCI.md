---
layout: post
title:  "Self-hosting for more Flexibility"
tag: cloud 
---

Every company is adjusting services and products they are offering - usually that comes at a price, namely the actual _value for what you get_. Usually, you get less value for the same price.

Companies like to reduce the content but maintain the same price. There are websites in Germany which document this behaviour, for example [VZHH](https://www.vzhh.de/themen/mogelpackungen/weniger-drin-preis-gleich-die-neuesten-mogelpackungen).

Why am I mentioning this? Well, my domin provider of choice [one.com](https://www.one.com) is guilty of the same unfortunate behaviour. I have been a customer for over 15 years and I have seen changes and adjustments to their services - which is normal. Unfortunately, with every adjustment it seems I am losing more and more functionality to an extend where I am questioning the price-value ratio.
In my previous post, I described how I am revaluating my current set up. The first step is to decouple my homepage, i.e. the webserver from my domain provider. I will use Oracle Cloud Infrastructure to host my web server and create an DNS A-Record to point my domain to the IP address of that web server.
This is what it will look like:

![Future Architecture](/assets/homepage.png) 

In the next few posts, I will describe the process of migrating my homepage to a web server which I have to maintain. This includes setting up the network, securing the whole server and the webpage, etc.

First step: Get the virtual machine up and running.!