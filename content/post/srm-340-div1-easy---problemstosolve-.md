+++
title = "SRM 340 DIV1 Easy - ProblemsToSolve ××○"
date = 2014-01-20T19:09:00Z
updated = 2015-08-14T13:42:11Z
tags = ["考察"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=7504&amp;rd=10664" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=7504&amp;rd=10664</a><br /><br />・各問題について、その楽しさの値が与えられる。<br />・最初は０番目の問題を解く。その後、次の問題かその次の問題を選んでいく。<br />・選んだ問題の楽しさの値の最小と最大の差が、指定された値より大きくなればそこで終了。そうでなければ、全ての問題を解かなければいけない。<br /><br />このとき、解かなければならない問題の最小値を求める。<br /><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題数が最大５０なので、全探索で解けない。<br /><br />問題の条件より、ある２つを選んだときその差が指定値より大きければ終了になる。<br /><br />そのため全ての２つの組み合わせの中から、その差が指定値より大きくなるもの全てについて最小値を求めて更新していけばよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class ProblemsToSolve {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minNumber(vector&lt;int&gt; p, int variety) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=p.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=n;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,i+1,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(abs(p[j]-p[i])&gt;=variety)ret=min(ret,(i+3)/2+(j-i+1)/2);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
