---
title: "Wi-Fi multicast that realizes simultaneous broadcast distribution service to a large number"
date: 2018-01-23T10:00:00+09:00
tags: [ "wifi"]
---

This is an English version of [my written technical article](http://www.nttdata.com/jp/ja/insights/trend_keyword/2015111201.html)

## Wi-Fi multicast
By using Wi-Fi multicast technology, multimedia contents such as movies etc. can be delivered simultaneously to all terminals where Wi-Fi can reach.

## Two distribution methods
As delivery modes of Wi-Fi multicast technology, there are two types of real-time viewing services by live streaming and two patterns of accumulating files on the terminal by file cast delivery. By making good use of these two forms, it is possible to realize a shift time viewing service that can be viewed anytime and anywhere.

## Assuring delivery quality

In normal Wi-Fi communication, since the bandwidth is shared by unicast one-to-one communication, tens of terminals that can be connected at the same time are the limit, but by performing multicast 1: N multicast simultaneous connection It can provide services without congestion and limitation of number. Also, in Wi-Fi communication data loss occurs due to attenuation of radio waves. In the case of multicast communication, it is one-way communication, so if data loss occurs, it can not complement data such as "retransmission" and it becomes difficult to provide complete service. For this reason, it is necessary to complement the data on the terminal side when data is lost.

In NTT DATA we developed a system optimized for multicast by combining MPEG-DASH (Dynamic Adaptive Streaming over HTTP) reference 1 and IP reference 2 called IP datacast, which is an international standard for realizing streaming delivery . With this system, it is possible to deliver video with less loss with a low delay of one second in real-time live streaming delivery, and in file cast delivery it is possible to handle shift time service that can handle large capacity files in units of several gigabytes I am doing.

## Specific service image
In a place where many people are densely populated like stadiums and event venues, simultaneous broadcast distribution service of contents becomes possible. It realizes multi-angle viewing of sports competition, overlooked viewing of decision scenes, and emergency information distribution which is hard to congest even in the event of a disaster.

Compared with broadcasting service, it is possible to realize at low cost because it requires only a minimum Wi - Fi access point and delivery server that does not need a broadcasting license and has facilities covering the area as well. In addition, users do not have to worry about packet capacity limitation by using Wi-Fi, and since dedicated receivers are unnecessary, visitors from overseas can also receive services with individual smart phones and applications. It is a technology suitable for international events as well.

NTT DATA provided Wi-Fi multicast distribution service at the 144 British Open (held in July 2015). Players score, course introduction, the three channels of play relay video and live delivery to tablets and wearable devices for, we have provided a new viewing experience to the user that the simultaneous viewing of the real and the video reference 3 . Also, at the National Football League Finals Competition on Friday, November 6, we offered a second screen service for Wi-Fi multicast to viewers 4, 5 . We are planning to provide services to event businesses and local governments in the future.

## Reference
- Reference 1 [DASH Industry Forum](http://dashif.org/)
- Reference 2 [NTT Technical Journal 2014.4 from NTT Data (PDF: 4 pages, 1,694 KB)](http://www.ntt.co.jp/journal/1404/files/jn201404040.pdf)
- Reference 3 [NTTDATA WALL 2015](https://www.youtube.com/watch?v=K1KamWHpToQ&feature=youtu.be)
- Reference 4 [Provide Wi-Fi multicast technology for football's new watching style experiment project](http://www.nttdata.com/jp/ja/news/services_info/2015/2015103001.html)
- Reference 5 [Okada owner Imabari distributes information terminals and tries new watching](https://www.nikkansports.com/soccer/news/1562866.html)
