+++
title = "SRM 509 DIV1 Easy - LuckyRemainder"
date = 2015-05-10T20:58:00Z
updated = 2015-05-10T20:58:58Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11138&amp;rd=14438" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11138&amp;rd=14438</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />各桁の数は与えられた整数の桁数をNとすると、それぞれ2^(N-1)回<br />足されることになる。<br /><br />この数を９で割った余りが答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LuckyRemainder {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int getLuckyRemainder(string X) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,X.size())ret=(ret+X[i]-'0')%9;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ret*=pow(2,X.size()-1);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret%9;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
