+++
title = "SRM 587 DIV1 Easy - JumpFurther ○"
date = 2015-05-31T13:36:00Z
updated = 2015-08-06T09:55:56Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=12300&amp;rd=15699" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=12300&amp;rd=15699</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />最初はすべてのターンでジャンプし、そのときbadStepに当たらなければ<br />それが最大の答えとなる。<br />badStepにあたった時、最初の１ステップだけ待てばbadStepに当たらなくなるので<br />それが答えになる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class JumpFurther {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int furthest(int N, int badStep) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int valid=1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int cur=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=1;i&lt;=N;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cur+=i;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(cur==badStep)valid=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(valid)return cur;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>cur=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=2;i&lt;=N;i++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cur+=i;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return cur;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>