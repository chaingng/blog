+++
title = "SRM 538 DIV1 Easy - EvenRoute"
date = 2015-05-17T13:38:00Z
updated = 2015-05-17T13:38:33Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11808&amp;rd=14729" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11808&amp;rd=14729</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />（ｘ，ｙ）の合計が奇数の座標と偶数の座標が存在すれば、どちらにもできるので<br />答えは必ずYESになる。<br />そうでない場合はそれぞれ奇数のみ、偶数のみのルートとなる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class EvenRoute {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string isItPossible(vector&lt;int&gt; x, vector&lt;int&gt; y, int wantedParity) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=x.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int odd=0,even=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((x[i]+y[i])%2==0)even++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>else odd++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(even &amp;&amp; odd)return "CAN";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(even&gt;0 &amp;&amp; wantedParity==0)return "CAN";<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(odd&gt;0 &amp;&amp; wantedParity==1)return "CAN";<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return "CANNOT";<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
