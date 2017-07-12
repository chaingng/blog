+++
title = "SRM 445 DIV1 Easy - TheNewHouseDivOne"
date = 2015-05-09T16:58:00Z
updated = 2015-05-09T16:58:07Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10512&amp;rd=13899" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10512&amp;rd=13899</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />元となる点はすべて座標上の点なので、<br />すべての実数上の点を調べなくても、0.5単位ですべての位置を調べればよい。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TheNewHouseDivOne {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: double distance(vector&lt;int&gt; x, vector&lt;int&gt; y, int k) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>double ret=1e+9;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=x.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(double xx=-100;xx&lt;=100;xx+=0.5)for(double yy=-100;yy&lt;=100;yy+=0.5){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vector&lt;double&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,0,n)vx.push_back(abs(xx-x[i])+abs(yy-y[i]));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>sort(all(vx));<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret=min(ret,vx[k-1]);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
