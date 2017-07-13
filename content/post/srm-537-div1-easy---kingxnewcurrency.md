+++
title = "SRM 537 DIV1 Easy - KingXNewCurrency"
date = 2015-05-17T13:35:00Z
updated = 2015-05-17T13:35:16Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11817&amp;rd=14730" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11817&amp;rd=14730</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />A，B自身をXとYで表せられるような整数を求めれば良い。<br />どちらもXで割り切れるならばYが不要になるので−１となる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class KingXNewCurrency {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int howMany(int A, int B, int X) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(A%X==0 &amp;&amp; B%X==0)return -1;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>set&lt;int&gt; s1,s2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;A;i+=X)for(int j=1;j&lt;=A-i;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((A-i)%j==0)s1.insert(j);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=0;i&lt;B;i+=X)for(int j=1;j&lt;=B-i;j++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((B-i)%j==0)s2.insert(j);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(A%X==0)return s2.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(B%X==0)return s1.size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(set&lt;int&gt;::iterator it=s1.begin();it!=s1.end();it++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(s2.find(*it)!=s2.end())ret++;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};<span id="goog_1499391229"></span><span id="goog_1499391230"></span><a href="https://www.blogger.com/"></a></div></div>