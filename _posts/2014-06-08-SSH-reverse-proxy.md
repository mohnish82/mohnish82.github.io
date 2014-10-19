---
layout: post
title: SSH reverse proxy
---

Discovered today that SSH reverse proxy option allows bypassing firewalls. It's helful in connecting to devices sitting behind a router with no port forwarding setup. So, let’s say I need to SSH to my friend's laptop, who has no port forwarding setup in his router. I can ask him to SSH to my router using command:

>    ssh -N 8000:localhost:22 root@MY-ROUTER-IP

Then I login to my router and the following command gives me shell access to the remote laptop:

>    ssh -p 8000 root@localhost

Although, I setup SSH tunnel to my router in my example above, this is not required. You can setup the tunnel to your laptop, but remember to forward SSH traffic to your laptop in your router settings.

Please note that if you use dropbear keys for password-less authentication between the two routers, the commands need to specify the dropbear identity key also.
