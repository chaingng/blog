+++
title = "SRM 373 DIV1 Easy - StringFragmentation ○"
date = 2015-08-09T20:42:00Z
updated = 2015-08-09T20:42:02Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8087&amp;rd=10791" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8087&amp;rd=10791</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />全探索可能なので解くだけ。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class StringFragmentation {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int largestFontSize(string text, int width, int height) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>vector&lt;int&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>stringstream out(text);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(string str;out&gt;&gt;str;){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>vx.push_back(str.size());<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=vx.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(int i=5000;i&gt;=8;i--){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int at=0,lines=0;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>while(at&lt;n){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int cur=0;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>if(vx[at]*(i+2)&lt;=width){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>cur+=vx[at]*(i+2);<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}else break;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">    </span>while(at+1&lt;n &amp;&amp; cur+(vx[at+1]+1)*(i+2)&lt;=width){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>cur+=(vx[at+1]+1)*(i+2);<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>at++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>lines++;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>at++;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if(at&gt;=n &amp;&amp; lines*2*i&lt;=height)return i;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return -1;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br />}</div></div>