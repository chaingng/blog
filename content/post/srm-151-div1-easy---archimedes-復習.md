+++
title = "SRM 151 DIV1 Easy - Archimedes (復習×○)"
date = 2014-02-11T09:25:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=1693&amp;rd=4560" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=1693&amp;rd=4560</a><br /><br />円周率を正多角形から求めたい。<br />円の外周は２＊円周率＊半径の長さで求められる。<br /><br />このとき、正ｎ角形を考えた時に計算できる円周率を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />求めたい円周率をx,半径をr、正n角形の外周をyとすると、<br />2*x*r=y　...①<br /><br />また、正多角形のうち一つの二等辺三角形の底辺dを考えると<br />正ｎ角形の外周はy= n*d<br /><br />ここで、dの長さは<br />sinα=(d/2)/r<br />α=(2*Pi)/(n*2)=Pi/nであるため<br />d=2*r*sin(Pi/n)<br /><br />y=n*2*r*sin(Pi/n)　...②<br /><br />①、②より、<br />2*x*r=n*2*r*sin(Pi/n)<br />x=n*sin(Pi/n)<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class Archimedes {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double approximatePi(int numSides) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return numSides*sin(M_PI/numSides);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
