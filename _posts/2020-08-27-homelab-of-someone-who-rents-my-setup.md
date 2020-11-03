---
layout: post
title: Homelab of someone who rents | My setup
---

If you browse r/homelab you would see a myriad of amazing homelabs, which is great unless you rent, can’t add proper cabling to the house/flat, can’t spend much money or do not have enough space for all equipment. My setup was primarily created due to my interest in different tech, improving security as well as a result of the requirements mentioned above.

### What is a homelab?

Homelab is a place/environment at home that allows you to implement, learn and test different technologies. Some examples of what people run in their homelabs:
[https://www.reddit.com/r/homelab/comments/3usg1y/what_vmservices_are_you_running/](https://www.reddit.com/r/homelab/comments/3usg1y/what_vmservices_are_you_running/)
[https://www.reddit.com/r/homelab/comments/dzjecg/what_services_are_you_guys_running_in_your_home/](https://www.reddit.com/r/homelab/comments/dzjecg/what_services_are_you_guys_running_in_your_home/)
Check this out: [https://www.reddit.com/r/homelab/comments/d0oahc/my_not_so_humble_homelab_is_finally_complete/](https://www.reddit.com/r/homelab/comments/d0oahc/my_not_so_humble_homelab_is_finally_complete/)

### Why have a homelab?
Overall having a homelab is about learning and improving quality of life for me. Also it is about:

- Automation — there are things you want automated, homelab can take care of that
- Potential security improvement — I know some people who browse the internet from dedicated VMs that roll to a “clean” state and update daily for example.
- Freedom to break things without worrying as much,
- Improvements to your quality of life :)
- Some people out there aim to be independent from online service providers and run their own mail server, storage etc.
There are some disadvantages to having a homelab, to name a few:

- Time consuming — for some people its nearly a part-time job
- Money — good hardware can cost good money, Dell PowerEdge T440 starts at £1300 for example

### My setup

![Network diagram]({{ site.url }}/public/images/2020/homelab.png)
### Services
Kali VM — https://www.kali.org/
FreeNAS — https://www.freenas.org/
Plex media server — https://www.plex.tv/en-gb/media-server-downloads/
Zabbix — https://www.zabbix.com/
GitLab with two GitLab runners — https://about.gitlab.com/
OSSEC (in progress) — https://www.ossec.net/
Various VMs that are not in use 24/7
Kali
Used for bug bounties mainly as well as testing, example
https://twitter.com/alikhan_uzakov/status/1294026520965582851
FreeNAS
NAS for file storage and laptop backup.
Plex media server
Local media server, I like rewatching some of the TV shows I purchased a while ago.
Zabbix
VM monitoring and alerting, something I am planning to improve in the near future
OSSEC
OSSEC is HIDS — Host based detection system, work in progress.
Hardware
For the network part I went with Ubiquiti, chose UDM (Unifi Dream Machine) device https://store.ui.com/collections/routing-switching/products/unifi-dream-machine. It plays a role of my router, switch and security gateway. While there are a number of disadvantages in “all-in-one devices” this is the optimal choice for me as it’s likely I might be moving houses and my current place doesn’t have enough space for all the required hardware.
