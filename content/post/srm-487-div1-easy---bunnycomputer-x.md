+++
title = "SRM 487 DIV1 Easy - BunnyComputer x"
date = 2015-05-05T23:30:00Z
updated = 2015-08-09T20:57:31Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11157&amp;rd=14240" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11157&amp;rd=14240</a><br /><br />Bコンピュータをすべてのうさぎが使いたい。<br />ただしBコンピュータは１台しかないため、１度に１匹のうさぎしか使えない。<br /><br />うさぎがタスクをこなすのに、１秒Bコンピュータを専有し、その後K秒机上で計算を行い、その後１秒コンピュータを専有する。<br /><br />コンピュータを専有する時間によってpreferenceの値が与えられ、この時間を最大化したい。<br />その最大値を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />スタート時間を０〜Kとし、各スタート時間に対しK+1秒ごとに同じ集合に<br />することができる。<br /><br />この集合ごとに得られるpreferenceを最大化し、その和を求める。<br />各集合についてpreferenceを最大化する選び方は貪欲法では難しいので<br />dpを用いればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class BunnyComputer {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int getMaximum(vector&lt;int&gt; preference, int k) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=preference.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;k+1;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vector&lt;int&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=i;j&lt;n;j+=k+1)vx.push_back(preference[j]);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int m=vx.size();<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int dp[m+1];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>memset(dp,0,sizeof(dp));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=2;j&lt;=m;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>dp[j]=max(dp[j],dp[j-1]);<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>dp[j]=max(dp[j],dp[j-2]+vx[j-2]+vx[j-1]);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=dp[m];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>