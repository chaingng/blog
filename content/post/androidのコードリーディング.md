+++
title = "androidのコードリーディング"
date = 2014-10-14T21:31:00Z
updated = 2014-10-16T20:11:24Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />業務でandroidのソースコードを読まなければならなかったときに学んだ、<br />効率的なソースコードの読み方のメモ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">動的な解析と静的な解析</h3><br />ソースコードの解析には、動的な解析と静的な解析がある。<br /><br />動的な解析とはデバッガなどでプログラムを実行させながら流れを解析する方法で、<br />静的な解析とは実際のソースコードを読んでいく方法。<br /><br />最初は動的な解析からはじめると効率的に読むことができる。<br /><br />androidではlogcatと呼ばれるログ出力関数が用意されていて、<br />プログラムを実行するとソースコードに埋め込まれたログが出力される。<br /><br />また、開発環境ではなく実際の端末で実行されたログであれば、<br />以下のadbコマンドでlogcatを取得することができる。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">$adb logcat -v time &gt; logcat.txt</div><br />ただこのlogcatには読みたいプログラム以外にも端末で動いているものの全ての<br />ログが出力されるので、grepなどで必要な箇所だけ切り出してあげると見やすくなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">まとめると</h3><br />まずはプログラムを動かしてみて、出力されるlogcatからそのログが出力されている<br />コードの箇所を探していって、流れを組み立てるとよい。<br /><br />その後、組み立てられたクラスの流れができるので、そこから静的解析として<br />クラスごとにソースを読んでいけば大まかに内容をつかむことができる。</div>
