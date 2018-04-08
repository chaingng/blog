+++
title = "Windowsのプロキシ"
date = 2014-10-31T22:24:00Z
updated = 2014-10-31T22:24:58Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><div dir="ltr" style="text-align: left;" trbidi="on">Windowsのプロキシには２種類存在する。<br /><br />１つめはInternetExplorerのプロキシサーバー設定、もう一つは主にWindows Updateに使用されるWinhttpのプロキシ設定。<br /><br />InternetExplorerはIEのインターネットオプションから設定できるが、<br />Winhttpはnetshコマンドにて設定する。<br /><br />設定方法としては、直接設定するものとIEの設定をコピーする方法の２つ。<br /><br />直接設定する方法<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">netsh winhttp set proxy proxy-server="myProxyServer:8080" bypass-list="&lt;local&gt;;*.microsoft.com;*.foo.ne"</div></div><br />IEの設定をコピーする方法<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">netsh winhttp import proxy source=ie</div><br />現在の設定は、以下のコマンドで確認できる。<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">netsh winhttp show proxy</div><br />また、以下のコマンドで設定をリセット（プロキシなしに）できる。<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">netsh winhttp reset proxy</div><br />WindowsUpdateは手動での更新時はIEの設定が利用されるが、<br />自動更新時はWinhttpのプロキシ設定が適用されるため、プロキシ環境下で自動更新を行いたいときは必要な設定となる。<br /><br />（参考）公式ページ<br /><a href="http://support.microsoft.com/kb/2894304/ja" target="_blank">http://support.microsoft.com/kb/2894304/ja</a><br /><br /></div>
