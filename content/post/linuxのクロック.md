+++
title = "Linuxのクロック"
date = 2014-01-26T19:37:00Z
updated = 2014-01-26T19:37:36Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">ハードウェアクロックとシステムクロック</h3><br />Linuxには「ハードウェアクロック」と「システムクロックの」２つが存在します。<br /><br />「システムクロック」がＯＳで使われている通常の時計であり、ＰＣを立ち上がっているときのみ有効です。メモリ上で管理するためＰＣをシャットダウンすると消えてしまいます。<br /><br />上記のシステムクロックの仕組みですと、ＰＣを起動するたびに毎回時刻を設定しなければいけません。<br />初期のＰＣは毎回時刻を設定していました。<br /><br />ただ現在では、電源が落ちていても内部バッテリーで動くハードウェアクロックが存在します。<br /><br />ＰＣを立ち上げると、ハードウェアクロックを１度だけ参照してシステムクロックが設定される仕組みになっています。<br /><br /><h3 style="border-bottom-color: rgb(106, 90, 205); border-bottom-style: solid; border-bottom-width: 2px; border-left-color: navy; border-left-style: solid; border-left-width: 8px; padding: 0px 0px 1px 5px;">コマンドでの時刻合わせ</h3><div><br />ハードウェアクロックは内部バッテリーで動いているためバッテリーがなくなれば止まってしまい、また時刻のズレも発生してしまいます。</div>時刻合わせにはＮＴＰの設定など色々と方法はありますが、以前手動で設定する必要があったためその方法をメモしておきます。<br /><div><br /></div>手動での設定時の注意ですが、<br />システムクロックはハードウェアクロックを参照して設定されるため、システムクロックだけ直しても再起動すると無効になってしまいます。<br />そのため、ハードウェアクロックの書き換えが必要になります。<br /><div><br />最初に、システムクロックを変更</div><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"># date --set="2014/1/26 19:32"</div><br />次に、システムクロックをハードウェアクロックに書き込み<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"># clock -w</div><br />これで、ＰＣを再起動しても変更後の時刻が有効になります。<br /><br /><div></div></div>
