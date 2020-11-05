---
layout: post
title: Week of Cyber Meetups
---
<div class="message">
  See original post on <a href="https://medium.com/@uzakov/week-of-cyber-meetups-c3d2421a7804">Medium</a>
</div>
Last week was full of interesting cyber security meetups in London.
I attended two, one hosted at Capital One office and another one hosted by OWASP at Revolut office.

### Cyber London, hosted by Capital One
[https://www.meetup.com/London-Cyber-Capital-One/events/262063647/](https://www.meetup.com/London-Cyber-Capital-One/events/262063647/)
![White Collar Factory]({{ site.url }}/public/images/2019/20190717_221119.jpg)
On the 17th of July Georg(my colleague) and I attended a cybersecurity event after work, hosted and organized by Capital One.

There were two talks:

1. Hostage Negotiation, Cyber Extortion, Critical Incident Handling and You!
2. Browser Security Basics


#### Hostage Negotiation, Cyber Extortion, Critical Incident Handling and You!
![Talk 1]({{ site.url }}/public/images/2019/20190717_192344.jpg)
“To Pay or Not To Pay used to be the question, now, Are You Ready to Negotiate?” That was one of the themes of the talk. Two presenters had extensive experience in hostage negotiation and fighting organized crime. One is formerly the Team Leader of Canada’s Royal Canadian Mounted Police’s (RCMP) International Negotiation Team, graduate of both the FBI’s and Scotland Yard’s Hostage Negotiation Programs. Another formerly a United Nations senior security official. They shared their experience and knowledge of organized crime. Even though they do not deal with cybercrime directly, a lot of their methods are also applicable to IT. Do not pay the ransomware creators.

![Crowd]({{ site.url }}/public/images/2019/20190717_195303.jpg)

#### Browser Security Basics

![Talk 2]({{ site.url }}/public/images/2019/20190717_201440.jpg)
The most interesting talk from the engineering perspective, where we had a chance to hear from Mark Goodwin, Mozilla engineer who is working on the Firefox web browser.

Mark covered the basics of browser security, what it does and why it’s important. He also covered the use of Rust at Mozilla, why it’s a great language from a security point of view(memory and thread safety) and plans to increase the amount of Rust code in Firefox. [https://wiki.mozilla.org/Oxidation](https://wiki.mozilla.org/Oxidation)
![Firefox talk]({{ site.url }}/public/images/2019/20190717_203219.jpg)
![Talk 3]({{ site.url }}/public/images/2019/20190717_204631.jpg)

### OWASP London Chapter Meeting at Revolut

[https://www.meetup.com/OWASP-London/events/262880260/](https://www.meetup.com/OWASP-London/events/262880260/)
![OWASP Talks]({{ site.url }}/public/images/2019/20190718_200210.jpg)
![OWASP Talks]({{ site.url }}/public/images/2019/20190718_200723.jpg)
There were three talks:
1. Scaling Security - Move Fast and Make Things
2. Hack In, Cash Out: Hacking and Securing Payment Technologies
3. Advanced Bots and Security Evasion Techniques

#### Scaling Security - Move Fast and Make Things

![Scaling security]({{ site.url }}/public/images/2019/20190718_190238.jpg)

Talk by Revolut CISO, where he talked about the use of Google Cloud Platform at Revolut, a bit about how they do AppSec, automation around security they do at Revolut, microservices, context-aware access [https://cloud.google.com/context-aware-access/](https://cloud.google.com/context-aware-access/), how important it is to move and react fast. He also shared the bank's plans for the near future.

#### Hack In, Cash Out: Hacking and Securing Payment Technologies
![Hack In, Cash Out]({{ site.url }}/public/images/2019/20190718_195834.jpg)

Talk by a researcher from Positive Technologies, who talked about attacks on payment platforms, what cybercriminals do, what his company has found. To sum up, there are a lot of problems with payment platforms. One of the methods criminals used to use was a race condition, where there would be a transaction, from account A to B, transferring a very small amount of money, say £0.000005 and then instantly criminals would send cancel transaction call. Due to the processing error, account B would still have £0.000005

#### Advanced Bots and Security Evasion Techniques

This talk was presented by a Senior Researcher at F5 networks, covering advanced techniques used by bot creators and what F5 does to detect them.
As always there was free pizza and beer. The office was very cool, in a good location and hip inside!
There was a vending machine that gave out Revolut debit cards. You just need to register it through the app.

PS Join OWASP [https://www.owasp.org/index.php/Membership](https://www.owasp.org/index.php/Membership)

![OWASP Talks]({{ site.url }}/public/images/2019/20190718_201215.jpg)
![OWASP Talks]({{ site.url }}/public/images/2019/20190718_210057.jpg)

#### NEVER SETTLE
