+++
title = "SRM 585 DIV1 Easy - TrafficCongestion (復習×○)"
date = 2013-08-18T16:44:00Z
updated = 2015-03-26T19:54:39Z
tags = ["DP"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11361&amp;rd=15697" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11361&amp;rd=15697</a><br /><br />２分木の高さが与えられる。<br />車は一筆書きでそのセルを移動することができる。<br />ただし、一度車が通った道は行くことができない。<br /><br />このとき、すべてのセルを移動するのに必要な車の台数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />いくつか例を並べてみると、前の高さで必要な車の数＋２つ前で必要な車の数×２が答えになるという法則が出てくる。<br />あとはこれをｄｐで実装すればよい。<br /><br /><br />Challenge<br />高さが０のときはセルが1個存在するので答えは１になる。<br />値が０、１のときにコードがそのままでよいのか、例外条件を書かなければいけないのかを確かめる。<br />特にこの問題の場合は2つ前の配列を調べることからスタートは２からになるので<br />特に注意する。<br /><br />dpの配列の宣言がなぜかうまく通らなかったのですが、vectorで宣言するとうまくいきました。１０＾６を超えるなど大きい場合のときはvectorを用いるのがよさそうです。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TrafficCongestion {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int theMinCars(int treeHeight) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;long long&gt; dp(treeHeight+1,0);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long MOD=1000000007;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>dp[0]=1,dp[1]=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,2,treeHeight+1)dp[i]=(dp[i-1]+2*dp[i-2])%MOD;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return (int)dp[treeHeight];<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
