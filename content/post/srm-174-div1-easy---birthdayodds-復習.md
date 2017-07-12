+++
title = "SRM 174 DIV1 Easy - BirthdayOdds (復習×○)"
date = 2014-02-11T00:24:00Z
updated = 2015-04-03T11:06:47Z
tags = ["確率"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=1848&amp;rd=4675" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=1848&amp;rd=4675</a><br /><br />何人かのグループを考えた時、ある割合で同じ誕生日の人が存在する。<br /><br />同じ誕生日の人がいる確率が与えられ、また誕生日となりうる日数が与えられた時、<br />何人の人がいれば与えられた確率以上で同じ誕生日の人が存在するかを求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />日数をＤとすると、Ｄ／Ｄ＊（Ｄ－１）／Ｄ・・・と計算していき<br />この値が１００－与えられた確率以下になるときの人数を答えればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class BirthdayOdds {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minPeople(int minOdds, int daysInYear) {<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double p=1.0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,daysInYear){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>p*=(double)(daysInYear-i)/daysInYear;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(p*100&lt;=100-minOdds)return i+1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return daysInYear+1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
