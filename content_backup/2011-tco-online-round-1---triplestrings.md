+++
title = "2011 TCO Online Round 1 - TripleStrings"
date = 2014-11-10T19:29:00Z
updated = 2015-04-03T11:30:37Z
tags = ["文字列"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11374&amp;rd=14560" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11374&amp;rd=14560</a><br /><br />・○とXからなる配列initがあらかじめ与えられる。<br />・この配列を操作して、最終的にはgoalで示される配列にしたい。<br />・可能な操作としては、最初に空の配列B,Cがあり、initをAとする。<br />・１操作で、Aの最初の１文字をBもしくはCの最後につけることが可能。<br />・もしくは１操作で、BもしくはCの最初１文字をAの最後につけることが可能。<br />・このとき、必要な最小の操作回数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・まず、initの配列の一部を残した方法がありそう。<br />・この方法は残りの配列のうち○をすべてBに、×をすべてCに入れることで<br />　残りの配列＊２が答えになる。<br />・他の方法としては、AをBにして・・・等いろいろ考えて行き詰ってしまった。<br /><br />→他の人のコードをみる。<br /><br />・他の方法は最初に考えた方法に含まれる、つまり最悪ケースで文字列長×２回となる。<br /><br />・反省：問題文の読み方と紙に書いたトレースが悪かった。もっと整理が必要。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class TripleStrings {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int getMinimumOperations(string init, string goal) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=1e+9;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=init.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,n+1)if(init.substr(n-i,i)==goal.substr(0,i))ret=min(ret,(n-i)*2);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret==1e+9 ? n*2 : ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
