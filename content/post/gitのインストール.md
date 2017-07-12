+++
title = "gitのインストール"
date = 2014-10-03T21:20:00Z
updated = 2014-10-04T21:37:38Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />gitのインストールメモ。<br />GIT EXTENTIONがCUIもGUIも同時にインストールできるのでスグレモノ。<br /><br />以下のURLのDownloadからmsiをダウンロード。<br /><a href="https://code.google.com/p/gitextensions/" target="_blank">https://code.google.com/p/gitextensions/</a><br /><br />・同梱ツールはMsysGITとKdiff3の両方ともインストール。<br /><br />・Kdiff3は「GIT bash here」「GIT gui here」の両方を選択。<br />　これでCUIライクな操作もGUI操作も可能になる。<br /><br />・PATH環境変数は「Run Git from the Windows Command Prompt」を選択。<br />　これでコマンドプロンプトからも操作可能になる。<br /><br />・改行コードは「Checkout Windows-style, commit Unix-style endings」を選択。<br />　これで通常はwindowsの改行コードに沿って、コミット時のみunixスタイルに変換してくれる。<br /><br />・インストール後、デスクトップを右クリックしてGit Extentions&gt;Settingsを選択。<br />　グローバル設定を選択し、ユーザ名とメールアドレスを登録。<br /><br />・lsの文字化けを防ぐにはデスクトップを右クリックして「GIT bash here」を選択し、<br />　ホームディレクトリから「.bashrc」という名前のファイルを作成、以下のエイリアスを追加する。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">alias ls='ls --show-control-chars'<br />alias dir='ls --show-control-chars'</div><br />・合わせてホームディレクトリから以下のコマンドを設定すれば完了。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">git config --global core.quotepath off</div></div>
