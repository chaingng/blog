+++
title = "SRM 621 DIV2 Middle - NumbersChallenge (○○)"
date = 2015-03-19T19:19:00Z
updated = 2015-04-10T10:46:14Z
tags = ["DP"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13166" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13166</a><br /><br />・整数の集合Sが与えられる。<br />・この整数の組み合わせで表わせないような、最小の正の整数を求める。<br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・Sの数が２０、各要素が10^5から<br />計算量O（20*10^5=2*10^6）でメモリ、速度とも足りそうなのでｄｐで解ける。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />int dp[2000001];<br /><br />class NumbersChallenge {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int MinNumber(vector&lt;int&gt; S) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=S.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>memset(dp,0,sizeof(dp));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0]=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)for(int j=2000000-S[i];j&gt;=0;j--)dp[S[i]+j]+=dp[j];<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,2000001)if(dp[i]==0)return i;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return 2000001;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
