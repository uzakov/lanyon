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
List of VMs/services I run:
- Kali VM — [https://www.kali.org/](https://www.kali.org/)
- FreeNAS — [https://www.freenas.org/](https://www.freenas.org/)
- Plex media server — [https://www.plex.tv/en-gb/media-server-downloads/](https://www.plex.tv/en-gb/media-server-downloads/)
- Zabbix — [https://www.zabbix.com/](https://www.zabbix.com/)
- GitLab with two GitLab runners — [https://about.gitlab.com/](https://about.gitlab.com/)
- OSSEC (in progress) — [https://www.ossec.net/](https://www.ossec.net/)
- Various VMs that are not in use 24/7

#### Kali
Used for bug bounties mainly as well as testing, example [https://twitter.com/alikhan_uzakov/status/1294026520965582851](https://twitter.com/alikhan_uzakov/status/1294026520965582851)
#### FreeNAS
NAS for file storage and laptop backup.
### Plex media server
Local media server, I like rewatching some of the TV shows I purchased a while ago.
#### Zabbix
VM monitoring and alerting, something I am planning to improve in the near future
#### OSSEC
OSSEC is HIDS — Host based detection system, work in progress.

### Hardware
For the network part I went with Ubiquiti, chose UDM (Unifi Dream Machine) device [https://store.ui.com/collections/routing-switching/products/unifi-dream-machine](https://store.ui.com/collections/routing-switching/products/unifi-dream-machine). It plays a role of my router, switch and security gateway. While there are a number of disadvantages in “all-in-one devices” this is the optimal choice for me as it’s likely I might be moving houses and my current place doesn’t have enough space for all the required hardware.

![Ubiquiti UDM]({{ site.url }}/public/images/2020/20200825_210824.jpg)
*My UDM, I call it “Smol Battle Station” — its small but as good and strong as a battlecruiser from StarCraft. I really love the design, it’s very minimal, clean and actually reminds me of EVE from WALL-E cartoon.*

Alternatively, I could have gone with custom flashing a router with dd-wrt, open-wrt or tomato, buying a dedicated switch. There are a number of reasons I did not do that, to name a few:

1. There is a chance that router will be bricked during flashing
2. I currently have limited free time, dd-wrt always takes time (read forums for example, some builds were unstable etc)
3. UDM offers everything I need at the moment

If you want to see a good guide how to do network segregation and segmentation with a router that is flashed with dd-wrt check out the guide from Bishop Fox [https://labs.bishopfox.com/industry-blog/an-updated-guide-to-do-it-yourself-network-segmentation](https://labs.bishopfox.com/industry-blog/an-updated-guide-to-do-it-yourself-network-segmentation)

### Server

For my server I went with a used PC, the specs are:
* 6th gen i7
* 48GB DDR RAM
* 1TB HDD and 256GB SSD
It hosts my VMWARE ESXi and corresponding VMs
![Homelab sticker]({{ site.url }}/public/images/2020/sticker-homelab.png)

### Networking

One of the key requirements for my homelab was simplicity and best value for time, following the Pareto principle(80/20). My local network is separated and segregated into various parts, talked about below.

One of the things I did was deciding not to allow remote access for the majority of things I run, to save time I would have to spend maintaining adequate security. They can still be accessed locally and can reach the internet.

#### Guest network
This network is used by people visiting the house.
#### Homelab network
This network containing homelab: ESXi host and VMs
#### Trusted devices network
This network is for devices that are more closely maintained, more trusted
#### IoT/Other
This network is for Internet of Things devices or ones that are hard to patch, examples are home smart plugs, sensors.

Here are the firewall policies I have set:

1. No outside to inside traffic
2. “IoT/Other”, “Guest networks” can’t reach other networks and can only talk with the internet
3. “Trusted” can reach “Homelab”
4. Homelab VMs can talk to each other

Some points to keep in mind: you can do micro segmentation, above example is not perfect, far from it, see what suits you. Additionally you can do MAC filtering but that does not give you a great deal (if any) of security as anyone can easily change their MAC address. All VMs could take good use of things mentioned in [https://medium.com/@uzakov/pretty-good-setup-pgs-4d3b58b4341a](https://medium.com/@uzakov/pretty-good-setup-pgs-4d3b58b4341a)

If you are interested to know more, check the links below.

[https://robpickering.com/ubiquiti-configure-micro-segmentation-for-iot-devices/](https://robpickering.com/ubiquiti-configure-micro-segmentation-for-iot-devices/)
[https://nguvu.org/pfsense/pfsense-baseline-setup/](https://nguvu.org/pfsense/pfsense-baseline-setup/)
[https://joshspicer.com/homelab](https://joshspicer.com/homelab)
[https://www.homelabrat.com/](https://www.homelabrat.com/)
