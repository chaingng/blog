+++
title = "SRM 427 DIV1 Easy - DesignCalendar （復習○）"
date = 2014-02-01T20:08:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10155&amp;rd=13518" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10155&amp;rd=13518</a><br /><br />１日あたりの日数Ｄと１年あたりの日数Ｙが与えられる。<br />１年あたりの日数が１日あたりの日数で割り切れるのに必要な年数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題文がとにかく難しい。<br /><br />要は、必要な年数をＸとすると<br />（Ｙ＊Ｘ）％Ｄ＝＝０となる最小のＸを求めればよい。<br /><br />ここでＹ％Ｄ＝aとすると、求めるxは<br />（例）<br />　a=4,D=6のとき lcd=12 gcd=2となりx=3<br />　a=4,D=14のとき lcd=28 gcd=2となりx=7<br /><div><br /></div><div>つまり、x=D/gcd(a,D)となる。</div><br />例外処理として、aが割り切れる場合は答えは１となるのに注意。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class DesignCalendar {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int gcd(int a,int b){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(a%b==0)return b;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return gcd(b,a%b);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int shortestPeriod(int dayLength, int yearLength) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int a=yearLength%dayLength;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return a==0 ? 1 :dayLength/gcd(dayLength,a);<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
