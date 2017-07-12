+++
title = "SRM 668 DIV1 Easy - PaintTheRoom ○"
date = 2016-01-06T20:47:00Z
updated = 2016-01-06T20:47:23Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="https://community.topcoder.com/stat?c=problem_statement&amp;pm=13846&amp;rd=16548" target="_blank">https://community.topcoder.com/stat?c=problem_statement&amp;pm=13846&amp;rd=16548</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />K=1の場合はどのようなR,Cでも達成できる。<br />その他の場合は、全ての道を通って元のセルに戻ってこれればOKとなる。<br />Rが偶数の場合もしくはCが偶数のときは元のセルに戻ってこれるが、<br />双方とも奇数のときは戻ってこれない。<br /><br />よって、RかつCがどちらも奇数かつKが２以上の時のみCannot Paintとなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class PaintTheRoom {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string canPaintEvenly(int R, int C, int K) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(R%2 &amp;&amp; C%2 &amp;&amp; K&gt;1)return "Cannot paint";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "Paint";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};<br /><div><br /></div></div></div>
