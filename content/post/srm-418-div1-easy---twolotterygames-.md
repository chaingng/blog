+++
title = "SRM 418 DIV1 Easy - TwoLotteryGames ○"
date = 2015-05-05T18:02:00Z
updated = 2015-08-09T20:49:10Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10071&amp;rd=13509" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10071&amp;rd=13509</a><br /><br />ｎ個のくじからm個選ぶ。<br />相手も同様にm個選ぶ。<br />選んだくじのうち、相手がえらんだくじとk個一致していれば勝ちとなる。<br /><br />このとき、勝ちとなる確率を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />ｎが８と小さいので、全探索すればよいだけ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TwoLotteryGames {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double getHigherChanceGame(int n, int m, int k) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ret=0.0,sum=0.0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=1;i&lt;1&lt;&lt;n;i++)if(__builtin_popcount(i)==m){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int j=1;j&lt;1&lt;&lt;n;j++)if(__builtin_popcount(j)==m){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>sum++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(__builtin_popcount(i&amp;j)&gt;=k)ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret/sum;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
