---
layout: post
title:  "What do I really need?"
tag: cloud oracle
---

I started looking into the services that my domain provider offers me. With their latest service 'optimization', I lost the capability to log into my server using ```ssh```.

Maybe it is time to switch to a new provider. But what do I actually need?
Mandatory:
- Email
    - Aliases. I use a lot of aliases and this is a must
    - Acocunts. I do not need 100 but up to 10 shuld be sufficient
- Server
    - ssh access
- Management
    - DNS management that includes A-record, CNAME, MX records, etc.

Nice to have:
- SSL certificates

No need for:
- website builder
- online shop
- analytics

Looking at the above list, I have quite simple and straight-forward requirements which mainly focus around email.
DNS management and ssh access is an interesting point: I do not need necessarily ssh access if I have full acces to the DNS configuration because I can point my domain to any IP, i.e. any server (for which I actually have ssh access). 

It is a bit daring since I would be responsible to keep that server up-and-running, make sure that patches are applied, etc. Now I am not running a business so I can live with the fact that my homepage might not be available 24x7 on 365 days a year.

I guess the only way of knowing what this all means is actuyally tryign it out. 
Oracle offers has an ['Always Free'](https://www.oracle.com/cloud/free/) offer which might be one piece of my overall revisit of what I actually need from a domain provider.
I get (among other things) two virtual machines from Oracle for free. 

So - next steps are:
1. Get an Oracle 'always free' cloud account
2. Set up a web server in OCI
3. Update the A-records of my domain provider

...and then we see how all of that goes...

