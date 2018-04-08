+++
title = "短縮URLの仕組み"
date = 2014-10-10T22:21:00Z
updated = 2014-10-10T22:21:36Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />整理用にメモ。<br /><br />短縮URLでアクセスできる仕組みは、要はリダイレクトを利用しているだけ。<br /><br />サンプルとして、こちらのページで短縮URLを作成してみる。<br /><a href="https://goo.gl/" target="_blank">https://goo.gl/</a><br /><br />まずhttp://www.yahoo.co.jp/を入力すると、<br /><a href="http://goo.gl/0wXWlP" target="_blank">http://goo.gl/0wXWlP</a>という短縮URLが作成される。<br /><br />この短縮URLにアクセスすると、<br />つまりhttp://goo.gl/にある0wXWlPという名前のファイルにアクセスすることになる。<br /><br />そして、このファイルにアクセスした場合は<br />http://www.yahoo.co.jp/にリダイレクトするという命令を以下のように.htaccessファイルに書いてあげればリダイレクトにより短縮URLによるアクセスが実現できる。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">Redirect /0wXWP http://www.yahoo.co.jp/&nbsp;</div></div>
