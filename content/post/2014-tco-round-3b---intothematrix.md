+++
title = "2014 TCO Round 3B - IntoTheMatrix"
date = 2014-09-20T08:49:00Z
updated = 2015-03-26T20:32:53Z
tags = ["ビット"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13066&amp;rd=16058" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13066&amp;rd=16058</a><br /><br />N種類のピルがあり、どれがマジックピルかを判別したい。<br />判別するのに友人に協力してもらうことができ、マジックピルを飲んだ友人は消えてしまう。<br />協力してもらうターン数turnsが与えられた時、最低限必要な友人の数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />・問題文から、ターンと友人の数により判別できるピルの数を列挙してみる<br />・問題文の誘導からか、なんとなくはまってしまう。<br /><br />・他の人のコードを読む<br /><br />・要は、人数とターンにより表わされる状態数が判別できるピルの数<br />・例えば１ターンでA,Bがいるときは、{ABが残る}、{Aだけ残る}、{Bだけ残る}、{両方消える}の４通り<br />・友人の数を固定すると、１人のとき1ターンで２通り、２ターンで３通り・・・Tターンで（T+1）通り<br /><br />・よって、友人の数を０から増やしていき、（T+1)＾友人の数がN以上となるところが答え<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">using namespace std;<br /><br />#define all(c) (c).begin(),(c).end()<br />#define FORE(i,d,e) for(int i=d;i&lt;e;i++)<br />#define FOR(i,s,e) for (int i = int(s); i != int(e); i++)<br />#define FORIT(i,c) for (typeof((c).begin()) i = (c).begin(); i != (c).end(); i++)<br />#define ISEQ(c) (c).begin(), (c).end()<br /><br />class IntoTheMatrix {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int takePills(int turns, int N) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int F=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long x=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(x&lt;(long long)N){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>x*=(turns+1);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>F++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return F;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
