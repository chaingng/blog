+++
title = "SRM 226 DIV1 Easy - ManhattanMovement (復習×○)"
date = 2014-01-25T11:27:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=3498&amp;rd=6515" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=3498&amp;rd=6515</a><br /><br />・直線ax+by=1、スタート位置（x0,y0）が与えられる。<br />・スタート位置から直線上の点まで移動する。<br />・ただし、ｘ軸に平行、もしくはｙ軸に平行のどちらか１回しか移動できない。<br /><br />このとき、スタート位置から直線上の点まで移動するための最小の距離を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題文のｘ軸に平行もしくはｙ軸に平行の部分について、どちらも利用できると判断してしまった。<br /><br />計算式を変換して、ｘ軸に対する平行移動とｙ軸に対する平行移動のうちどちらか最小を返してあげればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ManhattanMovement {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double getDistance(int a, int b, int x0, int y0) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ans=1e+18;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(a!=0)ans=min(ans,fabs( (1.0-(double)b*(double)y0)/(double)a -(double)x0 ));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(b!=0)ans=min(ans,fabs( (1.0-(double)a*(double)x0)/(double)b -(double)y0 ));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return &nbsp;ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
