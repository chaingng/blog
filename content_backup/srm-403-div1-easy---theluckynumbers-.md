+++
title = "SRM 403 DIV1 Easy - TheLuckyNumbers ○"
date = 2015-04-29T22:04:00Z
updated = 2015-08-08T07:05:55Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8568&amp;rd=12175" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8568&amp;rd=12175</a><br /><br />整数aとbが与えられる。<br />a以上かつb以下の整数のうち、4と7からなる整数の総数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />a,bは10^9でありすべて全探索しては間に合わないが、<br />４と７からなる数字は2^9のため、<br />DFSにて４と７からなるすべての数字について調べればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">int ret,a,b;<br /><br />class TheLuckyNumbers {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>void dfs(long long x){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(x&lt;=b){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dfs(x*10+4);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dfs(x*10+7);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(a&lt;=x)ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int count(int a_, int b_) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>a=a_,b=b_;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dfs(0);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
