---
layout: post
title: SSH reverse proxy
---

Discovered today that SSH reverse proxy option allows bypassing firewalls. It's helpful in connecting to devices sitting behind a router with no port forwarding setup. E.g. If I need to SSH to my friend's laptop, who has no port forwarding setup, I can ask him to SSH to my router using command:

>    ssh -NR 8000:localhost:22 root@MY-ROUTER-IP

Then I login to my router and the following command gives me shell access to the his machine:

>    ssh -p 8000 root@localhost

Although, I setup SSH tunnel to my router in my example above, this is not required. This tunnel can be set up to any machine

Please note that while using dropbear keys for password-less authentication between the two routers, the commands need to specify the dropbear identity key also.
