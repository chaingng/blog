+++
title = "SRM 153 DIV1 Easy - Inventory (復習×○)"
date = 2014-02-10T22:57:00Z
updated = 2015-03-26T19:42:11Z
tags = ["実装"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=1772&amp;rd=4570" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=1772&amp;rd=4570</a><br /><br />ある製品について、何日間で何個売れるかがわかっている。<br />複数の製品について上記の情報が与えられたとき、<br />１カ月あたり、つまり３０日あたり平均何個の製品が売れるかを求めたい。<br /><br />ただし、情報が０日間であったときはその製品はないものとみなす。<br />また、割りきれない場合は誤差1e-9を引いたのちに繰り上げる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />実装自体はシンプル。<br />以下の例外条件をきちんと書けるかがポイント。<br /><br />・情報が０日間はカウントしない。（売れる数が０個のときはカウント）<br />・誤差の計算（問題文のとおり、1e-9を引く）<br />・最後に割り算が来るので、０のときの例外条件を記載<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class Inventory {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int monthlyOrder(vector&lt;int&gt; sales, vector&lt;int&gt; daysAvailable) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double cnt=0.0,ret=0.0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,sales.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(daysAvailable[i]==0)continue;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=sales[i]*30.0/daysAvailable[i];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cnt++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return cnt==0 ? 0 :(int)(ceil(ret/cnt-1e-9));<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
