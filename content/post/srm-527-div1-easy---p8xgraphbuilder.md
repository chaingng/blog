+++
title = "SRM 527 DIV1 Easy - P8XGraphBuilder"
date = 2015-05-27T20:01:00Z
updated = 2015-05-27T20:01:28Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11308&amp;rd=14552" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11308&amp;rd=14552</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />ｄｐで解く。最終的に２＊ｎ−２個のエッジが発生する。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class P8XGraphBuilder {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int solve(vector&lt;int&gt; scores) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=scores.size()+1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int dp[n+1][2*n-1];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n+1)FORE(j,0,2*n-1)dp[i][j]=-(1e+9);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0][0]=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;n;i++)for(int j=i;j&lt;2*n-2;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int k=0;k&lt;n-1&amp;&amp;j+k+1&lt;=2*n-2;k++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>dp[i+1][j+k+1]=max(dp[i+1][j+k+1],dp[i][j]+scores[k]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return dp[n][2*n-2];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
