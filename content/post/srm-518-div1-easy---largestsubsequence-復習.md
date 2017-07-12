+++
title = "SRM 518 DIV1 Easy - LargestSubsequence （復習○）"
date = 2013-10-13T10:23:00Z
updated = 2015-03-26T19:36:06Z
tags = ["文字列"]
blogimport = true 
[author]
	name = "chngng"
	uri = "https://www.blogger.com/profile/14196381724208675248"
+++

<div dir="ltr" style="text-align: left;" trbidi="on"><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">問題 </h3><br /><a href="http://community.topcoder.com/stat?c=problem_statement&amp;pm=11471&amp;rd=14543" target="_blank">http://community.topcoder.com/stat?c=problem_statement&amp;pm=11471&amp;rd=14543</a><br /><br />ある文字列が与えられる。<br />その文字からいくつかの文字を削除したものがそのサブ文字列と定義される。<br />このとき、辞書順で最も降順となるサブ文字列を求める。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">解き方 </h3><br />現在の文字列で最も降順のアルファベットがサブ文字列の左側にくる。<br />次に、選ばれたアルファベット以降の位置から上記の文字を探す。<br />この操作を繰り返すことで答えが求められる。<br /><br /><h3 style="border-bottom: 2px solid slateblue; border-left: 8px solid navy; color: black; padding: 0px 0px 1px 5px;">コード </h3><br /><div style="background-color: #e3f2fb; border: 1px dotted #CCCCCC; padding: 5px;">class LargestSubsequence {<br /><br /><span class="Apple-tab-span" style="white-space: pre;"> </span>public: string getLargest(string s) {<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>string ret;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>int cur=0;<br /><br /><span class="Apple-tab-span" style="white-space: pre;">  </span>while(cur!=s.size()+1){<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>int tmp=cur;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>FORE(i,cur+1,s.size())if(s[i]&gt;s[tmp])tmp=i;<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>ret+=s[tmp];<br /><span class="Apple-tab-span" style="white-space: pre;">   </span>cur=tmp+1;<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>}<br /><span class="Apple-tab-span" style="white-space: pre;">  </span>return ret;<br /><span class="Apple-tab-span" style="white-space: pre;"> </span>}<br /><br />};</div></div>
