---
title: "Getting started with Ansible"
header:
    image: /assets/images/posts/ansible/ansible.jpg
    teaser: /assets/images/posts/ansible/ansible-th.jpg
toc: true
toc_label: "Contents"
toc_icon: "Book"  
categories:
  - blog
tags:
  - DevOps
  - Infrastructure as Code
  - PowerShell
  - Ansible
---
Talk about infrastructure as code
Comment on understood the concept, briefly played with Puppet / DSC was turned off by the agent based approach etc. Ansible being completely agentless really caught my attention. Twiiter noise.

Some linux skill required - hadn't realised it but over the last 12 months operating from a mac and playing with docker etc my linux skills had developed enough to not be scared off.

Using docker to setup a dev environment

Josh duffney book.

Always aware of wirm and it use within powershell remoting, but with windows it just worked. Ansible uses winrm but requried understand how it worked from a deeper level. Initally what i found in the docs and online suggested that Kereberos with SSL is what was required, this opened up some greater challehes and required some manual configuration on the end point to get up and running, which i felt went against the IaC concept.

Also understood more about the winrm / firewall setup of windows server out of the box.

It wasn't until i discovered the use message enryption flag that it all started to fit together.

No i have only done some minor things so far, add to domain, mange some software with choco, built a domain controller, some windows patching so very much a nood when it comes to ansible but it can definitely can now see the benefit and wil be continuing on this path.  expect a few more ansible blog posts in the future.