+++
title = "SRM 221 DIV1 Easy - TerribleEncryption (復習○)"
date = 2014-02-09T09:58:00Z
updated = 2015-03-26T19:43:17Z
tags = ["実装"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=1924&amp;rd=5867" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=1924&amp;rd=5867</a><br /><br />暗号化された文字列があり、それを復号したい。<br />あらかじめ暗号化された文字pool、配列data,keysが与えられる。<br /><br />復号後の文字列のi番目の文字は、<br />(data[i]*k)%keys[i]=1となる最小の正の整数kを求め、<br />j=k%(poolのサイズ)としたとき、pool[j]の文字となる。<br /><br />このとき、復号後の文字列を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題文の理解ができれば、同じように実装するだけ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class TerribleEncryption {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string decrypt(string pool, vector&lt;int&gt; data, vector&lt;int&gt; keys) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=data.size(),m=pool.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string str="";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int k=1;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>while((data[i]*k)%keys[i]!=1)k++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>str+=pool[k%m];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return str;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
