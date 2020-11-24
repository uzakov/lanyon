---
layout: post
title: Pretty Good Setup (PGS)
---
<div class="message">
  See original post with 23k views on <a href="https://medium.com/@uzakov/pretty-good-setup-pgs-4d3b58b4341a">Medium</a>
</div>

For a while I had this security guide written for myself and finally decided to share it with everyone. This post will be a semi-detailed guide on what, why and how to secure your machine. Hope you enjoy it :)

### Full manual
The reason why I called it Pretty Good Setup is that the security of this setup is pretty good for many situations, it’s good for the vast-majority of people and covers a good amount of threats.

#### Table of contents

1. Securing the BIOS
2. Move to user friendly GNU/Linux OS
3. Enable automatic security updates
4. Firewall
5. Browser extensions and settings
6. Cover your camera
7. Install a VPN
8. Use a password manager
9. Use a Virtual Machine
10. Encrypt important files

#### Securing the BIOS
You can’t have a secure setup*[1] without a secure core/part of it. The first thing when you make a new system should be securing your BIOS (basic input/output system):

![Example BIOS]({{ site.url }}/public/images/2017/bios-example.jpeg)

First you must set an admin password in your BIOS. As shown above it will stop an attacker*[2] from modifying settings, restrict booting from external devices, which protects against modifying the root password. The next step must be to disable booting from external devices to stop the attack mentioned above.

![Example BIOS]({{ site.url }}/public/images/2017/bios-password.png) Now when your PC turns on you might see something like this.

#### Move to user friendly GNU/Linux OS

Move to Ubuntu or any other user friendly GNU/Linux OS

![Example BIOS]({{ site.url }}/public/images/2017/ubuntu.png)

There are fewer malwares written for GNU/Linux Operating systems compared to Windows and by simply switching your OS to Ubuntu you greatly decrease your chances of getting a virus. Also, malware written for Windows generally don’t work on GNU/Linux. For most the switch shouldn’t cause any problems(in my personal opinion) since Ubuntu offers the same functionality as Windows and even looks similar. My mother, who isn't a techie is using Ubuntu on day-to-day basis :)

Whilst installing a new OS (in my example I will use Ubuntu) choose the option to use the full disk encryption:

Full disk encryption ensures that if we lose our machine, the attacker will not be able to read any data from it. More info <a href="https://en.wikipedia.org/wiki/Disk_encryption">here</a>. Next follow the steps and create a new account. After it’s done you will have access to a user with sudo rights. You should not use this account for everyday use but create an additional account without any sudo rights:
Search for system settings ->
![Ubuntu settings]({{ site.url }}/public/images/2017/ubuntu-settings.png)
Click on user accounts
![Ubuntu settings]({{ site.url }}/public/images/2017/ubuntu-user.png)
You will see the list of users on your machine

2) Then add another non-Administrative user. It can be done by pressing the + in the lower left corner of the image 1. This is done to protect you from accidentally downloading and executing files, since the user has no sudo right it will be much harder for a virus to get installed.[3] You should use this user on an everyday basis. Before you start using this account on everyday basis it would be a good idea to give this account sudo rights, install all needed programs first, and then switch the account back to standard type. A good practice would be not to install programs from <a href="https://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them">PPA</a>, unless you know what you are doing.

#### Enable automatic security updates
From System Settings open Update Manager. Click the ‘Settings…’ button, then on the ‘Updates’ tab, select the radio button ‘Install security updates without confirmation.’
More at :[https://askubuntu.com/questions/9/how-do-i-enable-automatic-updates](https://askubuntu.com/questions/9/how-do-i-enable-automatic-updates)
![Ubuntu updates]({{ site.url }}/public/images/2017/ubuntu-updates.png)

#### Firewall
In this guide we will be using <a href="https://en.wikipedia.org/wiki/Uncomplicated_Firewall">UFW</a> (Uncomplicated Firewall). It’s a simple to use firewall, which doesn’t require vast knowledge in iptables. The goal of the firewall is to monitor traffic and block unwanted (also malicious) traffic. UFW should be installed by default in the Ubuntu OS and is disabled by default. If it is not installed you can install it by typing this command into the terminal:
sudo apt-get install ufw
One of the things that will make setting up any firewall easier is to define some default rules for allowing and denying connections. UFW’s defaults are to deny all incoming connections and allow all outgoing connections. This means anyone trying to reach your machine would not be able to connect, while any application within the machine would be able to reach the outside world. To set the defaults used by UFW, you would use the following commands:

{% highlight js %}
sudo ufw default deny incoming
sudo ufw default allow outgoing
{% endhighlight %}

Next we need to enable the firewall and can achieve that by typing:

{% highlight js %}
sudo ufw enable
{% endhighlight %}
You should see the command prompt again if all went well. You can check the status of your rules now by typing:
{% highlight js %}
sudo ufw status
{% endhighlight %}
Now you have a working, uncomplicated firewall, which blocks incoming connections and allows outgoing ones. [4]

#### Browser extansions and settings
Most of the current browsers are pretty secure by default, considering your threat is not coming from state agencies. You can make it even more secure by changing settings in the browser and installing security extensions.
1. Install browser plugins
##### uBlock Origin
[https://github.com/gorhill/uBlock/](https://github.com/gorhill/uBlock/) uBlock Origin blocks ads, trackers and malware sites. There are a number of reasons why you would choose uBlock Origin over Adblock Plus, which some might say is more known, some of which are: <a href="https://www.theverge.com/2016/9/13/12890050/adblock-plus-now-sells-ads">Adblock Plus sells ads</a>, performance and efficiency.
![uBlock origin]({{ site.url }}/public/images/2017/uBlock.png)

###### uMatrix
https://github.com/gorhill/uMatrix [https://github.com/gorhill/uMatrix](https://github.com/gorhill/uMatrix)
uMatrix allows you to configure how your browser interacts with websites, what those can load etc.
![uMatrix 1]({{ site.url }}/public/images/2017/umatrix_1.png)
Set the setting as follows by clicking on the top part of the block to make a block green and by clicking at the bottom part to make it red. The “\*” in the left corner means that these rules will apply to all websites, unless you have specific rules for particular ones. On the image 1, generally all websites are allowed to load images and css files. When you visit webpages they load Javascript(JS) to enhance its functionality and look. While generally JS loaded is not malicious it could be used to harm your machine. Malicious websites could load bad JS when users visit it, this malicious code infects the users computer with malware or performs unwanted actions on behalf of user \*[5] So it’s better not to allow websites to load JS, and whitelist <a href="https://en.wikipedia.org/wiki/Whitelist">whitelist</a> the websites you trust so that they can load JS.

![uMatrix 2]({{ site.url }}/public/images/2017/umatrix_2.png)
Explanation of image 2 : Since I trust Medium I allow it to read cookies, allow it to load and run scripts, XHR. Another explanation on how to configure uMatrix: <a href="https://github.com/gorhill/uMatrix/wiki/Very-bare-walkthrough-for-first-time-users">https://github.com/gorhill/uMatrix/wiki/Very-bare-walkthrough-for-first-time-users</a>
2. In your browser set the setting to the following (example shown uses Google Chrome browser):
![Chrome setting 1]({{ site.url }}/public/images/2017/chrome_settings.png)
By blocking sites from setting cookies you improve your privacy
![Chrome setting 2]({{ site.url }}/public/images/2017/chrome_flash.png)
Block Flash and pop-ups (those can still come up without a plugin)
![Chrome setting 3]({{ site.url }}/public/images/2017/chrome_camera.png)
What is happening above: We blocked websites from setting any data, which increases our privacy since websites will not be able to track us, block Flash from being run, which stops many Flash security holes. Even though we block cookies from being set we will need to manage exceptions, ie allow certain websites you trust to set cookies. You can do that by pressing “Manage exceptions” button.
![Chrome setting 4]({{ site.url }}/public/images/2017/chrome_cookies.png)
This what you will see when you click manage exceptions for cookies.
I allowed websites you can see on Image 3 to set cookies and also made exception on uMatrix.

###### Cover your camera

Cover your camera with something e.g. tape. Certain viruses can get access to your machines camera and see what you are doing.

![Camera]({{ site.url }}/public/images/2017/camera_fb.png)

Picture taken from the Guardian article: <a href="https://www.theguardian.com/technology/2016/jun/22/mark-zuckerberg-tape-webcam-microphone-facebook">https://www.theguardian.com/technology/2016/jun/22/mark-zuckerberg-tape-webcam-microphone-facebook</a>
Even though it’s not likely that you will get a virus on your machine, which will be able to access the camera, its better be safe than sorry.

###### Install a VPN

Install a VPN <a href="https://en.wikipedia.org/wiki/Virtual_private_network">(Virtual private network)</a> In short it secures your traffic from your Internet Service Provider(ISP) by not letting them know what websites you visit and what you do on the Web, bad person on the same network as you in a cafe, on any open access wifi hotspot etc. I will not go into the details how to install one but rather suggest to choose VPN which doesn’t log, though its difficult to check if they do and don’t. One of the main ways to check if your provider logs is to have a look if your VPN provider has received any court orders to release data and what have they provided. If your VPN provider didn’t give any data it’s very likely that their no log policy is real. I personally would support <a href="https://www.privateinternetaccess.com/">Private Internet Access(PIA)</a>. Only get a paid VPN as most free VPN services are probably selling your data, so they’re not worth using.
![VPN]({{ site.url }}/public/images/2017/vpn.png)

How VPN works. Credits: <a href="http://blog.flashkirby.com/">http://blog.flashkirby.com/</a>
Below you can find reviews of VPN providers. Note that, I am not paid nor connected to any of those providers nor tested them all.
<a href="https://torrentfreak.com/best-vpn-anonymous-no-logging/">https://torrentfreak.com/best-vpn-anonymous-no-logging/</a>

###### Use a password manager

A password manager is a software application or hardware that helps a user store and organize passwords. Instead of using a simple password like qwerty123 you have a complex unique password for different services. I suggest to use <a href="https://www.keepassx.org/">KeePassX </a> for a number of reasons some of which are: your password database is stored locally, meaning that there is no threat from online service leaking your passwords, saves many different information, whole database is encrypted with the AES (aka Rijndael) encryption algorithm using a 256 bit key.
![Camera]({{ site.url }}/public/images/2017/keepassx.png)
