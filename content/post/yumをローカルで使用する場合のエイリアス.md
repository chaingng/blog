+++
title = "yumをローカルで使用する場合のエイリアス"
date = 2014-10-02T18:51:00Z
updated = 2014-10-04T21:37:47Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />yumをインターネット経由ではなくローカルで使用したい場合のエイリアス設定。<br /><br />/etc/bashrcもしくは~/.bashrcについて、以下を設定してあげればよい。<br />(rhel-redhatはrepoの名前)<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">alias yum='yum --disablerepo=\* --enablerepo=rhel-redhat'</div><br /></div>
