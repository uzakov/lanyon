---
layout: post
title: Cost-effective means of combating domain phishing.
---

If you ever needed a solution to find and monitor phishing domains related to your company, but didn’t have a budget (or didn’t want to spend too much money) for a full scale solution – you are in the right place.
The goal of this post is to talk about combating phishing domains, what actionable and measurable steps you can take, advantages and disadvantages of this setup.

### Core functionality:

1. Certificate Monitoring - real-time monitoring of certificates issued for specific domain strings and permutations
2. Suspicious domain monitoring for changes
3. Checking new domains bought and sold

### Certificate monitoring
Whenever a new certificate gets requested and issued, the Certificate Authority (CA) records information about it to the public log. More information about certificate transparency can be found here: [https://certificate.transparency.dev/howctworks/](https://certificate.transparency.dev/howctworks/)

What this setup does is monitors for certificates issued for your domain but also for lookalike domains or certain keywords in domains. For example, if the domain is example.com we will monitor for certificates issued to example-sales.com, examples.com, testexample.com etc

The way you do that is by watching the Certificate Transparency log update stream in real-time, parsing certificate information and checking for information related to the company. Diving deeper, this is performed by directly parsing certificate information from the Certificate Transparency log, while cross-checking for company information, such as company name, brands, intellectual property.
Example certificate logged [https://crt.sh/?id=5112823461](https://crt.sh/?id=5112823461)

![Certificate]({{ site.url }}/public/images/2021/certificate.png)
While you can build a solution for this yourself, you can also look at open source solutions, for example, [CertStreamMonitor](https://github.com/AssuranceMaladieSec/CertStreamMonitor)

CertStreamMonitor can monitor certificates generated for specific domain strings and associated, store data into sqlite3 database, alert you when sites come online.
![Certificate Transparency]({{ site.url }}/public/images/2021/CT.gif)
To get started you would need to edit at least
{% highlight js %} SearchKeywords, DetectionThreshold, BlacklistKeywords {% endhighlight %} in the config file.

### Notifications

There are two portable and cheap ways to enable notifications: Slack and Telegram. In this post I will be covering Telegram.

### Telegram

Probably the easiest way to enable notifications, as the only thing required on machines is curl. For more information about Telegram bots: [https://core.telegram.org/bots](https://core.telegram.org/bots)

Registering our bot:

1. On Telegram message @BotFather with /newbot command. The BotFather will ask you for a name and username, then will generate an authorization token for your new bot.
2. After you successfully register the bot you will receive a token you will need later

![Telegram]({{ site.url }}/public/images/2021/telegram.png)

To be able to send messages we need a token and chat_id.

To get “chat_id”, you need to first {% highlight js %} curl https://api.telegram.org/bot<BOT_TOKEN>/getUpdates {% endhighlight %}

After you get *chat_id* you can start messaging :) Please note, *chat_id* can be a negative value

{% highlight js %} curl "https://api.telegram.org/bot<BOT_TOKEN>/sendMessage?chat_id=<CHAT_ID>&text=<YOUR_TEXT>" {% endhighlight %}

### Newly registered domains, squatting, homograph attacks monitoring
Often malicious actors register domains that are similar to your company domain but these domains wouldn't necessarily be caught by Certificate Transparency log monitoring.

To combat this we can use [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) to find similar enough domain names and watch for those as well, by monitoring newly registered domains, performing DNS requests. openSquat project can help with that and much more.

[openSquat](https://github.com/atenreiro/opensquat) is an opensource Intelligence (OSINT) security tool to identify cybersquatting threats to specific companies or domains, such as:

1. Phishing campaigns
2. Domain squatting
3. Typosquatting
4. Bitsquatting
5. IDN homograph attacks
6. Doppelganger domains
7. Other brand/domain related scams
8. Automatic newly registered domain updating (once a day)
9. IDN homograph attack detection
10. Integration with VirusTotal
11. Integration with Quad9 DNS service

### Advantages and disadvantages of this setup

Most commercial offerings are comprised of 80% of what this post covers, with price ranges starting at $7k per year for basic, and upwards of $50k for comprehensive monitoring, that sometimes includes certain number of takedowns per month. The advantage of the setup described above is that it is fast to build, does not cost anything/much, can deliver value from the very beginning and covers most of the use cases manjority of companies face.

The setup explained above does not take into account things like ML, the amount of engineering effort required to build and maintain such a solution, amount of time spent requesting domain takedowns and other ways and tools to discover phishing domains like [sherlock](https://github.com/sherlock-project/sherlock). It's up to the reader to decide whether it's worth building this yourself or buying a solution.


Having read this you might be wondering how this all fits together. Well this is a task for the reader to combine everything mentioned above into one.

> Give a man a fish and you feed him for a day; teach a man to fish and you feed him for a lifetime - Anne Isabella Thackeray Ritchie

> Give a man an 0day and he'll have access for a day, teach a man to phish and he'll have access for life. - grugq

Thank you for reading and have a good day!


Further reading:
* [https://www.ncsc.gov.uk/guidance/phishing](https://www.ncsc.gov.uk/guidance/phishing)
* [https://www.keepnetlabs.com/antiphishing-tools-and-phishing-protection-software-phishing-attacks-with-legitimate-urls/](https://www.keepnetlabs.com/antiphishing-tools-and-phishing-protection-software-phishing-attacks-with-legitimate-urls/)
* [https://www.fbi.gov/scams-and-safety/common-scams-and-crimes/spoofing-and-phishing](https://www.fbi.gov/scams-and-safety/common-scams-and-crimes/spoofing-and-phishing)
