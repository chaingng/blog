+++
title = "SRM 380 DIV1 Easy - LameKnight ○"
date = 2015-08-04T06:31:00Z
updated = 2015-08-04T06:31:31Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8183&amp;rd=10802" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8183&amp;rd=10802</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />条件より、すべての４方向にいける場合とそれ以外を場合分けする。<br />次に高さの値によって場合分けできることがわかる。<br />高さが３以上ある場合は上に２、右に１行き、次に下に２、右に１行くのが<br />最適になる。<br />高さ２のときは上に１、右に２，下に１，右に２しかいけなく、<br />高さ１のときは動くことができない。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LameKnight {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int maxCells(int height, int width) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(height&gt;=3 &amp;&amp; width&gt;=7)return width-2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(height&gt;=3)return min(4,width);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(height==2)return min(4,(width+1)/2);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return 1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
