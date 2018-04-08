+++
title = "android studioのインストール"
date = 2014-10-06T19:47:00Z
updated = 2014-10-06T19:47:26Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on">android studioのインストールメモ。<br /><br />まずはここから本体をダウンロード。<br /><a href="https://developer.android.com/sdk/installing/studio.html" target="_blank">https://developer.android.com/sdk/installing/studio.html</a><br /><br />後はこちらのページの内容に沿ってインストール。<br /><a href="https://developer.android.com/sdk/installing/index.html?pkg=studio" target="_blank">https://developer.android.com/sdk/installing/index.html?pkg=studio</a><br /><br />まずはandroid studioの起動にあたってはJDKとJAVA_HOMEのPATH設定が必要なのであらかじめ済ませておく。<br /><br />インストール後、必要なsdkをインストールする。<br />Configure＞sdk managerと移動すればインストール可能。<br /><br />このとき、管理者権限でandroid studioを起動していなければsdkのインストール時に<br />「Nothing was installed」とエラーが出てしまう。<br /><br />そのときはandroid studioのアイコンを右クリック＞プロパティから<br />管理者権限で実行するをチェックする。<br />これで次回からは常に管理者権限で実行され、sdkのインストール時にもエラーは出なくなる。<br /><br />必要なsdkパッケージは以下の通り。<br /><br />＜メインパッケージ＞<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">・sdk tools<br />・sdk platform tools<br />・sdk build tools</div><br />＜androidのバージョンごと＞<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">・sdk platform<br />・intel系のsystem image（インテルのエミュレータを用いる場合）</div><br />＜extra＞<br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">・android support repository<br />・android support library<br />・google usb driver<br />・intel x86 emulator（インテルのエミュレータを用いる場合）</div></div>
