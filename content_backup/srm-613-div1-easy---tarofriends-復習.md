+++
title = "SRM 613 DIV1 Easy - TaroFriends (復習○)"
date = 2014-11-14T19:46:00Z
updated = 2015-03-26T19:05:57Z
tags = ["中間点"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13005&amp;rd=15846" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13005&amp;rd=15846</a><br /><br />・猫が一直線上に数匹存在する。<br />・それぞれの猫が１度移動し、その移動する距離はDであることがわかっている。<br />・ただし、左側もしくは右側のどちらに移動するかはわかっていない。<br />・移動した後に、最も左端と右端の猫の距離が最短になるときの値を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・とりあえずソートして考えるのがよさそう<br />・左端と右端は右と左に動けばよい？<br />・左と右をポイントし、そのうち差の距離が小さくなる方を採用していけばよいか<br />・サンプルは通った<br /><br />→System Failed<br /><br />・貪欲法で解こうとしたが、ソートしたのちに左に動く集合と、右に動く集合にわける場合の数は最大５１通りなので全探索できる。<br />・なんとなく思いついたが、貪欲法の方を実装してしまった。<br /><br />・反省：トレースして思いついた貪欲法を実装してしまったが、今回のようにソートした後に全探索が可能なケースがあるので全探索の線を優先して考える。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class TaroFriends {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int getNumber(vector&lt;int&gt; coordinates, int X) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=coordinates.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(coordinates));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=1e+18;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vector&lt;int&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,0,i)vx.push_back(coordinates[j]+X);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(j,i,n)vx.push_back(coordinates[j]-X);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>sort(all(vx));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret=min(ret,(long long)vx[n-1]-vx[0]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return (int)ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
