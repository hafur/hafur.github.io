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

Let me give you an idea of w