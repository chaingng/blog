+++
title = "SRM 389 DIV1 Easy - ApproximateDivision ○"
date = 2015-07-25T05:00:00Z
updated = 2015-07-25T05:00:58Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=6125&amp;rd=11123" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=6125&amp;rd=11123</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題分の通りに実装すればよい。<br /><br />ただし、c/tの計算はそれぞれc,tをかけてから割り算を行うとオーバーフローするので<br />c/tを毎回掛けて計算する必要がある。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ApproximateDivision {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double quotient(int a, int b, int terms) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int t=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(t&lt;b)t*=2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int c=t-b;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ret=0,add=1/(double)t;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,terms){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=add;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>add*=c/(double)t;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret*a;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
