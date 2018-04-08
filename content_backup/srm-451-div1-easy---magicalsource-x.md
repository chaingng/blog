+++
title = "SRM 451 DIV1 Easy - MagicalSource x"
date = 2015-05-04T21:59:00Z
updated = 2015-07-28T04:51:53Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10635&amp;rd=13905" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10635&amp;rd=13905</a><br /><br />ある整数が与えられ、下のように同じ数が段になって足されているとき、<br />そのような元の数の最小値を求める。<br />　１２<br />１２<br />ーーー<br />１３２<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />最後の一桁を固定して、すべての元の数の桁数で全探索して・・・と<br />考えたくなるが、段になって足されているということは<br />元の数に１１、１１１、１１１１・・・のいずれかの数が<br />かけられたものになる。<br /><br />よって、１、１１、１１１・・・と割っていき<br />割りきれるもののうち最小の商が答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class MagicalSource {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long calculate(long long x) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=x;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long p=1LL;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(p&lt;x){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>p=p*10+1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(x%p==0)ret=min(ret,x/p);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
