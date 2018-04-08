+++
title = "adbをWi-Fi経由で利用"
date = 2014-10-01T19:20:00Z
updated = 2014-10-04T21:37:58Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />端末が増えてくるとそれぞれusb接続してadbコマンドを打つと大変になった。<br />そこで、usbに接続しなくとも無線LAN経由にてadbを利用する方法があったので整理しておく。<br /><br />１．下準備として、端末にusb接続してtcpポートを解放。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">$adb tcpip 5555</div><br /><br />２．usbを外して、adb connectにて端末のIPアドレス(ここでは仮に10.10.10.10)にアクセス。<br />このとき、操作元の端末と操作したい端末は同じWi-Fiネットワーク下にあること。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">$adb kill-server<br />$adb connect 10.10.10.10:5555</div><br />これだけで無線LAN経由でadbコマンドを打つことが可能になる。<br /><br />ちなみに、公式ページを下の方にも解説がある。<br /><a href="http://developer.android.com/tools/help/adb.html" target="_blank">http://developer.android.com/tools/help/adb.html</a></div>
