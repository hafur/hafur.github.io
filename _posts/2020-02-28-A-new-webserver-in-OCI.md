---
layout: post
title:  "A new webserver in OCI"
tag: cloud oracle
---

As mentioned in the previous post, I will try to get my homepage set up on a webserver running on a virtual machine with in the Oracle Cloud Infrastructure.
Oracle is offering an 'Always free' account which comes with 2 VMs, a couple of databases and some other services. Interestingly, I can also get a Load Balancer which could help setting up some HA approaches by distributing the web server over two VMs.
But first things first: Lets start with one VM first

## Technical Details
There are a bunch of tutorials out there which describe how to set up a VM in OCI. It is no rocket science whatssoever. You need a Virtual Cloud Network (which can be set up automatically during the provisioning of the VM) and of you go. 
One thing to note though: I have used my own ssh key in the configuration process and did not opt for the option where Oracle provide

Let me give you an idea of what my OCI webserver comprises:
* Ubuntu 18.04 LTS
* nginx (I only knew Apache so nginx is a new experience)
* Let's encrypyt SSL certificate via Certbot

Pretty minimalist, I reckon. 
I will not go into details on how to set up all of that: Google is your friend. There is a ton of tutorials out there and all of the above is really straight forward.
The only thing that kept me busy for while was the security of this darn thing. I actually should not complain. Oracle claims that OCI is 'secure by default' and that is actually true. 
As part of their virtual cloud networking, Oracle provides a Network Security List to configure ingress and egress traffic to and from your services that are deployed in a particular Virtual Cloud Network (VCN). 
For my use case I require a rule that allows incoming traffic on TCP port 80 and 443. Really easy to set up as a matter of fact.
This is what the rule table looks like after I added my rules for port 80 and 443:

![My NSL](/assets/nsl.png)

Excited about how fast everything was set up and configured, I threw my shiny, new public IP at my browser of choise just to be completely shattered.
It did not work. I was expecting some default nginx welcome page but my browser would just return errors.

I checked the nginc config on the server, made sure I could do a curl on the localhost. All and everything was working - as long as I was doing the test on the actual server.

It took my some time (mainly because I ignored the documentation - RTFM? No not for me.
Remember: OCI is secure by default. That means that Oracle put an actual firewall on the Ubuntu image. As a matter of fact, every Linux distro you can use to fire up a VMs will have a firewall enabled by default. And the default configuration allows only ssh traffic!

Well - fair enough: I do know Ubuntu Firewall (that ```ufw``` thing). Would have been too easy. In OCI the images come with a proper ```iptables``` firewall config - which I do not know.

There is a bunch of information on ```iptables``` out there. Really! A lot! And I really feel it is a complex topic - naturally security is always a complex topic. 

To keep it short - here is the solution (I would not recommend this for a production system):
```sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 80 -j ACCEPT```
```sudo iptables -I INPUT 6 -m state --state NEW -p tcp --dport 443 -j ACCEPT```
```sudo netfilter-persistent save```

For reference: [OCI-Ubuntu-Apache Tutorial](https://docs.oracle.com/en-us/iaas/developer-tutorials/tutorials/apache-on-ubuntu/01oci-ubuntu-apache-summary.htm)

Horray! It is working! 

![OCI webserver architecture](/assets/Webserver.png)



Final step: Creating an DNS A-record for the IP address at my domain provider et voila: My homepage is now hosted on an 'always free' compute instance n Oracle Cloud Infrastructure.

Now I have to evaluate how robust this solution is.
I figure the main thing to worry about is maintenance of the webserver, i.e. applying patches etc.
We will see...



