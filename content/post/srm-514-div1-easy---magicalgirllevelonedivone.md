+++
title = "SRM 514 DIV1 Easy - MagicalGirlLevelOneDivOne"
date = 2015-05-29T22:28:00Z
updated = 2015-05-29T22:28:16Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11476&amp;rd=14539" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11476&amp;rd=14539</a><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />(1,n)と(1,-n)の動作により現在のマスから２つ上下に移動したマスには<br />必ず到達することができる。<br /><br />ここで、jumpTypesが偶数のとき、（ｘ，ｙ）が<br />（偶数、偶数）→上記より可能　（奇数、奇数）→(1,n) (n,1)により可能<br />（偶数、奇数）→(n,1)により可能<br /><br />よってすべての（ｘ，ｙ）に到達可能。<br /><br />jumpTypesが奇数のときは、<br />（偶数、偶数）→上記より可能　（奇数、奇数）→(1,n) により可能<br />（偶数、奇数）→不可能<br /><br />よって（ｘ，ｙ）が（偶数、奇数）のときだけ不可能となる。<br /><div><br /></div><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class MagicalGirlLevelOneDivOne {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string isReachable(vector&lt;int&gt; jumpTypes, int x, int y) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=jumpTypes.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(jumpTypes[i]%2==0)return "YES";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if((x+y)%2==0)return "YES";<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "NO";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
