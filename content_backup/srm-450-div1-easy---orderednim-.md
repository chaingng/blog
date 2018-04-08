+++
title = "SRM 450 DIV1 Easy - OrderedNim ○"
date = 2015-05-04T22:06:00Z
updated = 2015-07-28T04:51:13Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10190&amp;rd=13904" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10190&amp;rd=13904</a><br /><br />Nimを少し変化させたゲームがあり、<br />ある山についてそれよりも左の山が存在する時は選ぶことができない。<br /><br />山が与えられたとき、２人のうちどちらが勝つか求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />左側からしか山を選ぶことができないので、<br />その中で法則がないか考察する。<br /><br />まず、すべて１のときは選び方が一様なので<br />配列数が偶数のときはBob,そうでないときはAliceが勝つ。<br /><br />次に、すべて１でないときは最初に２以上の山が当たられた方が<br />その後の順番をコントロールできるので、その選択権を持った方が勝ちとなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class OrderedNim {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string winner(vector&lt;int&gt; layout) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=layout.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)if(layout[i]!=1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>return i%2 ? "Bob" : "Alice";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return n%2 ? "Alice" : "Bob";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
