---
layout: post
title: Cost effective combatting of phishing domains
---

<div class="message">
  Early draft
</div>

If you ever needed a solution to find and monitor phishing domains related to your company but didn’t have a budget (or didn’t want to spend too much money) for a full scale solution – you are in the right place.
The goal of this post is to talk about combating phishing domains, what actionable and measurable steps you can take, advantages and disadvantages of this setup.

### What can the setup do

Core functionality:

1. Certificate Monitoring - real-time monitoring of certificates issued for specific domain strings and permutations
2. Suspicious domain monitoring for changes
3. Checking new domains bought and sold

### Certificate monitoring
Whenever a new certificate gets requested and issued, Certificate Authority (CA) adds information about it to public logs. You can read about it here in more detail:[https://certificate.transparency.dev/howctworks/](https://certificate.transparency.dev/howctworks/)

What we can do is use these logs to watch for certificates issued for our domain but also for lookalike domains or certain keywords in domains. For example, if our domain is example.com we can monitor for certificates issued for example-sales.com, examples.com, testexample.com etc

The way you do that is by watching the certificate transparency log update stream in real-time, parsing certificate information and checking for information related to the company.
Example certificate logged [https://crt.sh/?id=5112823461](https://crt.sh/?id=5112823461)

![Certificate]({{ site.url }}/public/images/2021/certificate.png)
While you can build a solution for this yourself, you can also look at open source solutions, for example, CertStreamMonitor [https://github.com/AssuranceMaladieSec/CertStreamMonitor](https://github.com/AssuranceMaladieSec/CertStreamMonitor)

CertStreamMonitor can monitor certificates generated for specific domain strings and associated, store data into sqlite3 database, alert you when sites come online.

### Notifications

There are two portable and cheap ways to enable notifications: Slack and Telegram. In this post I will be covering Telegram.

#### Telegram

Probably the easiest way to enable notifications, as the only thing required on machines is curl.[https://core.telegram.org/bots](https://core.telegram.org/bots)

Registering our bot:

1. On Telegram message @BotFather with /newbot command. The BotFather will ask you for a name and username, then will generate an authorization token for your new bot.
2. After you successfully register the bot you will receive a token you will need later

![Telegram]({{ site.url }}/public/images/2021/telegram.png)

#### Notifications
To be able to send messages we need a token and chat_id
To get “chat_id”, you need to first send curl https://api.telegram.org/bot<BOT_TOKEN>/getUpdates

After you get chat_id you can start messaging :) Please note, “chat_id” can be a negative value

curl "https://api.telegram.org/bot<BOT_TOKEN>/sendMessage?chat_id=<CHAT_ID>&text=<YOUR_TEXT>"

### Newly registered domains, squatting, homograph attacks monitoring

[openSquat](https://github.com/atenreiro/opensquat) is an opensource Intelligence (OSINT) security tool to identify cybersquatting threats to specific companies or domains, such as:
https://github.com/atenreiro/opensquat

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

What most commercial companies do is 80% of what you see here while pricing goes from 7-8k per year up to 50k per year. It’s worth noting that often that prices include X number of takedowns per month.
The setup explained above does not take into account things like ML, the amount of engineering effort required to build such a solution and also maintain it. Its up to the reader to decide whether its worth building this yourself or buying a solution.

Having read this you might be wondering how this all fits together. Well this is a task for the reader to combine everything mentioned above into one.

Give a man a fish and you feed him for a day; teach a man to fish and you feed him for a lifetime - Anne Isabella Thackeray Ritchie

Give a man an 0day and he'll have access for a day, teach a man to phish and he'll have access for life. - grugq

Thank you for reading and have a good day!


Further reading:
[https://www.ncsc.gov.uk/guidance/phishing](https://www.ncsc.gov.uk/guidance/phishing)
[https://www.keepnetlabs.com/antiphishing-tools-and-phishing-protection-software-phishing-attacks-with-legitimate-urls/](https://www.keepnetlabs.com/antiphishing-tools-and-phishing-protection-software-phishing-attacks-with-legitimate-urls/)
[https://www.fbi.gov/scams-and-safety/common-scams-and-crimes/spoofing-and-phishing](https://www.fbi.gov/scams-and-safety/common-scams-and-crimes/spoofing-and-phishing)