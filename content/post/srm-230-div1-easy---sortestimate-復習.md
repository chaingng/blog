+++
title = "SRM 230 DIV1 Easy - SortEstimate （復習○）"
date = 2014-02-09T08:53:00Z
updated = 2015-04-03T11:05:58Z
tags = ["二分探索"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=3561&amp;rd=6519" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=3561&amp;rd=6519</a><br /><br />ソートアルゴリズムの計算量を計算したい。<br />計算量はc*n*log2(n)で表わされ、これをtime以下でかつ最大となるときのｎを求めたい。<br />cとtimeはあらかじめ与えられる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />nが一意に決まれば計算量は算出できるので、二分探索が適用できる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class SortEstimate {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double howMany(int c, int time) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double low=0.0,high=1e+18;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,100){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>double mid=(low+high)/2.0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(c*mid*log(mid)/log(2)&lt;=time)low=mid;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else high=mid;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return low;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
