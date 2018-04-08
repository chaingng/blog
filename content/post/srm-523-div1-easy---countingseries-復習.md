+++
title = "SRM 523 DIV1 Easy - CountingSeries (復習××)"
date = 2013-10-13T07:55:00Z
updated = 2015-03-26T20:31:12Z
tags = ["数学"]
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10957&amp;rd=14548" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10957&amp;rd=14548</a><br /><br />１からupperBoundまでの数が与えられる。<br />また、a,b,c,dの正の整数が与えられる。<br />このとき、a+b*x または c*d^y（x,yは任意の整数）を満たす数がいくつあるか求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />「a+b*x」、「c*d^y」は重複する場合があるので、<br />重複した場合は１度しか計算しない処理が必要。<br /><br />「a+b*x」では、各整数は10^12のため全探索では不可。<br />upperBoundがa以上であれば、 (upperBound-a)/b +1が満たす全ての数になる。<br /><br />「c*d^y」は全探索が可能。<br />各数に対して「a+b*x」でも表わせないか判定し重複を調べる。<br />（同じようにa以上かどうかを調べる）<br />ただしd=1のときは無限ループになるのでbreak処理が必要。<br /><br />Challengeポイント<br />階乗が出てくる場合は1の階乗のbreak処理が入っているか？<br />数の判定の際は正負の判定が入っているか？<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;"><br />class CountingSeries {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long countThem(long long a, long long b, long long c, long long d, long long upperBound) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>long long ans=upperBound&gt;=a ? (upperBound-a)/b+1 :0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(long long x=c;x&lt;=upperBound;x*=d){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((x-a)&lt;0||(x-a)%b!=0)ans++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(d&lt;=1)break;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
