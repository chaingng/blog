+++
title = "SRM 188 DIV1 Easy - Percents (復習×)"
date = 2014-02-09T17:25:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=2386&amp;rd=4760" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=2386&amp;rd=4760</a><br /><br />あるアンケートに対して、yesと答えた人の割合が％で与えられる。<br />このとき、その割合になるときに必要なアンケート人数の母数を求める。<br />ただし、小数点３位以下は四捨五入される。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />最初に文字列からｐを取りだすのにそのままの小数点を取りだすと、整数にしようと掛け算をした時に誤差が出てしまうので、文字から直接取りだした。<br /><br />母数を１～１００００まで順に操作し、<br />そのときのyesと答えた人の割合は切り捨てとなる場合と切り上げになる場合の<br />両方を検査する。<br /><br />ｎで割ったときの判定については、ｎの半分を足すことで四捨五入の値を求めることができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class Percents {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minSamples(string percent) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int p=(percent[0]-'0')*1000+(percent[1]-'0')*100+(percent[3]-'0')*10+(percent[4]-'0');<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(n,1,10000){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int cost=n*p/10000;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((cost*10000+n/2)/n==p)return n;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(((cost+1)*10000+n/2)/n==p)return n;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return 10000;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
