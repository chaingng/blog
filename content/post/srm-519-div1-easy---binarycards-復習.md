+++
title = "SRM 519 DIV1 Easy - BinaryCards (復習××)"
date = 2013-10-13T10:17:00Z
updated = 2015-03-26T20:32:22Z
tags = ["ビット"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11552&amp;rd=14544" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11552&amp;rd=14544</a><br /><br />正の整数ＡとＢが与えられる。<br />ＡからＢを得るには、２進数で表わされたＡから各ビットを返していく。<br /><div>この操作を行ったとき、途中で現れる最大の数を求める。</div><div><br /></div><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />Ａ，Ｂは最大１０＾１８のため単純なシミュレーションでは解くことができない。<br />そのため、計算量を削減する法則がないか考える。<br /><br />２進数にしてみて、最初と最後の状態までのプロセスの変化が答えに関連しないか考えてみる。<br />いくつか例を出してみると、<br />一度も触ったことがないビットは固定しなければいけないが<br />「ＡからＢを得るときに１度でもひっくり返したビット以降はすべて１」にできることがわかる。<br /><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class BinaryCards {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: long long largestNumber(long long A, long long B) {<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(long long i=63;i&gt;=0;i--){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>long long x=1LL&lt;&lt;i;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((A&amp;x)!=(B&amp;x))return A | ( (1LL&lt;&lt;(i+1))-1);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return A;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
