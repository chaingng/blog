+++
title = "SRM 352 DIV1 Easy - NumberofFiboCalls （復習○）"
date = 2014-01-18T09:29:00Z
updated = 2015-03-26T19:54:39Z
tags = ["DP"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=2292&amp;rd=10709" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=2292&amp;rd=10709</a><br /><br />フィボナッチ数の計算が再帰プログラムで書かれている。<br /><br />このとき、ある整数ｎのフィボナッチ数を求めるときに再帰プログラムにて１と０が出力される回数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />ｎの最大が４０のため全探索では解くことができない。<br /><br />ここで、ある数xまでに出力される０と１の回数もフィボナッチ数と同様に、<br />x-1とあるx-2の０と１の回数の和で求められることがわかる。<br /><br />これをｄｐで実装する。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class NumberofFiboCalls {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: vector&lt;int&gt; fiboCallsMade(int n) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; ans;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int dp0[n+1],dp1[n+1];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp0,0,sizeof(dp0));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp1,0,sizeof(dp1));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp0[0]=1,dp1[1]=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,2,n+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dp0[i]=dp0[i-1]+dp0[i-2];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>dp1[i]=dp1[i-1]+dp1[i-2];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans.push_back(dp0[n]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ans.push_back(dp1[n]);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
