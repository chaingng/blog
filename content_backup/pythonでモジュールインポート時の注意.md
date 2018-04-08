+++
title = "Pythonでモジュールインポート時の注意"
date = 2014-01-26T16:22:00Z
updated = 2014-01-26T19:12:03Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />クローラーを作るのにPythonが使いやすかったので利用したのですが、<br />そのときにimportでひっかかってしまったのでメモ。<br /><br /><h3 style="border-bottom-color: rgb(106, 90, 205); border-bottom-style: solid; border-bottom-width: 2px; border-left-color: navy; border-left-style: solid; border-left-width: 8px; padding: 0px 0px 1px 5px;">importの書き方</h3><div><br /></div>importには２通りの書き方があります。<br /><br />１つ目は、importにパッケージ名.モジュール名と書く方法。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">import urllib.request</div><br />こちらの場合はモジュールを使うのにフルパスを書かなければいけないです。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted rgb(204, 204, 204); padding: 5px;">html = urllib.request.urlopen(x)</div><br /><br />２つ目は、from　パッケージ名　import モジュール名と書く方法。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted rgb(204, 204, 204); padding: 5px;">from bs4 import BeautifulSoup</div><br />こちらはモジュール名だけ書くだけで使用できるので、こちらの方がすっきりします。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted rgb(204, 204, 204); padding: 5px;">datas2 = BeautifulSoup(datas).findAll("td", attrs={"class": "tdSearchResultListKanji"})</div><br /><br /><h3 style="border-bottom-color: rgb(106, 90, 205); border-bottom-style: solid; border-bottom-width: 2px; border-left-color: navy; border-left-style: solid; border-left-width: 8px; padding: 0px 0px 1px 5px;">import時の注意点</h3><div><br /></div>モジュールを利用するには、その上階層にある全てのパッケージ、サブパッケージ名を指定しなければいけないということ。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted rgb(204, 204, 204); padding: 5px;">＃エラー<br />import urllib<br /><br />＃正しい<br />import urllib.request</div><br /><br />Ｃに慣れていたので、この書き方にひっかかってしまいました。<br /><br />どうやら、サブパッケージを設けることでお互いがお互いの使用モジュールについて気にしなくてもよいからこの書き方をしているとのことです。<br /><a href="http://docs.python.jp/2.5/tut/node8.html" target="_blank">http://docs.python.jp/2.5/tut/node8.html</a><br /><br /><br /></div>
