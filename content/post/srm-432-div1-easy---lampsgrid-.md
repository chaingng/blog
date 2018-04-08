+++
title = "SRM 432 DIV1 Easy - LampsGrid ○"
date = 2015-05-05T23:35:00Z
updated = 2015-08-08T07:01:41Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10154&amp;rd=13694" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10154&amp;rd=13694</a><br /><br />１と０からなるランプが複数並べられている。<br />各ランプは１行から成り、すべてのランプが一列に並べられている。<br />ランプの値がすべて１となったとき、そのランプは点灯する。<br /><br />プレイヤーはK回、一つの列を選んでそのすべての値を反転させる。<br /><br />このとき、点灯するランプが最大となるときのそのランプ数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />０１の並びがまったく同じランプだけが、最終的に同時に点灯する可能性がある。<br /><br />すべての並びのランプについて、その０の値とKの値によってすべて点灯させられるか<br />確かめればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LampsGrid {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int mostLit(vector&lt;string&gt; initial, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=initial.size(),m=initial[0].size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int cnt=0,num=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,n)if(initial[i]==initial[j])cnt++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,m)if(initial[i][j]=='0')num++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(K&gt;=num &amp;&amp; (K-num)%2==0)ret=max(ret,cnt);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
