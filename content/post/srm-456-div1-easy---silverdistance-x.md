+++
title = "SRM 456 DIV1 Easy - SilverDistance x"
date = 2015-05-03T22:39:00Z
updated = 2015-07-28T04:54:48Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10699&amp;rd=13909" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10699&amp;rd=13909</a><br /><br />銀の動きをする駒がある。<br /><br />２次元のセル上でスタート位置とゴール位置が与えられた時、<br />ゴールにたどりつくまでの最小のターン数を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />☓の形で４つのエリアに分け、場合分けして求める方法があるが<br />複雑になってしまうためシステムで落ちやすくなる。<br /><br />今回、セルをチェスのように白と黒で分けた時、<br />同じエリアであればｘとｙの位置の差の最大の方が答えになる。<br />エリアが異なる場合は、一つ上に移動することで同じエリアに移動することができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class SilverDistance {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int minSteps(int sx, int sy, int gx, int gy) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if((abs(gx-sx)-abs(gy-sy))%2)ret++,sy++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>ret+=max(abs(gx-sx),abs(gy-sy));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
