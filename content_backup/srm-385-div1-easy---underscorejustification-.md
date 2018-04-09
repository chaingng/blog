+++
title = "SRM 385 DIV1 Easy - UnderscoreJustification ○"
date = 2015-07-27T20:18:00Z
updated = 2015-07-27T20:18:21Z
blogimport = true
draft = true
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 <br /></h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=8482&amp;rd=10810" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=8482&amp;rd=10810</a><br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />各スペースに挿入するアンダースコアの数の差は最大１なので、<br />スペースの数と挿入できるアンダースコアの数がわかれば<br />答えは一意に定まる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class UnderscoreJustification {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public:<br /><br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>string justifyLine(vector&lt;string&gt; words, int width) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int n=words.size();<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int len=0;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,0,n)len+=words[i].size();<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int s=width-len;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int num2=s%(n-1);<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int num1=(n-1)-num2;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>s/=(n-1);<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string ret=words[0];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>FORE(i,1,n){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>if((num1&gt;0 &amp;&amp; num2==0) || (words[i][0]&lt;='Z' &amp;&amp; num1&gt;0)){<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>FORE(j,0,s)ret+='_';<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>num1--;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}else{<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>FORE(j,0,s+1)ret+='_';<br /><span class="Apple-tab-span" style="white-space: pre;">    </span>num2--;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=words[i];<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>