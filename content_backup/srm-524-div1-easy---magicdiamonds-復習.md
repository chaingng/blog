+++
title = "SRM 524 DIV1 Easy - MagicDiamonds (復習×○)"
date = 2013-10-13T07:42:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11607&amp;rd=14549" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11607&amp;rd=14549</a><br /><br />ｎ個のダイヤモンドを運びたい。<br />１度に最大ｎ個運ぶことができるが、ｎが素数だった場合消滅してしまう。<br />このとき、消滅せずに全てのダイヤを運べる最小の回数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />ｎが最大１０＾１２のためＤＦＳ等では解くことができない。<br />そこで法則がないかシミュレーションしてみる。<br /><br />すると、ｎ＝３（３回）のときを除いて、以下がわかる。<br />①素数でない場合は、１回で運べる<br />②素数の場合は、「素数ー１」個＆「１」個の２回で運べる<br /><br />あとは素数判定関数を作って実装するだけでよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"><br />class MagicDiamonds {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>bool isprimary(long long x){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(x==2)return true;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(x==1||x%2==0)return false;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(long long i=3;i*i&lt;=x;i+=2)if(x%i==0)return false;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return true;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>long long minimalTransfer(long long n) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(n==3)return 3;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return isprimary(n) ? 2 : 1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
