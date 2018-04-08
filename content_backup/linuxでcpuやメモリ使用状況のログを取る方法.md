+++
title = "LinuxでCPUやメモリ使用状況のログを取る方法"
date = 2014-03-12T19:55:00Z
updated = 2014-03-12T19:57:58Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />Linux(使っているのはRedhat Enterprise Linux 6.3)でCPU負荷とメモリ使用状況のログを取る必要があったので使い方をメモ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">①CPU使用率とメモリ使用状況の表示</h3><br />vmstatを使うことでCPU・メモリ使用率のログが取ることができる。<br />5秒間隔で３回ログを取りたいときは、以下のように引数を指定する。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">$vmstat 5 3</div><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">②時刻情報の表示</h3><br />使用率の分析にはいつ出力されたかが知りたいと思うので、時刻と紐づけたいことが多いと思う。これはpipとawkを使うことで実現する。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">vmstat 1 | awk '{ print strftime("%Y/%m/%d %H:%M:%S"), $0 }'</div><br />awkで時刻情報を出力させた後、現在の行(vmstat)を出力させている。<br />これで１秒間隔で、年／月／日　hh:mm:sssの時刻情報と紐づけて出力することができる。<br /><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">③ログへの出力</h3><br />実は上記のコマンドの標準出力をログに出そうとしても出力されない。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">vmstat 1 | awk '{ print strftime("%Y/%m/%d %H:%M:%S"), $0 }'　&gt;&gt; sample.log</div><br />これは、pipの後ろの処理が終了してからバッファに保存してある情報をファイルに書き込みむため。<br />そのため、system()関数を用いてバッファをリフレッシュする。<br /><br /><br /><div style="background-color: #e3f2fb; border: 1px dotted rgb(204, 204, 204); padding: 5px;">vmstat 1 | awk '{ print strftime("%Y/%m/%d %H:%M:%S"), $0 } {system("")}'　&gt;&gt; sample.log</div><br />こちらに詳細な解説が。<br /><a href="http://www.kt.rim.or.jp/~kbk/gawk-30/gawk_13.html" target="_blank">http://www.kt.rim.or.jp/~kbk/gawk-30/gawk_13.html</a><br /><br />これでやっと、途中でコマンドを終了させてもログに書き込まれているようになる。<br /><br /><br /></div>
