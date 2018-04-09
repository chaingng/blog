+++
title = "SRM 513 DIV1 Easy - YetAnotherIncredibleMachine"
date = 2015-05-10T12:55:00Z
updated = 2015-05-10T12:55:06Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11502&amp;rd=14538" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11502&amp;rd=14538</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />各プラットフォームについて有効な場所の総数を、それぞれかけていけばよい。<br />あるプラットフォームについて有効な場所かどうかの判定は、<br />一番左側の点と右側の点の間にボールがなければよい。<br />この判定には二分探索を使うことができる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class YetAnotherIncredibleMachine {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int countWays(vector&lt;int&gt; platformMount, vector&lt;int&gt; platformLength, vector&lt;int&gt; balls) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=platformMount.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int MOD=1000000009;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int m=balls.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(balls));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int cur=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(int l=platformMount[i]-platformLength[i];l&lt;=platformMount[i];l++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int r=l+platformLength[i];<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int s=lower_bound(balls.begin(),balls.end(),l)-balls.begin();<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if( !(0&lt;=s &amp;&amp; s&lt;m) || balls[s]&gt;r )cur++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret=(1LL*ret*cur)%MOD;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>