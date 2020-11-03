---
layout: post
title: Why Edward Snowden is wrong and SMS protocol is broken
---
<div class="message">
  See original post on <a href="https://medium.com/@uzakov/why-edward-snowden-is-wrong-and-sms-protocol-is-broken-c80b5bc450a6">Medium</a>
</div>

It all started a while back when I was watching an amazing talk from Defcon https://www.youtube.com/watch?v=DU8hg4FTm0g And I decided to read more into SMS and telecom technology.

Research into this topic showed a couple of companies who offered internet-to-SMS message delivery. I went with (name not given due to privacy) since they provide a nice API and enough documentation. After doing a proof-of-concept SMS spoof on myself and a couple of other phone numbers on different networks, it worked flawlessly! The owners of the other phone numbers were told what was happening, and they gave their permission prior to testing. Even using so called safe messengers, such as Signal, which was recommended by Snowden, doesn’t save you, since the receiving phone has no way of validating the SMS text message.

To show possible implications let’s imagine a situation: your friend got a new and exciting job in a big company. One afternoon, his boss leaves the office. Later, your friend receives a text message from his/hers boss telling them that they have forgotten some documents and need them urgently. They will send their nephew, whose name is say Alikhan, to pick them up. They inform your friend that their nephew is already on their way. Do you think your friend would give those documents to Alikhan? You would be surprised how many people would do this as long as it came from their boss’s phone number.

To top this process off, (name not given due to privacy) even offers a couple of free SMS if you validate your mobile number. With this feature in mind, a bad person can buy a prepaid SIM from a small shop in a different town without revealing their identity. Next thing they would need is to have an email address, which one can register completely anonymously, by using VPN and a spoofing User agent of browser.

How it works

The SMS standard defines what information is sent in a text message, what bits of binary code make up each letter, and how this data is organised so that sending and receiving devices can communicate with each other. The actual data format for the message includes things like the length of the message, a time stamp, the destination phone number, and the actual message of course.
After the sender and receiver information comes a protocol identifier and a tag to identify the data encoding scheme used in the message, which will allowing different receivers to know how to decode the actual message. There’s also a time stamp and information on the length of the users message before the user’s actual message is encoded.
As for the message itself, as already mentioned it can contain up to 160 characters, where each character is defined by the 7-bits GSM alphabet. A 7-bit alphabet results in 128 (2⁷) available letters, numbers, and pieces of punctuation which can be used to create a SMS message. For example, 48656C6C6F is the GSM alphabet equivalent of the word Hello.
Above is a short explanation of sms message structure. One can edit variable and in the most networks operator wouldn't check whether the sender and sender number are the same. After bad guys change the FROM header then can send this SMS to the victim. Network operators keep logs but perform no server side verification.

TL;DR
Don’t use SMS text messages for communication, call the sender if unsure. SMS protocol is broken.
Update 1:
Some people requested to see proof and images. Here they are:
![Signal]({{ site.url }}/public/images/2016/signal.jpeg)
