+++
title = "SRM 489 DIV1 Easy - BallsConverter (復習○)"
date = 2014-02-02T20:45:00Z
updated = 2015-03-26T19:30:55Z
tags = ["状態遷移"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11211&amp;rd=14242" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11211&amp;rd=14242</a><br /><br />２つのボールを捨てて、新しくボールを作るマシーンがある。２つのボールのタイプがi、jとすると、<br />新しく作られるボールはパターンc[i][j]もしくはc[j][i]となる。<br /><br />このとき、最初に入っているボールがわかっているときに結果が変わらないパターンであればＧｏｏｄ、そうでなければＢａｄを返す。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題文を理解するのが難しかった。<br />要は、任意の３つのボールに対して結合法則が成り立つかどうかを全てのタイプに対して調べればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class BallsConverter {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>int f(char ch){<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if('A'&lt;=ch&amp;&amp;ch&lt;='Z')return ch-'A';<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>else return ch-'a'+26;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>string theGood(vector&lt;string&gt; c) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=c.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)FORE(j,0,n)FORE(k,0,n)if(c[f(c[i][j])][k]!=c[i][f(c[j][k])])return "Bad";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "Good";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
