+++
title = "2014 TCO Round 1B Easy - SpamChecker (○)"
date = 2014-10-28T20:52:00Z
updated = 2015-03-26T19:11:25Z
tags = ["状態遷移"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13119&amp;rd=15950" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13119&amp;rd=15950</a><br /><br />・与えられたe-mailがスパムかどうかチェックしたい。<br />・e-mailの各行のうち、スパムな文字列でないときは○、スパムなときは×であるという<br />　情報が与えられる。<br />・○が現れたら○のときのスコアを足し、×のときは×のときのスコアを引く。<br />・最初のスコアは０であり１行目から順にスコアを計算していき、１度でもスコアが<br />　マイナスになったらそのe-mailはスパムとなる。<br />・このとき、与えられたe-mailがスパムであるかどうかを求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />単純に実装するだけ。<br />スコアを順に計算して毎回マイナスかどうかを判定すればよい。<br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class SpamChecker {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string spamCheck(string judgeLog, int good, int bad) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=judgeLog.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int score=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(judgeLog[i]=='o')score+=good;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else score-=bad;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(score&lt;0)return "SPAM";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "NOT SPAM";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
