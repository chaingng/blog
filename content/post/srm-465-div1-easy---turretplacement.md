+++
title = "SRM 465 DIV1 Easy - TurretPlacement"
date = 2015-05-03T21:51:00Z
updated = 2015-05-03T21:51:10Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10840&amp;rd=14182" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10840&amp;rd=14182</a><br /><br />２次元座標上の複数の点が与えられる。<br />ここから２つの点を選び、それぞれ各点が中心となるように正方形をそれぞれ<br />１つずつ設置したい。<br /><br />正方形の１辺は整数になるようにしたい。<br />また、正方形は互いに重ならないようにしたい。<br /><br />このとき、正方形の設置の仕方の総数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />ある２点の選び方すべてについて、置けるすべての正方形の長さを<br />試してあげればよい。<br /><br />選んだ２点の距離＊２が、２つの正方形の１辺の和以下であればよい。<br /><br />ある点の距離＊２我与えられたときの置き方の総数は、<br />例えば長さがn=５であったとき１＋２＋３＋４となるので（n-1)*n/2となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TurretPlacement {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long count(vector&lt;int&gt; x, vector&lt;int&gt; y) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=x.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,i+1,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double d=sqrt((x[j]-x[i])*(x[j]-x[i])+(y[j]-y[i])*(y[j]-y[i]));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>long long num=d*2;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=(num-1)*num/2.0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
