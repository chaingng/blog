+++
title = "SRM 437 DIV1 Easy - TheSwap"
date = 2015-05-09T17:14:00Z
updated = 2015-05-09T17:14:28Z
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=10369&amp;rd=13699" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=10369&amp;rd=13699</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />全探索可能な問題。<br />setとvectorを利用して、各繰り返し回数で生成される数を更新していく。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class TheSwap {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: int findMax(int n, int k) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>set&lt;int&gt; cur,next;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>cur.insert(n);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,k){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>for(set&lt;int&gt;::iterator it=cur.begin();it!=cur.end();it++){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>int x=*it;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>vector&lt;int&gt; vx;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>while(x&gt;0){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>vx.push_back(x%10);<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>x/=10;<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">    </span>FORE(a,0,vx.size())FORE(b,a+1,vx.size()){<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>if(!(b==vx.size()-1 &amp;&amp; vx[a]==0)){<br /><span class="Apple-tab-span" style="white-space: pre;">      </span>swap(vx[a],vx[b]);<br /><span class="Apple-tab-span" style="white-space: pre;">      </span>int tmp=0;<br /><span class="Apple-tab-span" style="white-space: pre;">      </span>for(int c=vx.size()-1;c&gt;=0;c--)tmp=tmp*10+vx[c];<br /><span class="Apple-tab-span" style="white-space: pre;">      </span>next.insert(tmp);<br /><span class="Apple-tab-span" style="white-space: pre;">      </span>swap(vx[a],vx[b]);<br /><span class="Apple-tab-span" style="white-space: pre;">     </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cur=next;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>next.clear();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int ret=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>if(cur.empty())return -1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>for(set&lt;int&gt;::iterator it=cur.begin();it!=cur.end();it++){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret=max(ret,*it);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>