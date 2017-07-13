+++
title = "2014 TCO Round 3A Easy - BrightLamps (×)"
date = 2014-10-20T20:44:00Z
updated = 2015-03-26T19:30:08Z
tags = ["状態遷移"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13343&amp;rd=16050" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13343&amp;rd=16050</a><br /><br />・複数のランプがあり、現在ついているかどうかの情報が与えられる。<br />・各ランプについて、ついているときの明るさの値が与えられる。<br />・連続K個のランプの状態を変化させることができ、何回でも変化させてよいとき、得られる最大の明るさの値を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・ランプの数は２５００個のため、全探索は厳しい。<br />・ｄｐができないか考えてみるが、前の状態を持つことも難しいためできなさそう<br /><br />他のコードを見てみる。<br /><br />・状態を良く見てみると、あるランプからK個離れたランプは他のランプの状態を変化させずに<br />　それぞれ反転することが可能。<br />・例えば、ABCDEというランプがありK＝４、A＝０、E＝０とする。<br />　このとき、ABCDを反転し、BCDEを反転させることで他をかえずにA=1、E=1とすることができる。<br /><br />・よって、K個ずつ離れた集合をそれぞれ考え、一番最適な反転を考える。<br />　つまり、０の数が偶数個のときはすべて１にすることができ、奇数個の時は一番小さいものだけを<br />　０にして残りを１にすることができる。<br /><br />・ただし、状態によっては集合を奇数回反転した場合がよいことがある。<br />　よって、すべて偶数回反転させる場合と、奇数回反転させるときのうち大きい値が答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class BrightLamps {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int maxBrightness(string init, vector&lt;int&gt; a, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=a.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int odd=0,even=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,K){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int sum=0,minx=1e+9,zero=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=i;j&lt;n;j+=K){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>sum+=a[j];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>minx=min(minx,a[j]);<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(init[j]=='0')zero++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>odd+=sum-minx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>even+=sum-minx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(zero%2==1)odd+=minx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else even+=minx;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return max(odd,even);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>