---
layout: post
title: SSH reverse proxy
---

Discovered today that SSH reverse proxy option allows bypassing firewalls. So, let’s say my father wants me to troubleshoot something on his laptop. I ask him to setup reverse SSH to my router using command:

>    ssh -N 8000:localhost:22 root@MY-ROUTER-IP

Then I login to my router and the following command gives me shell access to the remote laptop:

>    ssh -p 8000 root@localhost

* If you use dropbear keys for password-less authentication between the two routers, the commands need to specify the dropbear identity key also.
