+++
title = "SRM 554 DIV1 Easy - TheBrickTowerEasyDivOne （復習○）"
date = 2013-08-18T10:15:00Z
updated = 2015-03-26T20:03:39Z
tags = ["考察"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12159&amp;rd=15176" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12159&amp;rd=15176</a><br /><br />２つの色のレンガと、レンガの個数がそれぞれ与えられる。<br />レンガは違う色を交互にだけ積み重ねることができる。<br />このとき、とりうる高さの場合の数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />いくつか例を出してみると、積み重ねたレンガの数が偶数のときは2通り存在し、<br />それ以外の場合は１通りしか存在しないことがわかる。<br /><br />１）積み重ねたレンガが偶数のときの場合の数　<br />　２色のうち最小の数<br /><br />２）レンガが奇数のときの場合の数<br />　＜レンガの長さが違う時＞<br />　　レンガの数が２色とも同じ<br />　　　その数×２<br />　　レンガの数が２色で異なる<br />　　　少ない方×２＋１<br />　＜レンガの長さが２色とも同じ時＞<br />　　レンガの数が２色とも同じ<br />　　　その数<br />　　レンガの数が２色で異なる<br />　　　少ない方＋１<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class TheBrickTowerEasyDivOne {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int find(int redCount, int redHeight, int blueCount, int blueHeight) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=min(blueCount,redCount)*2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(redHeight!=blueHeight)ret+=min(blueCount,redCount);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(blueCount!=redCount)ret++;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
