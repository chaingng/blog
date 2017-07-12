+++
title = "SRM 284 DIV1 Easy - TriCount (復習×○)"
date = 2014-02-08T19:47:00Z
updated = 2015-03-26T19:27:41Z
tags = ["全探索"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=4811&amp;rd=8081" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=4811&amp;rd=8081</a><br /><br />１辺の最小の長さと、最大の長さが与えられる。<br />このとき、とりうる三角形の数を求める。<br />ただし、回転して同じ三角形になる場合は同じものとみなす。<br />答えが10^9を超える場合は-1を返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />２重ループでは計算量として間に合わない、はずなのですが<br />10^9以上は-1を返すので２重ループで収まります。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TriCount {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int count(int minLength, int maxLength) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=0LL;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,minLength,maxLength+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,i,maxLength+1){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>ret+=min(maxLength,i+j-1)-j+1;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(ret&gt;1000000000)return -1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
