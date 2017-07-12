+++
title = "SRM 664 DIV1 Easy - BearPlays x"
date = 2015-08-05T09:25:00Z
updated = 2015-08-05T09:25:25Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13916&amp;rd=16513" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13916&amp;rd=16513</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />数学的に解くことができるのに気がつけるか。<br />A+B=Sとすると、<br />A&lt;Bのとき、A=2*A=2A%S<br />A&gt;Bのとき、A=A-B=A+(A-(A+B))=A+(A-S)=2A-S=2A%S<br />よって常にA*2%Sとなる。<br /><br />K回かけるので、かけた後はA*2^k%Sとなり、この値とSからこの値を引いたもののうち<br />最小のものが答えになる。<br /><br />Kは大きいので繰り返し２乗法を用いる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class BearPlays {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>long long modpow(long long a,long long k,long long m){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(k==0)return 1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(k%2==0)return modpow((a*a)%m,k/2,m);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return (a*modpow(a,k-1,m))%m;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int pileSize(int A, int B, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long a=(A*modpow(2,K,A+B))%(A+B);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return min(a,A+B-a);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
