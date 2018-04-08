+++
title = "SRM 401 DIV1 Easy - FIELDDiagrams"
date = 2015-04-28T21:04:00Z
updated = 2015-04-28T21:04:54Z
tags = ["DP"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8776&amp;rd=12173" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8776&amp;rd=12173</a><br /><br />整数fieldDiagramが与えられて、fieldDiagram行からなるBOXを作る。<br />各行0,1,2,...において、長さはそれぞれfieldDiagram,fieldDiagram-1,fieldDiagram-2以下で<br />なければならない。<br />また、各行において上の行以下の長さでなければならない。<br /><br />このような条件を満たすようなBOXの作り方の総数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />上の行における長さがわかっていれば、上から順にたどっていくことで総数が<br />計算できるのでｄｐで解ける。<br /><br />すべて０の場合は空になるので、最後にそのケース１通りを引いてあげれば良い。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class FIELDDiagrams {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long countDiagrams(int f) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long dp[f+1][f+1];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp,0,sizeof(dp));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0][f]=1LL;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,f)FORE(j,0,f+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int k=min(j,f-i);k&gt;=0;k--)dp[i+1][k]+=dp[i][j];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,f+1)ret+=dp[f][i];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret-1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
