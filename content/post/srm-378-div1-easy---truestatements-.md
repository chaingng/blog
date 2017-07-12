+++
title = "SRM 378 DIV1 Easy - TrueStatements ○"
date = 2015-08-04T06:20:00Z
updated = 2015-08-04T06:20:07Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8390&amp;rd=10798" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8390&amp;rd=10798</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />正しいことを言っている人数を０〜５０までのすべてについて調べ、<br />矛盾しないもののうち最大の人数が答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TrueStatements {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int numberTrue(vector&lt;int&gt; statements) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=statements.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=-1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;=50;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int cnt=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,n)if(i==statements[j])cnt++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(i==cnt)ret=i;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
