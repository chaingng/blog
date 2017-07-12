+++
title = "wgetをプロキシ経由で利用"
date = 2014-10-16T20:10:00Z
updated = 2014-10-16T20:12:22Z
tags = ["technology"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><br />/etc/wgetrcに、以下の設定を追加してあげればよい。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">use_proxy = on<br />proxy_user = user<br /><div><div>proxy_password = password</div><div>https_proxy = http://proxy.yoyodyne.com:18023/</div><div>http_proxy = http://proxy.yoyodyne.com:18023/</div><div>ftp_proxy = http://proxy.yoyodyne.com:18023/</div></div></div><br /><br />ちなみに、ユーザ名とパスワードの設定はwgetrc中に書いていないが、<br />"info wget"で以下のように書いてある。<br /><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">&nbsp; &nbsp;You may specify your username and password either through the proxy<br />URL or through the command-line options. &nbsp;Assuming that the company's<br />proxy is located at 'proxy.company.com' at port 8001, a proxy URL<br />location containing authorization data might look like this:<br /><br />&nbsp; &nbsp; &nbsp;http://hniksic:mypassword@proxy.company.com:8001/<br /><br />&nbsp; &nbsp;Alternatively, you may use the 'proxy-user' and 'proxy-password'<br />options, and the equivalent '.wgetrc' settings 'proxy_user' and<br /><div style="-webkit-text-stroke-width: 0px; color: black; font-family: 'MS PGothic'; font-size: medium; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: normal; margin: 0px; orphans: auto; text-align: left; text-indent: 0px; text-transform: none; white-space: normal; widows: auto; word-spacing: 0px;">'proxy_password' to set the proxy username and password.</div></div></div>
