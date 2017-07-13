+++
title = "SRM 662 DIV1 Easy - FoxesOfTheRoundTable △"
date = 2015-07-12T15:18:00Z
updated = 2015-08-05T09:40:00Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=13858&amp;rd=16511" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=13858&amp;rd=16511</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />Dが1000までなので、Dを固定することで解けそう。<br />ただ、Dをできるだけ小さくするということは、並べ方は以下の通り<br />一意に定まる。<br /><br />要はh[i]の小さい順に0,1,2,3,4...とすると、単に0から左右に順に並べていけば良い。<br />3 1 0 2 4...となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class FoxesOfTheRoundTable {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: vector&lt;int&gt; minimalDifference(vector&lt;int&gt; h) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=h.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;pair&lt;int,int&gt; &gt; p;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)p.push_back(make_pair(h[i],i));<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>sort(all(p));<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; ans;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int end = n%2 ? n-2 : n-1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=end;i&gt;0;i-=2)ans.push_back(p[i].second);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;n;i+=2)ans.push_back(p[i].second);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ans;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>