+++
title = "SRM 592 DIV1 Easy - LittleElephantAndBalls"
date = 2015-05-31T13:49:00Z
updated = 2015-05-31T13:49:11Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12758&amp;rd=15704" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12758&amp;rd=15704</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />問題文を、最終的にボールを置いた位置の状態にすると勘違いしてしまった。<br />ボールが左から順に与えられて、それを任意の位置に配置する、という<br />問題になる。<br /><br />RGBそれぞれについて最初に出た時は左側に、次に出た時は右側においていけば<br />各色についてスコアは最初に出現した時は１、それ以降は２となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LittleElephantAndBalls {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int getNumber(string S) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int r=0,g=0,b=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,S.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=min(r,2)+min(g,2)+min(b,2);<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(S[i]=='R')r++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else if(S[i]=='G')g++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else b++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
